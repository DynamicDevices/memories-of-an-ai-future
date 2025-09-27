# Yocto/OpenEmbedded Development Best Practices

> **Scope**: Yocto Project, BitBake, embedded Linux distribution building  
> **Applications**: Custom Linux distributions, BSP development, embedded systems

## Layer Organization

- **Layer Structure**: Follow standard Yocto layer organization (conf/, recipes-*, classes/)
- **Layer Dependencies**: Declare layer dependencies in `conf/layer.conf`
- **Recipe Categories**: Organize recipes by category (recipes-bsp, recipes-core, recipes-kernel)
- **Version Control**: Keep layers in separate Git repositories for modularity
- **Documentation**: Maintain README.md with layer purpose, dependencies, and usage

## Recipe Development

- **Recipe Naming**: Use descriptive names following `<package>_<version>.bb` convention
- **Source Management**: Use `SRC_URI` with checksums for reproducible builds
- **Patch Management**: Keep patches minimal and well-documented
- **License Handling**: Specify `LICENSE` and `LIC_FILES_CHKSUM` correctly
- **Dependencies**: Use `DEPENDS` (build-time) and `RDEPENDS` (runtime) appropriately

## Machine Configuration

- **Machine Files**: Define hardware-specific settings in `conf/machine/<machine>.conf`
- **Device Trees**: Manage device tree sources and overlays systematically
- **Kernel Configuration**: Use kernel fragments for modular kernel configuration
- **Bootloader Integration**: Configure U-Boot and other bootloaders properly
- **Hardware Abstraction**: Abstract hardware differences through machine features

## Build Optimization

- **Shared State Cache**: Use `SSTATE_DIR` for faster incremental builds
- **Download Directory**: Configure `DL_DIR` for source download caching
- **Parallel Builds**: Optimize `BB_NUMBER_THREADS` and `PARALLEL_MAKE` for build host
- **Build History**: Enable build history tracking for debugging and analysis
- **Clean Builds**: Use `bitbake -c cleanall` when needed for problematic recipes

## Image Customization

- **Image Recipes**: Create custom image recipes inheriting from core-image classes
- **Package Groups**: Use `packagegroup-*` recipes for logical package grouping
- **Feature Selection**: Use `IMAGE_FEATURES` and `DISTRO_FEATURES` for functionality
- **Size Optimization**: Monitor image size and optimize for target constraints
- **Security Hardening**: Enable security features and remove unnecessary packages

## Development Workflow

- **Local Development**: Use `devtool` for iterative recipe development
- **SDK Generation**: Create SDKs for application development with `bitbake -c populate_sdk`
- **Testing**: Implement automated testing with `oe-selftest` and custom test suites
- **Debugging**: Use `bitbake -e` and `bitbake -g` for recipe analysis
- **Version Control**: Tag releases and maintain stable branches

## Cross-Compilation

- **Toolchain Management**: Understand cross-compilation toolchain configuration
- **Sysroot Handling**: Properly manage target sysroot for dependencies
- **Native vs Target**: Distinguish between native tools and target packages
- **Architecture Support**: Configure for ARM, ARM64, x86, and other architectures
- **Multilib Support**: Handle multiple library architectures when needed

## Integration and Testing

- **CI/CD Integration**: Automate builds with Jenkins, GitHub Actions, or similar
- **Hardware Testing**: Test images on actual target hardware
- **Regression Testing**: Maintain test suites for critical functionality
- **Performance Testing**: Monitor build times and image boot performance
- **Documentation**: Keep build instructions and troubleshooting guides updated

## Security Considerations

- **Secure Boot**: Implement secure boot chain with signed images
- **Package Signing**: Sign packages and verify signatures during installation
- **CVE Tracking**: Monitor and patch security vulnerabilities
- **Minimal Attack Surface**: Remove unnecessary services and packages
- **Update Mechanisms**: Implement secure OTA update systems

## Troubleshooting

- **Build Failures**: Analyze build logs and use `bitbake -v` for verbose output
- **Dependency Issues**: Use `bitbake -g` to visualize dependency graphs
- **Recipe Debugging**: Use `devshell` for interactive recipe debugging
- **Performance Issues**: Profile builds and optimize bottlenecks
- **Version Conflicts**: Resolve version conflicts between layers and recipes
