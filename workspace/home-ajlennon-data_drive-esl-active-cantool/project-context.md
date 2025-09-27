# CAN Bus GUI Test Tool Project

> **Workspace Path**: `/home/ajlennon/data_drive/esl/active-cantool`  
> **Project Type**: Cross-Platform GUI Application, Rust, CAN Bus  
> **Framework**: Iced GUI Framework

## Project Overview

Cross-platform CAN bus testing application with GUI built in Rust using the Iced framework. Provides abstraction layer for both Linux (SocketCAN) and Windows (PCan USB interface) with real-time monitoring and device command capabilities.

## Architecture

- **Language**: Rust with Iced GUI framework
- **Abstraction**: Trait-based `CanInterface` with platform-specific implementations
- **Linux Support**: SocketCAN via `socketcan` crate
- **Windows Support**: PCan USB DLL interface for PEAK-System CAN adapters
- **GUI Framework**: Iced for modern, cross-platform interface

## Key Features

- **Cross-Platform**: Linux (SocketCAN) and Windows (PCan USB)
- **Real-Time Monitoring**: CAN frame monitoring with timestamp and period calculation
- **Manual Frame Sending**: Hex input for custom CAN frame transmission
- **Device Commands**: Predefined commands for specific CAN devices
- **Command Builder**: Automatic parity calculation for command frames
- **Modern GUI**: Built with Iced framework for responsive interface

## Development Environment

- **Build System**: Cargo (Rust package manager)
- **Dependencies**: 
  - `iced` for GUI framework
  - `socketcan` for Linux CAN support
  - Platform-specific CAN libraries
- **Cross-Compilation**: Support for multiple target platforms
- **Testing**: Real CAN hardware required for full testing

## CAN Bus Integration

- **Protocol Support**: Standard CAN 2.0A/2.0B frames
- **Frame Types**: Data frames, remote frames, error frames
- **Filtering**: CAN ID filtering and message routing
- **Timing**: Precise timestamp and period measurements
- **Error Handling**: CAN bus error detection and reporting

## Work Types

- **rust-development**: Rust language, Cargo, cross-platform development
- **gui-applications**: Iced framework, user interface design
- **automotive-protocols**: CAN bus, automotive communication protocols
