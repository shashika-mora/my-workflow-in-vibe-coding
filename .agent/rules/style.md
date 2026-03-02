# Frontend & Backend Coding Standards

## 1. Principles
- **Functionality First:** Code must work and be tested over attempting to be perfectly clever.
- **Accuracy Over Speed:** Ten lines of clean code that explicitly handles errors is better than five lines of hacks.
- **Modularity:** Isolation of concerns is key. Use the appropriate design pattern (e.g., Service Layer offloads data tasks from components).

## 2. Formatting
- **Indentation:** 4 spaces for Python/Rust/Java/C++, 2 spaces for JS/HTML/CSS.
- **Quotes:** Double `"` for C++/Java/HTML. Single `'` internally for Python.
- **Vertical Spacing:** Feel free to use white space grouping to improve readability.

## 3. General Architecture
- **Web Applications:** React/Next.js/Vite should be structured using a component-driven architecture.
- **Vibe Checks:** Always generate a screenshot artifact after significant UI changes.
- **UI Aesthetics:** Create interfaces that are universally suitable and customized to the specific project, application, and user's desires. Ensure modern, clean aesthetics over forced generic trends.

## 4. Documentation
- Document any core classes or new service methods using JSDoc/Docstrings.
- Always add context as to 'why' a piece of code works as it does, rather than just 'what' it does.
