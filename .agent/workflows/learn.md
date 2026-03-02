---
description: Generate educational content for the user
---
# Socratic Learning Workflow

This workflow triggers the educational agent to teach the user about specific topics or codebase patterns.

1. **Topic Identification**:
   - Identify the user's requested topic (e.g., React Hooks, Service Layer Pattern).
2. **Codebase Scan**:
   - The agent scans the `src/` or `app/` directory for real-world examples of this topic in the active project.
3. **Generate Lesson Artifact**:
   - Create a Markdown document explaining the concept.
   - Use actual snippets from the project as examples.
   - Do NOT just write code for the user; ask probing questions to test their understanding.
4. **Socratic Questioning**:
   - E.g., "To implement this feature, we could use a custom hook or a higher-order component. Which approach aligns better with your understanding of the current architecture?"
5. **Knowledge Base Update**:
   - Log any new insights into `.antigravity/knowledge/LESSONS.md`.
