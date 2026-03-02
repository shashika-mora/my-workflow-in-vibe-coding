# Antigravity DevOps Stack

## 1. Containerization (Docker)
*   **Philosophy:** "It works on my machine" is not an excuse.
*   **Dockerfile Standard:**
    *   **Multi-Stage Builds:** Mandatory for compiled languages (Go, Rust, Java, C++) to keep images small.
    *   **Base Images:** Use `alpine` or `slim` variants (e.g., `python:3.11-slim`) to reduce surface area.
    *   **User:** Switch to a non-root user (`USER appuser`) at the end of the Dockerfile.

## 2. Local Environment (`docker-compose.yml`)
*   Define all dependencies (Postgres, Redis) here.
*   Use named volumes for persistence:
    ```yaml
    volumes:
      db_data:
    ```
*   **Networking:** Use internal hostnames (e.g., `db:5432` not `localhost:5432`) for container-to-container comms.

## 3. CI/CD (GitHub Actions)
*   **Triggers:** Run tests on every `push` to `main` and on `pull_request`.
*   **Linter:** Fail the build if code is not formatted (e.g., `black --check .` or `eslint`).
*   **Secrets:** Never echo secrets in build logs.

## 4. Versioning
*   **Format:** Semantic Versioning (`v1.0.0`).
*   **Tags:** Docker images should be tagged with the Git Commit SHA (`:sha-12345`) for traceability.
