# Architectural Patterns Catalog

This file documents the approved coding patterns and solutions for this workspace.

## 1. Service Layer Pattern
**Problem**: UI components become bloated with business logic or data fetching logic, making them hard to test and maintain.
**Solution**: Abstract business logic and external API calls into `Service` classes or independent structural hooks (`useUserData()`). The UI component should only handle view logic and local state (`isOpen`).

## 2. API Error Wrapping
**Problem**: Generic try/catch blocks swallowed specific error types.
**Solution**: Use a centralized error handling utility for all API responses so that standard codes (401, 500) trigger universal application logic (like logging out or showing a toast message), rather than handling it within each individual feature.

*(Add new patterns as architectural decisions are made.)*
