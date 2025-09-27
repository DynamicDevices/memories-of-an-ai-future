# MCXC143VFM E-Ink Power Controller Project

> **Workspace Path**: `/home/ajlennon/data_drive/esl/eink-microcontroller`  
> **Project Type**: Embedded Systems, Zephyr RTOS, MCUboot Bootloader  
> **Hardware**: MCXC143VFM ARM Cortex-M0+ Microcontroller

## Project Overview

ARM Cortex-M0+ power management controller for E-Ink displays with battery monitoring and NFC integration. Complete Zephyr RTOS application with MCUboot bootloader and production-ready CI/CD pipeline.

## Hardware Specifications

**Memory 9321044 & 9160859 - MCXC143VFM Hardware**
- **MCU**: MCXC143VFM, 33-pin QFN (32 I/O + 1 GND pad)
- **Memory**: 128KB Flash (NOT 256KB), 32KB RAM at 0x20000000
- **UART**: PTD4/PTD5 @ 115200 baud (host communication)
- **I2C0**: PTB0/PTB1 (LTC2959 coulomb counter @ 0x63)
- **I2C1**: PTE0/PTE1 (NTA5332 NFC controller @ 0x54)
- **Key Pins**: PMIC_EN=PTE17, DISP_EN=PTE16, CC_GPIO=PTC4
- **Power Rails**: WiFi (PTE19+PTE18), BT_WAKE (PTC1), WL_WAKE (PTC3)

## Flash Layout Design

**Memory 9326413 - Optimized Flash Layouts**
- **Production Build**: 32KB bootloader + 92KB app + 4KB config
- **Debug Build**: 124KB app + 4KB config  
- **Current Usage**: Production 42KB app (can grow to 91KB = 2.2x), Debug 111KB app
- **Config Partition**: Always at end (0x1F000-0x1FFFF) for protection

## Security & MCUboot

**Memory 9331008 & 9330272 - MCUboot Configuration**
- **Signing Key**: Single key at `keys/root-ec-p256.pem` (CRITICAL: only one copy)
- **UART Programming**: mcumgr over UART2 (PTD4/PTD5), 2-second boot delay
- **Field Updates**: Complete workflow via `target_scripts/firmware_update.py` (~108s)
- **Bootloader**: Uses same UART2 config as application for consistency

## Development Workflow

**Memory 9369547 & 9369551 - Development Process**
1. Test: `target_scripts/test_target_board.py` (comprehensive hardware validation)
2. Build: Clean production firmware with commit hash
3. Update: `target_scripts/firmware_update.py` with optimizations
4. Verify: Version matches commit hash exactly

**Key Optimizations**:
- Copy firmware before reset (not after) - avoids bootloader timeout
- Cleanup stuck mcumgr processes at multiple stages
- Timing: 1.5s reset wait, 1s bootloader init, 2s verification
- Remote development via SSH to ajlennon@62.3.79.162:23

## System Requirements

**Memory 9291663 - Shell Interface**
- Shell interface is CRITICAL - never disable CONFIG_SHELL
- Provides essential power management, GPIO control, NFC/battery diagnostics
- Keep enabled even in production builds for field debugging

## NFC Integration

**Memory 9371369 - NTA5332 System Reset**
- System reset: Write 0xE7 to RESET_GEN_REG at block address 0x10AA
- Use nta5332_write_config_block() function (not simple register write)
- Initialization sequence: 1) Set CONFIG_1 SRAM_ENABLE, 2) Reset, 3) Verify SRAM ready
- Works as software alternative to physical power cycle

## Build System

**Memory 9331285 - Dynamic Configuration**
- Build scripts dynamically parse flash partition sizes from device tree
- No hardcoded values - automatic adaptation to partition changes
- Parser handles various DT formats with fallback to defaults
- Better error messages showing actual vs available space
