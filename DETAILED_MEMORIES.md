# AI Memories - Complete Technical Knowledge Base

> **Repository**: `git@github.com:DynamicDevices/memories-of-an-ai-future.git`  
> **Last Updated**: 2025-09-27  
> **Project**: MCXC143VFM E-Ink Power Controller  
> **AI**: Claude Sonnet 4 (Cursor)

## Memory Index

| ID | Category | Title | Criticality |
|----|----------|-------|-------------|
| 9382134 | Engineering | Critical Engineering Principle | Critical |
| 9382423 | CI/CD | Cache Strategy Best Practice | High |
| 9382671 | CI/CD | Docker Image Optimization | High |
| 9321044 | Hardware | MCXC143VFM Specifications | High |
| 9326413 | Memory | Optimized Flash Layouts | High |
| 9331008 | Security | Single Signing Key Requirement | Critical |
| 9330272 | Bootloader | MCUboot UART Programming | High |
| 9369547 | Workflow | Complete Development Process | High |
| 9369551 | Tools | Firmware Update Optimizations | High |
| 9359663 | Quality | Code Organization Standards | Medium |
| 9343623 | RTOS | Zephyr Best Practices | High |
| 9341442 | Standards | Relative Path Requirements | Medium |
| 9291663 | System | Shell Interface Requirement | High |
| 9371369 | Hardware | NTA5332 System Reset | High |
| 9160859 | Hardware | Hardware Verification | High |

## Detailed Memory Records

### 🔧 Engineering Discipline

**Memory 9382134 - Critical Engineering Principle**
> Never assume code changes work until explicitly validated. Always wait for concrete evidence (builds, tests, verified functionality) before declaring "fixed". Making assumptions without validation leads to false confidence in broken systems.

### 🏗️ CI/CD & Build Systems

**Memory 9382423 - CI/CD Cache Strategy**
> Use `actions/cache@v4` for most needs (auto-restore + auto-save). Only use `actions/cache/save@v4` for special immediate saves. Avoid mixing both for same cache key. Auto-save is cleaner and saves only on successful completion.

**Memory 9382671 - Docker Image Optimization**  
> Use purpose-built images: `zephyrprojectrtos/zephyr-build:latest` for Zephyr. Verify exact SDK versions (e.g., 0.17.4). Eliminates 5-10min setup time. Benefits: faster builds, consistent environment, reduced network usage.

### 🔌 Hardware Specifications

**Memory 9321044 - MCXC143VFM Core Specs**
> 128KB Flash (NOT 256KB), 32KB RAM at 0x20000000. Production: 42KB app (grows to 91KB), Debug: 111KB app. Flash optimized for growth with config at end (0x1F000-0x1FFFF).

**Memory 9326413 - Flash Layout Design**
> Production: 32KB bootloader + 92KB app + 4KB config. Debug: 124KB app + 4KB config. Config partition ALWAYS at flash end for protection and future flexibility.

**Memory 9160859 - Hardware Verification**
> 33-pin QFN (32 I/O + 1 GND). Key pins: PMIC_EN=PTE17, DISP_EN=PTE16, UART2=PTD4/PTD5, I2C1=PTE0/PTE1. Verified by Ollie Hull 22/09/2025.

### 🔐 Security & MCUboot

**Memory 9331008 - Security Requirement**
> Only ONE signing key: `keys/root-ec-p256.pem`. All builds must use same key. Never duplicate keys - creates vulnerabilities and signature mismatches.

**Memory 9330272 - MCUboot UART Programming**
> Complete field programming via mcumgr over UART2 (PTD4/PTD5). Device waits 2s for commands, shows banner. Upload signed binary, reset via mcumgr. Bootloader overlay must be permanent file.

### ⚡ Development Workflow

**Memory 9369547 - Development Process**
> 1) Test with `target_scripts/test_target_board.py`, 2) Build production with commit, 3) Update via `target_scripts/firmware_update.py` (~108s), 4) Verify version matches commit hash. Remote via SSH to ajlennon@62.3.79.162:23.

**Memory 9369551 - Update Optimizations**
> Copy firmware before reset (not after). Cleanup stuck mcumgr processes at multiple stages. Timing: 1.5s reset wait, 1s bootloader init, 2s verification. Reduced time from 114.5s to 107.9s.

### 📝 Code Quality

**Memory 9359663 - Code Organization**
> Keep files under 500-800 lines. Split large files by responsibility (core/debug/advanced). Example: nfc_commands.c split into focused modules for maintainability.

**Memory 9343623 - Zephyr Best Practices**
> Device Tree integration (DT_* macros), minimal ISR context, work queues (k_work_submit()), proper device APIs, resource management, logging framework, memory safety, thread safety.

**Memory 9341442 - Path Standards**
> All references use relative paths from workspace root. Never absolute paths - breaks portability. Applies to scripts, docs, file operations.

### 🎯 System Requirements

**Memory 9291663 - Shell Interface**
> Shell is CRITICAL, never disable CONFIG_SHELL. Provides essential power management, GPIO control, diagnostics. Keep enabled even in production builds.

**Memory 9371369 - NTA5332 Integration**
> System reset: Write 0xE7 to RESET_GEN_REG at block 0x10AA using nta5332_write_config_block(). Sequence: 1) Set CONFIG_1 SRAM_ENABLE, 2) Reset, 3) Verify SRAM ready.

---

## Update Protocol

This knowledge base should be updated:
- After each development session with new learnings
- When memory conflicts are discovered and resolved  
- When best practices evolve or change
- When hardware specifications are verified/updated

**Maintenance**: AI Assistant automatically updates during development sessions
