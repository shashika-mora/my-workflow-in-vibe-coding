---
trigger: always_on
---

# Antigravity Systems & Low-Level Stack (C++ & Rust)

## 1. Core Philosophy
*   **Safety & Performance:** Systems code must perfectly balance high performance with absolute memory safety. Do not sacrifice safety for micro-optimizations.
*   **Predictability:** Avoid unpredictable latency spikes by explicitly managing memory allocations and minimizing system calls in hot paths.
*   **Cross-Platform Portability:** Systems code should compile and run deterministically across Linux, macOS (Apple Silicon/Intel), and Windows unless specifically writing an OS-dependent abstraction layer.

## 2. Modern C++ (C++17 Minimum)
*   **Memory Management:** 
    *   Strictly enforce the use of Smart Pointers (`std::unique_ptr` and `std::shared_ptr`).
    *   Raw `new` and `delete` are forbidden unless building custom low-level memory allocators (e.g., arena allocators).
*   **Resource Management:** Follow RAII (Resource Acquisition Is Initialization) strictly. Resources must be acquired in construction and released in destruction.
*   **Constants & Computations:** Use `constexpr` aggressively to shift computation from runtime to compile time.
*   **Build System:** Use **CMake** as the single source of truth. Avoid custom Makefiles wrapper scripts.

## 3. Rust Ecosystem
*   **Safety First:** The `unsafe` keyword is strictly prohibited unless interfacing with C-APIs (FFI) or writing guaranteed correct low-level hardware structures. Every `unsafe` block MUST be preceded with a `// SAFETY: ...` comment thoroughly explaining the invariants.
*   **Error Handling:** Never use `.unwrap()` or `.expect()` in production level logic unless initializing application-critical configurations where failure means immediate crash. Always use `Result<T, E>` and propagate with `?`.
*   **Iterators & Traits:** Prefer standard library iterators combinations over explicit `for` loops. Embrace Trait-Driven Design for abstractions.
*   **Build & Management:** Use **Cargo** exclusively. Enforce formatting via `rustfmt` and aggressive linting via `clippy`.

## 4. Concurrency & Multi-threading
*   **State Sharing:** Avoid shared mutable state. Rely on message passing (channels) or atomic operations where possible.
*   **Synchronization:** If locking is necessary, always acquire locks in a consistent, established order to prevent deadlocks. Prefer `std::shared_mutex` (C++) or `RwLock` (Rust) for read-heavy data.

## 5. Foreign Function Interface (FFI)
*   When integrating low-level code with other layers (e.g., Python scripts or Node.js), isolate FFI logic strictly behind safe wrapper abstractions. Maintain a clear and minimal API surface area for cross-language calls.