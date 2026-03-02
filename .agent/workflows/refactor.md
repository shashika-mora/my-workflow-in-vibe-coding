---
description: Workflow for safe code refactoring
---
# Safe Refactoring Workflow

Use this workflow to clean up or optimize code without changing its external behavior.

1. **Test Coverage Analysis**:
   - Identify existing tests for the module being refactored.
   - If tests are missing, create them first to establish a baseline.
2. **Plan Refactor**:
   - Outline the specific changes, design patterns to apply, and why they are necessary.
   - Present the plan before writing code.
3. **Approval**:
   - Wait for user approval on the plan.
4. **Iterative Refactoring**:
   - Apply the refactoring step-by-step.
   - Keep commits small and atomic.
5. **Verification**:
   - Run the test suite after each atomic change to verify nothing broke.
   - Compare performance or readability improvements.
