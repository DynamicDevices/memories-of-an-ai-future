# CI/CD Best Practices

> **Scope**: CI/CD pipelines, build systems, automation  
> **Memory IDs**: 9382423, 9382671, 9385453, 9385633, 9386531, 9386536, 9386540, 9386543, 9386549

## Caching Strategy

**Memory 9382423 - CI/CD Cache Strategy Best Practice**
- Use `actions/cache@v4` for most caching needs (auto-restore + auto-save)
- Only use explicit `actions/cache/save@v4` for special immediate save cases
- Avoid mixing both for same cache key - creates conflicts
- Auto-save approach saves only on successful workflow completion (usually desired)
- GitHub Actions' default cache behavior is well-designed for most scenarios

## Docker Image Optimization

**Memory 9382671 - CI/CD Docker Image Optimization**
- Always use purpose-built Docker images instead of generic OS images
- For Zephyr: `zephyrprojectrtos/zephyr-build:latest` from Docker Hub
- Verify and enforce exact SDK versions (add version checks if needed)
- Benefits: 5-10min faster builds, consistent environment, reduced network usage
- Apply to other ecosystems: node:18, python:3.11, rust:1.70, etc.
- Generic ubuntu/alpine only when no specialized image exists

## Environment Mirroring

**Memory 9385453 - Mirror Local Development Environment**
- CI/CD should mirror local development environment exactly
- Use same build scripts, environment variables, toolchain versions
- CI acts as validation and artifact controller, not different build environment
- Avoid CI-specific build logic that differs from local development
- Prevents "works on my machine" problems in reverse

## Simplicity Principles

**Memory 9385633 - Do Not Overcomplicate**
- Always prioritize simplicity over complexity
- Each step should have single, clear purpose
- Eliminate duplication and redundancy ruthlessly
- Best CI/CD pipelines are boring and predictable
- Question fundamental assumptions before adding complexity
- Ask "why is this needed?" and "what if we don't do this?"

## System Integration Wisdom

**Memory 9386531 - Work WITH the System**
- Don't assume "already initialized" states are errors
- Often means system is in desired state - that's good!
- Example: Check if workspace exists before initializing
- Respect existing state instead of fighting against it
- Ask "why is this a problem?" before complex workarounds

**Memory 9386536 - Question Assumptions**
- Challenge every assumption before implementing solutions
- Ask: "Why do we need cleanup?", "Why is this a problem?"
- Often simplest solution is working with existing state
- Prefer logical approaches over complex workarounds

## Performance Optimization

**Memory 9386540 - Avoid System-Wide Operations**
- Never use `find / -name pattern` in CI/CD (20+ minute hangs)
- Use targeted cleanup of known locations only
- System-wide operations create performance bottlenecks
- Always prefer specific, targeted operations

**Memory 9386543 - Eliminate Duplication**
- Audit for: duplicate caches, repeated env setup, redundant debug output
- Workflows accumulate duplication through iterative fixes
- Example: 155→109 lines (30% reduction) while maintaining functionality
- Duplication makes workflows slow, confusing, hard to debug

## Operation Sequencing

**Memory 9386549 - Order Matters**
- Understand what each step creates/modifies
- Map out dependencies before implementing fixes
- Example: SDK install creates CMake registry, cleanup must happen AFTER
- Wrong order causes cascading failures

## Build Optimization Principles

- Eliminate dependency installation time with pre-built images
- Use intelligent caching at multiple levels (dependencies, build artifacts)
- Prioritize production builds in CI (most important for releases)
- Implement proper cache invalidation strategies
- Monitor and optimize build times continuously
