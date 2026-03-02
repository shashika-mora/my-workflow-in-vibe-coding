# 🚨 README FIRST: The Antigravity Utility Belt

**Welcome to your new Operating System for "Vibe Coding".**
This folder contains the brain of your workflow. It defines how we (User + AI) collaborate, write code, and structure projects.

---

## 🔑 Rule Zero: The Sidebar Rule
**Always keep this `global_workflow` folder open** in your VS Code workspace, even if you are working on a different project.
**Always keep this `global_workflow` folder open** in your VS Code workspace.
*   *Why?* The AI reads `GEMINI.md` and `.agent/rules` to understand your style.

---

## 🔄 The Workflow Loop

### 1. 🏁 Starting a Project
*   **Pick a Scaffold:** Open `.antigravity/knowledge/patterns.md` or `.agent/rules/[stack].md` to see the standard structures.
*   **Safety First:** Copy `templates/gitignore_template` to your new project's `.gitignore`.

### 2. ⚡ Coding (The Vibe)
*   **Tech Stacks:** The AI will automatically check these files to ensure code quality:
    *   `.agent/rules/web.md` → Glassmorphism, Tailwind, Next.js.
    *   `.agent/rules/python_data.md` → Pandora chaining, Seaborn plots.
    *   `.agent/rules/mobile.md` → Flutter, Riverpod, GoRouter.
    *   `.agent/rules/gamedev.md` → Game Loops, Entity Component System.
*   **Shortcuts:** Use `05_MACRO_COMMANDS.md` to speed up interaction:
    *   *"Plan"* → Stop coding, start architecting.
    *   *"ELI5"* → Explain simply.
    *   *"Zen"* → Code only, no talk.

### 3. 📝 Documentation
*   **README:** Copy `templates/README_template.md` to your project root.
*   **Decisions:** Facing a tough technical choice? Copy `templates/ADR_template.md` and fill it out to remember *why* you made that choice later.

### 4. 🧠 Learning
*   **Log It:** At the end of a session, ask the AI to "Add a summary of this session to `06_LEARNING_LOG.md`".

---

## 🗺️ File Output Map

| File | Purpose |
| :--- | :--- |
| `GEMINI.md` | **The Constitution.** Global rules and philosophy. |
| `.agent/rules/*.md` | **Laws.** Project behaviors (Web, Mobile, Security). |
| `.agent/workflows/*.md` | **SOPs.** Standard Operating Procedures for tasks. |
| `.antigravity/knowledge/` | **Brain.** Patterns (`patterns.md`) and Lessons (`lessons.md`). |
| `templates/` | **Copy-Paste.** Ready-to-go files for new projects. |

---

## 🛠️ Installation & Customization
### 1. MCP Servers (Model Context Protocol)
To enable "Grounded Vibe Coding", install these servers via the Antigravity MCP Store:
*   **MCP Toolbox for Databases:** For connecting to Postgres/SQL.
*   **GitHub/Linear:** For issue tracking integration.

### 2. Security Configuration
*   **Terminal Policy:** Set to `Review-Driven` to prevent accidental `rm -rf`.
*   **File Access:** Default is Workspace Only. Grant broader access with caution.
