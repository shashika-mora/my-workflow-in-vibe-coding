# Antigravity Java Stack

## 1. Core Principles
*   **Approach:** Interface-driven design. Code to interfaces, not implementations.
*   **Boilerplate:** Use Lombok (`@Data`, `@Builder`) to reduce clutter.
*   **Modern Java:** Use Streams API and Lambdas for collection processing.

## 2. Structure
*   **Standard Maven/Gradle Layout:**
    *   `src/main/java`
    *   `src/test/java`
*   **Naming:** PascalCase for Classes, camelCase for methods/variables.

## 3. Testing
*   **Framework:** JUnit 5.
*   **Mocking:** Mockito.
*   **Rule:** meaningful test names: `shouldReturnUserGivenValidId()`.
