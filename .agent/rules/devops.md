---
trigger: always_on
---

## 1. Core Philosophy
*   **"It works on my machine" is unacceptable.** Every application must be reproducible, containerized, and documented.
*   **Zero Trust & Automation:** No manual deployments. Everything must pass through CI/CD pipelines.
*   **Infrastructure as Code (IaC):** Server configurations must be defined via code (Terraform, Pulumi, or Ansible) and tracked in Git alongside the application structure.

## 2. Containerization (Docker)
*   **Multi-Stage Builds:** Mandatory for compiled languages (Go, Rust, Java, C++) to minimize image footprint and enhance security by stripping build tools.
*   **Base Images:** 
    *   Prioritize `alpine`, `distroless`, or `slim` variants (e.g., `python:3.11-slim`) to reduce the attack surface area.
    *   Pin precise versions (e.g., `node:20.11.1-alpine`) rather than using `:latest`.
*   **Security Context:** 
    *   Never run containers as root. Create a dedicated user (`RUN adduser -D appuser` then `USER appuser`) at the end of the Dockerfile.
    *   Make the filesystem read-only where possible (`--read-only` flag via compose or Kubernetes).

## 3. Local Development (`docker-compose.yml`)
*   Define *all* systemic dependencies (Postgres, Redis, message brokers) in the compose file so `docker-compose up` gives a full working environment.
*   **Volumes & State:** Use named volumes for data persistence (e.g., databases) to prevent data loss across container restarts. Do not mount host directories for databases.
*   **Networking:** Use internal Docker hostnames (`db:5432`) for container-to-container communication. Do not hardcode `localhost`.

## 4. Continuous Integration (CI)
*   **Triggers:** CI must run on every push, pull request, and merge to `main` branch.
*   **Pipeline Stages:**
    1.  **Lint & Format:** Fail the build if code violates formatting standards (e.g., `black --check .`, `eslint`, `prettier`).
    2.  **SAST (Static Application Security Testing):** Run code scanners (e.g., SonarQube, Bandit for Python, Trivy for Docker images).
    3.  **Test Suite:** Run all unit and integration tests. The build must fail if coverage drops below the agreed threshold.
    4.  **Build:** Create the Docker image and push it to the container registry.

## 5. Continuous Deployment (CD)
*   Deployments should be triggered automatically from the `main` branch after a successful CI pass.
*   **Environment Parity:** Staging and Production environments should be as identical as possible.
*   **Rollbacks:** CI/CD must have an automated or single-click rollback strategy in case of deployment failure.

## 6. Observability & Logging
*   **Structured Logging:** Applications should output logs in JSON format (not plain text) to be easily ingested by systems like ELK or Datadog.
*   **Log Levels:** Use appropriate log levels (DEBUG, INFO, WARN, ERROR, FATAL). Do not use `ERROR` for expected behavior.
*   **Health Checks:** Every service must expose a `/health` or `/metrics` endpoint for load balancers and container orchestrators (Kubernetes/Docker Swarm) to monitor.

## 7. Versioning & Secrets Management
*   **Tags:** Docker images must be tagged with Semantic Versioning (`v1.0.0`) and the Git Commit SHA (`:sha-abcdef123`) for exact traceability.
*   **Secrets:** Never commit `.env` files. Secrets must be injected via secure vaults (GitHub Secrets, AWS Secrets Manager, HashiCorp Vault) directly into the CI/CD runners and Production environments. Mask secrets in all CI output logs.
