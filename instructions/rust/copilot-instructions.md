# Contributing to the Rust Repository

Welcome! This repository is a Rust-based application that emphasizes performance, reliability, and memory safety. It leverages Rust's strong type system and ownership model to prevent common bugs like null pointer dereferences and data races at compile time. We appreciate your contributions and ask that you follow the guidelines below to maintain code quality and consistency.

## 📌 Code Standards

### ✅ Required Before Each Commit

Before committing any changes, please ensure the following:

* **Format Code:** Run `cargo fmt` to format your code using Rustfmt.
* **Lint:** Run `cargo clippy` to identify and fix linting issues with Clippy.
* **Type Check:** Run `cargo check` to ensure there are no compilation errors without building the binary.

### 🔄 Development Flow

* **Install Dependencies:** `cargo build` (automatically fetches dependencies)
* **Start Development:** `cargo run` or `cargo run --bin <binary_name>`
* **Build Project:** `cargo build` (debug) or `cargo build --release` (optimized)
* **Run Tests:** `cargo test`
* **Full CI Check:** `cargo fmt -- --check && cargo clippy && cargo test` (includes format check, linting, and tests)

## 📁 Repository Structure

* `src/`: Main source code directory.
  * `main.rs`: Entry point for binary crates.
  * `lib.rs`: Entry point for library crates.
  * `bin/`: Additional binary entry points.
  * `modules/`: Code organized into modules.
* `tests/`: Integration tests.
* `examples/`: Example code demonstrating library usage.
* `benches/`: Benchmarks for performance testing.
* `docs/`: Documentation and developer guidelines.
* `Cargo.toml`: Project configuration and dependencies.
* `Cargo.lock`: Exact dependency versions (should be committed for applications).
* `.github/`: GitHub workflows and CI/CD configurations.

## 🛠️ Key Guidelines

1. **Rust Best Practices**

   * Follow the Rust API Guidelines for consistent and idiomatic code.
   * Use the type system to prevent bugs at compile time.
   * Prefer ownership and borrowing over raw pointers.
   * Use `Result` and `Option` types for error handling and optional values.

2. **Performance and Safety**

   * Avoid unsafe code unless absolutely necessary and well-documented.
   * Use const generics, const fn, and other zero-cost abstractions when appropriate.
   * Consider using async/await for concurrent operations when applicable.
   * Profile and benchmark performance-critical code paths.

3. **State and Data Management**

   * Use the appropriate data structures for your use case.
   * Consider using Arc/Mutex for shared mutable state across threads.
   * Leverage Rust's strong ownership model to prevent data races.
   * Use the standard library's collections effectively.

4. **Testing**

   * Write unit tests for all public functions using Rust's built-in testing framework.
   * Include documentation tests to serve as examples and to verify documentation.
   * Write integration tests for cross-module functionality.
   * Use property-based testing (e.g., proptest) for complex logic.

5. **Documentation**

   * Document all public APIs with proper rustdoc comments.
   * Include examples in documentation where appropriate.
   * Keep the README updated with build and usage instructions.
   * Use internal documentation for complex implementations.

6. **Dependencies**

   * Be mindful of adding new dependencies; evaluate their maturity and maintenance status.
   * Consider the license and security implications of dependencies.
   * Keep dependencies updated regularly.
   * Prefer crates from the wider ecosystem that solve common problems.

## 🤖 Using GitHub Copilot as a Coding Agent

To effectively leverage GitHub Copilot in this repository, please adhere to the following best practices:

### 🧩 Assigning Tasks to Copilot

* **Well-Scoped Issues:** Ensure that issues assigned to Copilot are clear and well-defined. Include:

  * A concise description of the problem or task.
  * Acceptance criteria outlining what a successful solution entails.
  * Specific files or areas of the codebase that need to be addressed.

* **Appropriate Tasks:** Assign tasks that are suitable for Copilot, such as:

  * Fixing bugs.
  * Enhancing test coverage.
  * Updating documentation.
  * Improving accessibility.
  * Addressing technical debt.

Avoid assigning complex, ambiguous, or sensitive tasks that require deep domain knowledge or involve critical business logic.

### 💬 Iterating on Pull Requests

* **Reviewing Copilot's Work:** Treat Copilot-generated pull requests as you would those from human contributors. Review the code thoroughly and provide feedback through comments.

* **Batching Comments:** If you have multiple comments, batch them using GitHub's "Start a review" feature. This approach allows Copilot to process all feedback collectively, leading to more coherent updates.

### 🛡️ Security and Best Practices

* **Code Review:** Always review and test Copilot's code suggestions to ensure they meet security standards and do not introduce vulnerabilities.

* **Prompt Engineering:** When interacting with Copilot, craft thoughtful prompts. Be specific about requirements and provide examples when possible to guide Copilot towards desired outcomes.

* **Stay Informed:** Keep up-to-date with Copilot's features and best practices by referring to the [official documentation](https://docs.github.com/en/copilot/using-github-copilot).

---

By following these guidelines, you help maintain the quality and integrity of the codebase. Thank you for your contributions!