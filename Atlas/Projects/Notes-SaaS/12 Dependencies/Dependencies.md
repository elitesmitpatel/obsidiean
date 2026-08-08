# Dependencies

## Runtime / core

- React
- React Router
- TanStack Query
- Firebase SDK
- Dexie
- React Markdown
- Tailwind CSS
- Lucide React
- Radix Slot
- class-variance-authority

## Build/test

- Vite
- TypeScript
- Vitest
- Testing Library
- ESLint
- PWA plugin/tooling

## Dependency rules

Do not add a dependency to solve a problem already covered by the existing architecture without an explicit requirement.

## Change impact

Dependency upgrades can affect bundle size, build output, browser compatibility, type behavior, and tests. High-risk dependencies: Firebase, React Router, TanStack Query, Dexie, React Markdown, PWA tooling.
