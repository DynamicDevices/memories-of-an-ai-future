# EL133UF1 E-Ink Display Driver Project

> **Workspace Path**: `/home/ajlennon/data_drive/esl/eink-spectra6`  
> **Project Type**: Linux Kernel Driver, Embedded Graphics, C/C++  
> **Hardware**: EL133UF1 13.3" Color E-Ink Display

## Project Overview

Production-ready Linux driver for the EL133UF1 13.3" color e-ink display with direct PNG and JPEG image support, advanced dithering, and automatic landscape rotation. Cross-platform development with ARM64 cross-compilation support.

## Hardware Specifications

- **Display**: EL133UF1 13.3" Color E-Ink Display
- **Resolution**: 1200x1600 (portrait), 1600x1200 (landscape with auto-rotation)
- **Colors**: 6-color E-Ink (Black, White, Yellow, Red, Blue, Green)
- **Controller**: Dual controller architecture (side-by-side)
- **Interface**: Linux kernel driver with character device interface

## Key Features

- **Direct Image Loading**: PNG and JPEG support without external conversion
- **Advanced Dithering**: Stucki serpentine error diffusion for photographic quality
- **Automatic Rotation**: Portrait displays directly, landscape auto-rotated 90° CCW
- **Cross-Platform**: ARM64 cross-compilation with stub libraries
- **Modular Processing**: Separated image processing with command-line control

## Development Environment

- **Language**: C/C++ with Linux kernel modules
- **Build System**: CMake with cross-compilation support
- **Target Platform**: ARM64 Linux (cross-compiled)
- **Image Libraries**: PNG and JPEG processing libraries
- **Testing**: Demo mode with automatic image downloading and slideshow

## Architecture

- **Kernel Driver**: Character device interface for display control
- **Image Processing**: Modular image processing pipeline
- **Color Matching**: Intelligent 6-color E-Ink palette matching
- **Dithering Engine**: Advanced error diffusion algorithms
- **Format Support**: Multiple image formats with automatic detection

## Work Types

- **embedded-systems**: Hardware interfacing, kernel drivers
- **graphics-programming**: Image processing, dithering algorithms
- **linux-kernel**: Kernel module development, device drivers
