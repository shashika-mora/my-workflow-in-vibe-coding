---
trigger: always_on
---

# Antigravity General Security & Auth Guidelines

## 1. Secrets & API Keys
*   **No Hardcoding:** Never hardcode passwords, API keys, or access tokens within the codebase. Always use environmental variables (`.env`).
*   **Git Credential Leaks:** NEVER commit `.env` files, `.pem` keys, or credential JSONs. Always verify git diffs before pushing to avoid leaking private credentials to GitHub.
*   **Pre-commit Hooks:** Use tools like `git-secrets` or `trufflehog` to scan for accidental commits if the project allows it.

## 2. Authentication & Authorization (JWT)
*   **JSON Web Tokens (JWT):** Never store sensitive user data (like passwords or PII) inside the payload of a JWT. JWTs are base64 encoded, *not* encrypted.
*   **Token Storage:**
    *   *Web:* Store JWTs in `HttpOnly`, `Secure`, `SameSite=Strict` cookies to defend against XSS. Avoid storing them in `localStorage`.
    *   *Mobile:* Store tokens in the OS secure enclave (e.g., EncryptedSharedPreferences, Keychain/flutter_secure_storage).
*   **Token Expiry:** Always implement short-lived Access Tokens and long-lived Refresh Tokens.

## 3. Data Injection Prevention
*   **SQL Injection (SQLi):** Never use string concatenation to build database queries. Strictly use Parameterized Queries or an ORM/Query Builder.
*   **Cross-Site Scripting (XSS):** Always sanitize and encode user input before rendering it in the UI (e.g., using React's default protection, or DOMPurify if manipulating `innerHTML`).
*   **Command Injection:** Avoid passing raw user input to `os.system()` or `subprocess.run()`. Validate against a strict allowlist.

## 4. Agent Safety Policies
*   **File Access:** Agent modifications are scoped solely to application directories (`/src`, `/app`, `/tests`). AI should not touch shell profiles or OS configurations.
*   **Database Operations:** Destructive queries like `DROP TABLE`, or schema migrations must require human review before execution.
*   **Terminal Execution:** No destructive commands like `rm -rf` without strict justification and a review prompt.
