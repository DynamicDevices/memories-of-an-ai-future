# Rust Development Best Practices

> **Scope**: Rust programming, Cargo, cross-platform development  
> **Applications**: System programming, GUI applications, performance-critical code

## Core Rust Principles

- **Memory Safety**: Leverage Rust's ownership system to prevent memory leaks and data races
- **Zero-Cost Abstractions**: Use high-level abstractions without runtime performance penalty
- **Fearless Concurrency**: Utilize Rust's type system for safe concurrent programming
- **Error Handling**: Use `Result<T, E>` and `Option<T>` for explicit error handling
- **Pattern Matching**: Leverage match expressions for exhaustive case handling

## Project Structure

- **Cargo.toml**: Dependency management and project configuration
- **src/main.rs**: Binary entry point for applications
- **src/lib.rs**: Library entry point for reusable code
- **tests/**: Integration tests separate from unit tests
- **examples/**: Usage examples for library crates
- **benches/**: Performance benchmarks using criterion

## Cross-Platform Development

- **Conditional Compilation**: Use `#[cfg(target_os = "...")]` for platform-specific code
- **Trait Abstractions**: Create platform-agnostic interfaces with platform-specific implementations
- **Feature Flags**: Use Cargo features for optional platform-specific functionality
- **Testing**: Test on multiple platforms using CI/CD with different runners
- **Dependencies**: Choose crates with good cross-platform support

## GUI Development with Iced

- **Application Structure**: Implement `Application` trait for main app logic
- **Message-Driven**: Use message passing for UI events and state updates
- **State Management**: Keep application state in a single struct
- **View Functions**: Separate view logic from business logic
- **Styling**: Use Iced's styling system for consistent UI appearance
- **Responsiveness**: Design for different screen sizes and DPI settings

## Performance Optimization

- **Profiling**: Use `cargo flamegraph` and `perf` for performance analysis
- **Memory Usage**: Monitor memory allocation patterns and optimize hot paths
- **Compilation**: Use `--release` for production builds with optimizations
- **SIMD**: Leverage SIMD instructions for data-parallel operations
- **Async Programming**: Use `tokio` or `async-std` for I/O-bound operations

## Error Handling Patterns

- **Custom Error Types**: Define domain-specific error types with `thiserror`
- **Error Propagation**: Use `?` operator for clean error propagation
- **Error Context**: Add context to errors using `anyhow` for debugging
- **Recovery Strategies**: Implement graceful degradation and retry logic
- **Logging**: Use `log` and `env_logger` for structured error reporting

## Testing Strategy

- **Unit Tests**: Test individual functions and modules with `#[cfg(test)]`
- **Integration Tests**: Test public APIs and cross-module interactions
- **Property Testing**: Use `proptest` for property-based testing
- **Mocking**: Use `mockall` for mocking external dependencies
- **Coverage**: Monitor test coverage with `cargo tarpaulin`

## Dependency Management

- **Semantic Versioning**: Follow semver for version constraints
- **Feature Selection**: Disable default features and enable only needed ones
- **Security Auditing**: Use `cargo audit` to check for security vulnerabilities
- **License Compliance**: Verify license compatibility with `cargo license`
- **Minimal Dependencies**: Prefer smaller, focused crates over large frameworks
