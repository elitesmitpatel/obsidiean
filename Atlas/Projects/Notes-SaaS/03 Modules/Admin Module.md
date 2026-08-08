# Admin Module

**Location:** `src/features/admin/` and `src/pages/admin/`

## Responsibility
ADMIN-only CRUD for subjects, topics, and notes.

## Guard
[[AdminRoute]] reads [[Users Collection]] role through [[Profile Module]].

## Data
[[Subjects Collection]], [[Topics Collection]], [[Notes Collection]].

## Mutations
Create/update/archive/restore-style status operations through existing services. There is no permanent content delete in the admin UI.

## Derived data
`noteService` derives `searchableText` from Markdown content. Note `version` increments only when note `content` changes.

## UI
[[Admin Dashboard Screen]], [[Admin Subjects Screen]], [[Admin Topics Screen]], [[Admin Notes Screen]].

## Change Impact
Changing admin authorization affects UI access and Firestore rules. Changing content schemas affects forms, services, indexes, search, reader, and offline behavior. Changing query invalidation affects both admin and student caches.
