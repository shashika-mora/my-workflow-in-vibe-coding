---
trigger: always_on
---

# Antigravity Frontend & Backend Coding Standards

## 1. Core Principles
*   **Functionality First:** Code must work and be fully tested before attempting to be "clever". Readability over brevity.
*   **Accuracy Over Speed:** Ten lines of clean, explicit, and error-handling code is infinitely better than five lines of brittle hacks.
*   **Modularity:** Strong isolation of concerns. Decouple business logic from UI components (e.g., utilize Service Layer or custom Hooks to offload data tasks).

## 2. Formatting & Syntax
*   **Indentation:**
    *   `4 spaces` for backend and systems languages: Python, Rust, Java, C++, C#.
    *   `2 spaces` for frontend and configuration: JS, TS, HTML, CSS, YAML, JSON.
*   **Quotes:**
    *   Use double `"` for C++, Java, HTML, and JSON.
    *   Use single `'` internally for Python, JS, and TS (unless dealing with JSX attributes).
*   **Vertical Spacing:** Liberally use blank lines to group logical blocks of code and improve scannability.

## 3. General Architecture
*   **Web Frameworks:** Use Component-Driven Architectures for frameworks like React, Next.js, and Vite.
    *   *Rule:* Keep components small and focused. Extract complex logic into utilities.
*   **State Management:** Differentiate local state (form inputs, toggles) from global state (user sessions, themes). Don't bloat global stores unnecessarily.
*   **API Interactions:** Centralize API calls in a dedicated `api/` or `services/` directory rather than making raw `fetch`/`axios` calls inside UI components.

## 4. UI Aesthetics & Vibe
*   **Adaptive Design:** Create interfaces that are universally suitable and customized to the specific project, application, and user's desires.
*   **Visual Quality:** Ensure modern, clean aesthetics over forced generic trends. Utilize tailored design systems (e.g., curated Tailwind CSS palettes, polished Vanilla CSS).
*   **Verification:** Always generate a screenshot or browser artifact recording after making significant UI changes to perform a "vibe check" with reality.

## 5. Documentation & Comments
*   **Code Documentation:** Document core classes, complex interfaces, and new service methods using standard language conventions (JSDoc, Docstrings, JavaDoc).
*   **In-line Comments:** Always add context as to **'why'** a specific, non-obvious piece of code was written, rather than just **'what'** it does.
*   **Self-Documenting Code:** Prioritize descriptive variable and function names (e.g., `isUserLoggedIn` instead of `flag`) over writing comments to explain bad names.
