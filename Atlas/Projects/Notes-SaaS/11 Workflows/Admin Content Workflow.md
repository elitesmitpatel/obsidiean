# Admin Content Workflow

1. User enters `/admin/*`.
2. [[AdminRoute]] checks Auth + profile role.
3. ADMIN sees content list.
4. Admin creates/edits subject, topic, or note.
5. Service writes Firestore.
6. TanStack Query invalidates relevant caches.
7. Published note changes propagate to reader/search/offline behavior.

## Note-specific
- `searchableText` is derived automatically.
- `version` increments iff content changes.
