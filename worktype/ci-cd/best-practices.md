# CI/CD Best Practices

> **Scope**: CI/CD pipelines, build systems, automation  
> **Memory IDs**: 9382423, 9382671

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

## Build Optimization Principles

- Eliminate dependency installation time with pre-built images
- Use intelligent caching at multiple levels (dependencies, build artifacts)
- Prioritize production builds in CI (most important for releases)
- Implement proper cache invalidation strategies
- Monitor and optimize build times continuously
