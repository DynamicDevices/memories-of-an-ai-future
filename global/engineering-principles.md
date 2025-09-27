# Global Engineering Principles

> **Scope**: Universal engineering practices applicable to all projects  
> **Memory IDs**: 9382134, 9298937, 9341442

## Core Engineering Discipline

**Memory 9382134 - Critical Engineering Principle**
- Never assume code changes work until explicitly validated and proven
- Always wait for concrete evidence (builds, tests, verified functionality)
- Work as engineering collaborator, challenge assumptions and decisions
- Making assumptions without validation leads to false confidence in broken systems

## Documentation Standards

**Memory 9298937 - Documentation Policy**
- Create ONE useful README for getting started, not multiple docs
- Unmaintained documentation is worse than no documentation
- Focus on single, well-maintained documentation rather than multiple outdated files
- Only document work that actually needs to be maintained

## Project Standards

**Memory 9341442 - Path Standards**
- All scripts, commands, and file references must use relative paths from workspace root
- Never use absolute paths - breaks portability and workspace isolation
- Ensures consistency with project practices and proper workspace isolation
- Applies to build scripts, test scripts, documentation, and all file operations

**Memory 9341453 - File Generation Safety**
- Scripts must NEVER use redirection (>) to overwrite source files or configs
- Never regenerate version-controlled files with scripts
- Use temporary files, append operations (>>), or manual editing instead
- Critical for maintaining version control integrity and preventing data loss
