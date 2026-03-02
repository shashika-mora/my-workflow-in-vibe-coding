# Antigravity Prompt Guide

*How to "hack" the Agent to get exactly what you want.*

---

## 🧪 The Golden Formula
To get the perfect result, structure your prompt like this:
`[Command/Mode] + [The Task] + [Specific Constraints]`

### Bad Prompt:
> "Make a python script for data."
*(Result: Generic, unhelpful, likely uses wrong libraries.)*

### Antigravity Prompt:
> "**[Zen Mode]** Create a Python script to clean `data.csv`. **[Constraint]** Use the **Pandas chaining** method from `stack_python_data.md` and save the result to parquet."

---

## 🎭 Mode-Based Examples

### 🚀 Speed Mode (The Builder)
*When you just want the code.*
*   **Prompt:** "Scaffold a new React component called `UserProfile`. Use a **suitable UI style** that fits our project's design system. No explanations, just code."
*   **Why it works:** Sets the visual style and forbids chatter.

### 🎓 Professor Mode (The Learner)
*When you are stuck or learning.*
*   **Prompt:** "**[Explain]** I don't understand how `useEffect` works in this file. Teach me using an analogy from a kitchen. Then quiz me."
*   **Why it works:** Defines the teaching style (Analogy) and interaction loop (Quiz).

### 🏗️ Architect Mode (The Planner)
*When you are overwhelmed.*
*   **Prompt:** "**[Plan]** I need to build a To-Do app. Don't write code yet. Outline the folder structure using the **Golden Scaffold** for Next.js and list the components we need."
*   **Why it works:** Prevents the agent from rushing into coding before the design is ready.

---

## ⚡ Power Moves (Macro Chaining)

*   **The "Audit":**
    > "Review this file. Fix any **PEP 8** violations and add docstrings to the complex functions."
*   **The "Pivot":**
    > "Stop. We are overcomplicating this. **[MVP]** Strip out the DB connection and just mock the data for now."
*   **The "Context Load":**
    > "Read `stack_mobile.md`. Now, look at `MainActivity.kt`. Does it follow our **MVVM** rules?"

---

## 📋 Copy-Paste Templates

**Feature Request:**
> "I need to add [Feature Name].
> 1. Check `07_ARCHITECTURE_PATTERNS.md` for the right pattern (Factory? Observer?).
> 2. Create the necessary files.
> 3. Update `README.md`."

**Bug Fix:**
> "I'm getting error [Error Code].
> **[Log It]** Add debug prints to trace the data flow.
> Don't fix it yet, just tell me where it breaks."
