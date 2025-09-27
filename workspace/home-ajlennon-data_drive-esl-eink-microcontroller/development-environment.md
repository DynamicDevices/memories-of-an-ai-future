# Development Environment & Infrastructure

> **Workspace**: `/home/ajlennon/data_drive/esl/eink-microcontroller`  
> **Remote Target**: ajlennon@62.3.79.162:23 with target on /dev/ttyUSB0

## CI/CD Pipeline

**Current Status**: Production-ready GitHub Actions pipeline
- **Docker Image**: `zephyrprojectrtos/zephyr-build:latest` with SDK 0.17.4 verification
- **Self-hosted Runner**: [self-hosted, Linux, X64] with 2GB ccache
- **Build Variants**: Debug + Production (with MCUboot signing)
- **Artifacts**: Versioned binaries with git commit hashes

## Build Variants

**Debug Build**:
- Size: ~111KB (87% of 124KB partition)
- Features: Full debugging, shell interface, comprehensive logging
- Partition: 124KB app + 4KB config (no MCUboot)
- Command: `./app/build.sh debug`

**Production Build**:
- Size: ~42KB (47% of 92KB partition, can grow to 91KB)
- Features: MCUboot enabled, size optimized, signed firmware
- Partition: 32KB bootloader + 92KB app + 4KB config
- Command: `./app/build.sh production`

## Testing Infrastructure

**Hardware Validation**: `target_scripts/test_target_board.py`
- Comprehensive hardware validation (GPIO, I2C, UART, power rails)
- NFC controller (NTA5332) and battery monitor (LTC2959) testing
- Power management verification (PMIC, WiFi, display control)
- Communication signal testing (BT_WAKE, WL_WAKE)

**Firmware Updates**: `target_scripts/firmware_update.py`
- Optimized update process (~108s total time)
- Process cleanup and timing optimizations
- Remote operation via SSH tunnel
- Automatic version verification

**Troubleshooting Tools**:
- `cleanup_mcumgr.py` - Fix stuck upload processes
- `check_board_status.py` - Connectivity diagnostics

## Key Commands

```bash
# Power control
power pmic on/off      # Main PMIC (PTE17)
power wifi on/off      # WiFi module (PTE19+PTE18)  
power disp on/off      # Display (PTE16)

# Communication
comm bt_wake on/off    # Bluetooth wake (PTC1)
comm wl_wake on/off    # Wireless wake (PTC3)

# Battery monitoring (LTC2959)
ltc2959 enable         # Enable ADC (smart sleep mode)
ltc2959 counting enable # Enable coulomb counting
ltc2959 read           # Read all measurements

# NFC (NTA5332)
nta5332 status         # NFC status and configuration
nta5332 uid            # Read unique identifier
```

## Directory Structure

```
/home/ajlennon/data_drive/esl/eink-microcontroller/
├── app/                    # Main Zephyr application
│   ├── boards/            # Custom MCXC143VFM board definitions
│   ├── src/               # Application source code
│   └── build.sh           # Build script (debug/production)
├── bootloader/            # MCUboot bootloader
├── keys/                  # Signing keys (CRITICAL: single key only)
├── scripts/               # Build and utility scripts
├── target_scripts/        # Remote testing and update tools
└── reports/               # Test reports and logs
```

## Remote Development Setup

- **SSH Access**: ajlennon@62.3.79.162:23
- **Target Device**: /dev/ttyUSB0 (UART2 PTD4/PTD5 @ 115200)
- **MCUboot Programming**: mcumgr over serial
- **Development Flow**: Local build → Remote test → Remote update → Verify
