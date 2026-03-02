# General Security Guidelines

## 1. Safety Rules
- **No Hardcoding Secrets:** Never commit passwords, API keys, or access tokens within the codebase. Always use environmental variables.
- **Never Commit `__pycache__` or `.env`:** These are to be in the `.gitignore` immediately.
- **No Silent Failures:** Log all warnings and errors rather than catching and ignoring them.

## 2. Agent Policies
- **File Access:** Agent modifications should generally be scoped to `/src`, `/app`, or `/tests` directories. Avoid editing unrequested configuration files without user confirmation.
- **Database Safety:** Operations like `DROP TABLE` or schema-altering migrations must require an explicit human review step.
- **Terminal Execution:** No destructive commands like `rm -rf` without a strict justification and review prompt.
