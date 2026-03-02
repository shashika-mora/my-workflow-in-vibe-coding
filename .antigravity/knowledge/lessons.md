# Post-Mortem & Lessons Learned

Use this file to record persistent errors or systemic bugs so that the AI doesn't repeat them.

## Issue #1: Vibe Coding Resulted in Infinite Loop
**Description:** Rapid vibe prototyping of a React functional component caused an infinite rendering loop due to improper dependency array management in `useEffect`.
**Fix:** Always include a comprehensive dependency array in `useCallback`, `useMemo`, and `useEffect` hooks. Run an ESLint pass on the component before validating the artifact.

*(Add new lessons as development continues.)*
