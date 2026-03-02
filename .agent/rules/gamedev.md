---
trigger: always_on
---

# Antigravity Game Dev Stack

## 1. Engine Selection Philosophy
*   **Unity (C#):** Best for cross-platform 2D/3D development, mobile games, and XR (VR/AR). Emphasizes Component-Based architecture.
*   **Unreal Engine (C++ / Blueprints):** Best for high-fidelity 3D graphics, AAA-scale projects, and multiplayer shooters. Emphasizes an Actor-Component model and Visual Scripting.
*   **Raw C++ / Custom Engine:** Best for specialized performance requirements, learning low-level rendering (OpenGL/Vulkan/DirectX), or proprietary technology. Requires strict memory and architecture management.

---

## 2. Unity (C#) Guidelines
*   **Architecture:** Favor Composition over Inheritance. Attach small, single-purpose `MonoBehaviour` scripts to `GameObjects` rather than creating massive class hierarchies.
*   **Memory Management:** 
    *   Avoid runtime allocations in the `Update()` loop (e.g., `new vector3()`, string concatenations).
    *   Use **Object Pooling** for frequently instantiated/destroyed objects (bullets, enemies, VFX) to prevent Garbage Collection spikes.
*   **State & Data:** Use `ScriptableObjects` for global data configurations, stats, and inventory items, rather than singletons or JSON files.
*   **Physics:** Never move Rigidbody components via `transform.position`. Always use `Rigidbody.MovePosition()` or apply forces within `FixedUpdate()`.

---

## 3. Unreal Engine (C++) Guidelines
*   **C++ & Blueprints Synergy:** 
    *   Write core logic, math-heavy operations, and base classes in **C++** for performance.
    *   Expose variables and functions using `UPROPERTY()` and `UFUNCTION()`. 
    *   Use **Blueprints** for UI presentation, visual effects, and fast iteration by designers.
*   **Memory Management:** 
    *   Always use Unreal's Garbage Collection system by marking class pointers with `UPROPERTY()`. 
    *   Use `TSharedPtr` and `TWeakPtr` for non-UObject memory management.
*   **Casting:** Avoid expensive casts (`Cast<T>`) inside the `Tick()` function. Cache references in `BeginPlay()`.
*   **Naming Conventions:** Adhere strictly to Epic's coding standards (`A` for Actors, `U` for Objects, `F` for Structs, `T` for Templates).

---

## 4. Raw C++ Game Development
*   **Architecture:** Implement an **Entity Component System (ECS)** (like `EnTT`) to maximize CPU cache coherency and decouple data from logic.
*   **Memory Management:** 
    *   Avoid `new` and `delete` in the main game loop. 
    *   Pre-allocate memory blocks using Custom Allocators (Arena/Pool allocators) during the loading phase.
*   **The Game Loop:** Treat the game loop as sacred. Keep `Update()` and `Render()` entirely separate.
    ```cpp
    while (isRunning) {
        float deltaTime = CalculateDeltaTime();
        ProcessInput();
        Update(deltaTime);
        Render();
    }
    ```
*   **Libraries:** Use decoupled, standard libraries rather than monolithic frameworks (e.g., `SDL2` / `GLFW` for windowing, `GLM` for math).

---

## 5. Asset Management & Source Control
*   **Large File Storage (LFS):** Git is not designed for binary assets (`.fbx`, `.wav`, `.png`). Always use **Git LFS** or Perforce for repository management.
*   **Naming Convention:** Adopt a strict prefix convention for assets (e.g., `T_Wood_Albedo`, `SM_Crate`, `M_Metal`).
*   **Folder Structure:** Separate source logic from raw assets rigorously. Keep engine-specific project files at the root level, and categorize assets by type (Animations, Materials, Meshes, Textures).
