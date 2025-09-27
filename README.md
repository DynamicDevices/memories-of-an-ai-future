# Memories of an AI Future - Hierarchical Knowledge System

> **AI Assistant Knowledge Base with Contextual Loading**

This repository contains a hierarchical memory system for AI assistants, organized by scope and automatically loaded based on workspace context.

## Memory Hierarchy

```
📁 memories-of-an-ai-future/
├── 🌍 global/                    # Universal engineering principles
│   └── engineering-principles.md
├── 🔧 worktype/                  # Domain-specific best practices
│   ├── ci-cd/
│   │   └── best-practices.md
│   ├── embedded-systems/
│   │   └── hardware-design.md
│   └── zephyr-rtos/
│       └── best-practices.md
├── 🏠 workspace/                 # Project-specific context
│   └── home-ajlennon-data_drive-esl-eink-microcontroller/
│       ├── project-context.md
│       └── development-environment.md
├── .cursorrules                  # Auto-loaded by Cursor
├── workspace-mapping.json       # Workspace → Memory mapping
└── README.md                    # This file
```

## Loading Strategy

**Hierarchical Context Loading**: Global → Work Type → Workspace Project

1. **Global Memories** (Always loaded)
   - Universal engineering principles
   - Documentation standards
   - File safety rules

2. **Work Type Memories** (Based on project domain)
   - `ci-cd`: GitHub Actions, Docker, build optimization
   - `embedded-systems`: Hardware design, memory layouts
   - `zephyr-rtos`: Device tree, drivers, RTOS practices

3. **Workspace Memories** (Project-specific)
   - Hardware specifications and pin assignments
   - Development workflows and testing procedures
   - Security requirements and build configurations

## Workspace Detection

The system automatically detects workspace context based on file paths:

- **Path**: `/home/ajlennon/data_drive/esl/eink-microcontroller`
- **Maps to**: `workspace/home-ajlennon-data_drive-esl-eink-microcontroller/`
- **Work Types**: embedded-systems, zephyr-rtos, ci-cd

## Current Project Context

**MCXC143VFM E-Ink Power Controller**
- ARM Cortex-M0+ microcontroller (128KB Flash, 32KB RAM)
- Zephyr RTOS with MCUboot bootloader
- CI/CD pipeline with GitHub Actions
- Remote development and testing infrastructure

## Usage

### Cursor Integration
The `.cursorrules` file is automatically loaded and provides:
- Workspace detection and memory loading strategy
- Condensed context from all relevant memory levels
- Project-specific rules and constraints

### Manual Reference
- Browse `global/`, `worktype/`, and `workspace/` directories
- Use `workspace-mapping.json` to understand project relationships
- Reference specific memory files for detailed technical knowledge

### Memory Updates
AI assistants should:
1. Update memories after significant development sessions
2. Add new workspace mappings for new projects
3. Maintain the hierarchical organization
4. Commit changes to preserve knowledge

## Benefits

- **Contextual Relevance**: Only load memories relevant to current work
- **Scalable Organization**: Easy to add new projects and work types
- **Automatic Loading**: Cursor integration provides seamless context
- **Knowledge Preservation**: Structured storage prevents knowledge loss
- **Team Sharing**: Version-controlled memories accessible to all team members

## Maintenance

- **Auto-Updated**: AI assistants update during development sessions
- **Conflict Resolution**: Newer memories take precedence
- **Validation**: Technical claims verified against implementations
- **Expansion**: New work types and workspaces added as needed

---

**Repository**: `git@github.com:DynamicDevices/memories-of-an-ai-future.git`  
**Maintainer**: AI Assistant (Claude Sonnet 4)  
**Last Updated**: 2025-09-27