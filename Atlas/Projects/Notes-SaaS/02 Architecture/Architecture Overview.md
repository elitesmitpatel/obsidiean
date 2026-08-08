# Architecture Overview

## Primary flow

`UI Component → React Hook → TanStack Query → Service → Firebase/Firestore`

Offline content uses:

`UI Component → Offline Hook → Offline Service → Dexie/IndexedDB`

Authentication uses React Context because auth state is client session state, not server data.

## Layers

### UI

Pages and feature components render screens and user interactions.

### Hooks

TanStack Query hooks own asynchronous server state and mutations.

### Services

Services are the only application layer that directly calls Firestore/Auth SDK operations.

### Persistence

- Firestore: authoritative application data.
- Firebase Authentication: identity/session.
- IndexedDB/Dexie: downloaded note content for offline reading.

### Routing

[[Router]] maps URLs to pages. [[ProtectedRoute]] gates authenticated routes. [[AdminRoute]] gates ADMIN-only routes. [[AppLayout]] supplies the authenticated shell.

## State ownership

See [[State Ownership]].

## Architectural invariants

- No Firebase SDK access directly from UI components for Firestore/Auth operations.
- No Redux/Zustand.
- TanStack Query owns server state.
- Auth state is React Context.
- Offline note data is Dexie-backed.
- No Storage provider exists in the current architecture.
