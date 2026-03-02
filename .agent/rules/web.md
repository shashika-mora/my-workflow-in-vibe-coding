# Antigravity Web Stack

## 1. The Core Stack
*   **Framework:** Next.js (App Router) for Apps; Vite (React) for SPAs.
*   **Styling:** Tailwind CSS. 
    *   *Rule:* Order utility classes logically (Layout → Spacing → Typography → Visuals).
*   **Language:** TypeScript preferred. JSDoc-typed Javascript allowed for "Vibe Coding" speed.
*   **State Management:**
    *   **Server:** React Query (TanStack Query).
    *   **Client Global:** Zustand.
    *   **Context:** For theming/static global data only.

## 2. Design System: "Neo-Glass"
*   **Philosophy:** Depth over flatness. UI elements should feel like they exist in 3D space.
*   **Tokens:**
    *   `backdrop-blur-md` or `backdrop-blur-lg`.
    *   `bg-white/10` or `bg-black/20` for surfaces.
    *   `border-white/20` for subtle definition.
    *   `shadow-xl` to lift elements.

## 3. Golden Scaffold (Web App)
```text
project_name/
├── public/                # Static assets
├── src/
│   ├── app/               # Next.js App Router Pages
│   ├── components/
│   │   ├── ui/            # Primitive/Dumb (Buttons, Inputs)
│   │   └── features/      # Smart/Business Logic (UserProfile)
│   ├── lib/               # Utilities, Helpers, API clients
│   └── hooks/             # Custom React Hooks
├── package.json
└── .env.local
```

## 4. Component Architecture
*   **Atomic Hierarchy:**
    *   Keep "dumb" UI components separate from "smart" feature components.
*   **Exports:** Named exports preferred (`export function Button()`).
