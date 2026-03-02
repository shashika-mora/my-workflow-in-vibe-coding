# Antigravity Systems Stack (C++/Rust)

## 1. C++
*   **Standard:** C++17 minimum.
*   **Memory Management:** 
    *   Start with `std::unique_ptr` and `std::shared_ptr`.
    *   Avoid raw `new` and `delete` unless building low-level allocators.
*   **Style:** CamelCase for functions/vars, PascalCase for Classes. 4 space indent.

## 2. Rust
*   **Safety:** No `unsafe` blocks without a documented comment explaining why it is safe.
*   **Error Handling:** Use `Result<T, E>`. proper error propagation with `?`. Avoid `unwrap()` in production code.
*   **Style:** `rustfmt` standard options.

## 3. General Low-Level
*   **Performance:** Profile before optimizing.
*   **Makefiles:** Use CMake (C++) or Cargo (Rust) as the build system source of truth.
