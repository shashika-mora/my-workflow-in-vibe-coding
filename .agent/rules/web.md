---
trigger: always_on
---

# Antigravity Web Development Stack

## 1. The Core Stack
*   **Framework:** Next.js (App Router) for heavy full-stack Apps; Vite (React) for Fast SPAs.
*   **Styling:** Vanilla CSS or Tailwind CSS (if explicitly chosen). 
    *   *Rule:* Order utility classes logically (Layout → Spacing → Typography → Visuals).
*   **Language:** TypeScript is strictly preferred for enterprise maintainability.
*   **State Management:**
    *   **Server State:** React Query (TanStack Query) or SWR to handle caching and async data.
    *   **Client Global:** Zustand.
    *   **Context:** Use standard React Context strictly for theming or static, rarely-changed global data.

## 2. Design System & Aesthetics
*   **Adaptive Design:** UI elements must be dynamically styled to best fit the project's brand guidelines. Do not enforce rigid styles (like "glassmorphism") unless explicitly requested.
*   **Visual Excellence:** Prioritize modern typography, curated color palettes, smooth hover effects, and micro-animations to create a premium feel.
*   **Responsiveness:** All pages must be mobile-friendly and utilize CSS Grid / Flexbox layouts for structural integrity.

## 3. SEO & Semantic Best Practices
Automatically implement SEO best practices on every page:
*   **Title Tags & Meta:** Include proper, descriptive title tags and meta descriptions.
*   **Heading Structure:** Use a single `<h1>` per page with proper hierarchical progression (`<h2>`, `<h3>`).
*   **Semantic HTML:** Use appropriate HTML5 semantic elements (`<main>`, `<article>`, `<nav>`, `<section>`).
*   **Accessibility (a11y):** All interactive elements must be keyboard navigable and contain appropriate ARIA labels or alt text.

## 4. Golden Scaffold (Web App)
```text
project_name/
├── public/                # Static assets (images, fonts, robots.txt)
├── src/                   # Main source code
│   ├── app/               # Next.js App Router Pages (or pages/ for Vite)
│   ├── components/
│   │   ├── ui/            # Primitive/Dumb (Buttons, Inputs, Modals)
│   │   └── features/      # Smart/Business Logic (UserProfile, AuthForm)
│   ├── lib/               # Utilities, Helpers, API clients (axios/fetch config)
│   ├── hooks/             # Custom React Hooks for encapsulating logic
│   └── styles/            # Global CSS, Tailwind configurations
├── package.json
└── .env.local             # Secrets (Ignored by Git)
```

## 5. Component Architecture
*   **Atomic Hierarchy:** Keep "dumb" presentation UI components strictly separate from "smart" feature components that fetch or mutate data.
*   **Single Responsibility:** A component should only do one thing well. If it grows past 150 lines, it likely needs to be broken down.
*   **Exports:** Named exports are strictly preferred (`export function Button()`) over default exports to avoid naming collisions during imports.