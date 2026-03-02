---
trigger: always_on
---

# Database & Data Engineering Guidelines

## 1. Choosing the Right Tool
We use both **SQL** and **NoSQL** depending on the specific application needs:
*   **SQL (PostgreSQL/MySQL):** Use when data is highly relational, requires complex transactions (ACID), or needs structural integrity.
*   **NoSQL (Firebase/MongoDB):** Use for rapid prototyping, real-time syncing, flexible schemas, or document-heavy structures.

## 2. SQL Best Practices
*   **Formatting:** Keywords UPPERCASE (`SELECT`, `FROM`, `WHERE`).
*   **Naming:** `snake_case` for tables and columns.
*   **Safety:** Parameterized Queries ONLY. String concatenation for SQL is forbidden.
*   **Migrations:** Always use a migration tool (Flyway, Alembic, Prisma, or framework native) for schema changes. *Never mutate schemas manually in production.*

## 3. NoSQL Best Practices
*   **Structure:** Flatten data where possible to avoid deep nesting limits and optimize read speeds.
*   **References:** Do not hardcode collection names in multiple places. Use global constants.
*   **Batching:** Use batched writes or transactions for writing to multiple documents simultaneously.

## 4. Security & Access
*   **Credentials:** Never hardcode connection strings. Always use `.env` files. Ensure the database user has the principle of least privilege.
*   **Sanitization:** Always validate and sanitize input prior to executing database queries.

## 5. MCP Server Integrations
Agents must leverage Model Context Protocol (MCP) servers for grounded database interactions:
*   **SQL Connections:** Use the `MCP Toolbox for Databases` to connect to live SQL schemas. Agents should run `DESCRIBE` or `\d` equivalents via MCP before writing query logic.
*   **Cloud Data Stores:** Connect to external services (like Firebase/BigQuery) via their respective MCP servers to securely test reads and writes during development without guessing data structures.
