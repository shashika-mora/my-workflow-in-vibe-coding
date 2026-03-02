---
trigger: always_on
---

# Antigravity Java & OOP Stack

## 1. Object-Oriented Programming (OOP) Fundamentals
*   **Encapsulation:** Protect object state. Fields strictly `private`. Expose behavior through methods, not just blind getters/setters.
*   **Inheritance vs. Composition:** Favor **Composition over Inheritance**. Only use inheritance for true 'is-a' relationships.
*   **Polymorphism:** Code to interfaces (e.g., `List<> list = new ArrayList<>()`), allowing interchangeable implementations.
*   **Abstraction:** Hide complex implementation details behind simple interfaces.

## 2. Object-Oriented Design (OOD) & SOLID Principles
All Java code must adhere to the **SOLID** principles:
*   **Single Responsibility (SRP):** A class should have one, and only one, reason to change.
*   **Open/Closed (OCP):** Software entities should be open for extension but closed for modification. Enable behavior changes without altering existing source code (via interfaces/abstract classes).
*   **Liskov Substitution (LSP):** Subtypes must be substitutable for their base types without altering the correctness of the program.
*   **Interface Segregation (ISP):** Clients should not be forced to depend on interfaces they do not use. Split fat interfaces into smaller, specific ones.
*   **Dependency Inversion (DIP):** Depend upon abstractions, not concretions. Always use Dependency Injection (DI) frameworks (Spring, Guice) or Constructor Injection.

## 3. Object-Oriented Software Development (OOSD)
*   **Domain-Driven Design (DDD):** Align the codebase architecture with the business domain. Use Ubiquitous Language.
*   **Immutability:** Defend against side-effects. Make classes `final` and fields `private final` whenever possible. Use `Record` types in modern Java for DTOs/Value Objects.

## 4. Required Design Patterns
Ensure these patterns are properly applied where necessary:
*   **Creational:** Use **Builder** (`@Builder` via Lombok) for complex object construction. Use **Factory Method** for creating instances of interchangeable types. Use **Singleton** *only* when absolutely guaranteed to need one instance (prefer DI).
*   **Structural:** Use **Adapter** to wrap incompatible interfaces. Use **Decorator** to attach additional responsibilities dynamically.
*   **Behavioral:** Use **Strategy** to swap out algorithms at runtime. Use **Observer** for event-driven pub/sub data flows.

## 5. Modern Java Best Practices
*   **Boilerplate:** Use **Lombok** (`@Data`, `@Getter`/`@Setter`, `@Slf4j`) carefully, but never let it violate encapsulation.
*   **Functional Parity:** Use the **Streams API** and **Lambdas** for data manipulation instead of manual `for` loops.
*   **Null Safety:** Exploit `java.util.Optional<T>` to definitively eliminate `NullPointerException`. Never use `Optional` as a class field, only as a method return type. 
*   **Testing:** Use JUnit 5 + Mockito. Name tests meaningfully (e.g., `givenInvalidId_whenFetchingUser_thenThrowsException()`).
