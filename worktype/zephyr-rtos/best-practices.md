# Zephyr RTOS Best Practices

> **Scope**: Zephyr RTOS development, device drivers, system integration  
> **Memory IDs**: 9343623, 9347422, 9331853

## Core Development Practices

**Memory 9343623 - Zephyr RTOS Best Practices**
- **Device Tree Integration**: Use DT_* macros, gpio_pin_*_dt() APIs
- **Minimal ISR Context**: No blocking operations, logging, or I2C in interrupt handlers
- **Work Queue Usage**: Defer complex work to thread context using k_work_submit()
- **Device API Compliance**: Use device_is_ready(), proper error codes (-ENODEV, -EINVAL, -ENOMEM)
- **Resource Management**: Proper GPIO/I2C device acquisition and release
- **Logging Framework**: Use LOG_MODULE_REGISTER() and appropriate log levels
- **Memory Safety**: Use k_malloc/k_free for large buffers >64 bytes, avoid stack overflow
- **Thread Safety**: Use mutexes/semaphores for shared resources like I2C devices

## Platform Migration Strategy

**Memory 9347422 - Zephyr Migration Success**
- Custom board definitions in app/boards/ are sufficient - no custom Zephyr fork needed
- Use device tree overlays and memory overrides for hardware-specific configurations
- Benefits of upstream Zephyr: simplified maintenance, no fork overhead, automatic updates
- Standard toolchain integration (Zephyr SDK) provides better compatibility
- Architecture proves custom board definitions handle most hardware variations

## Device Tree Configuration

**Memory 9331853 - Device Tree Overlay Processing**
- Use DTC_OVERLAY_FILE (not EXTRA_DTC_OVERLAY_FILE) for complete control
- DTC_OVERLAY_FILE replaces default overlay search, EXTRA_DTC_OVERLAY_FILE adds after
- Overlay processing order critical - base board DTS can override overlay settings
- Include /delete-property/ or complete node overrides to properly override base settings
- Verify final device tree (build/zephyr/zephyr.dts) shows correct overlay application
