# Embedded Systems Hardware Design

> **Scope**: Microcontroller hardware, memory layouts, system design  
> **Memory IDs**: 9326413, 9359663, 9330693

## Memory Layout Design

**Memory 9326413 - Optimized Flash Layouts**
- Design flash layouts for maximum future growth, not just current needs
- Always place configuration partition at end of flash for protection
- Optimize partition sizes to allow 2-3x application growth without layout changes
- Example: Production (32KB boot + 92KB app + 4KB config), Debug (124KB app + 4KB config)
- Config at end allows extending app partitions in future if needed

## Code Organization for Embedded

**Memory 9359663 - Code Organization Standards**
- Keep source files under 500-800 lines for maintainability
- Break large files into focused modules by responsibility
- Example: Split nfc_commands.c into nfc_core_commands.c, nfc_debug_commands.c, nfc_advanced_commands.c
- Improves maintainability, readability, and code review efficiency
- Single responsibility principle applies to embedded code organization

## Resource Management

**Memory 9330693 - Production Build Resource Constraints**
- Production builds should constrain FLASH usage, not RAM resources
- RAM is typically not the limiting factor in modern microcontrollers
- Hard faults often caused by incorrectly constraining RAM when only flash optimization needed
- Keep same RAM allocations (stack, heap) in production, optimize flash usage instead
- Use feature reduction, logging levels, and compiler optimizations for flash savings
