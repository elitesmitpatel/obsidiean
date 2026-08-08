# TanStack Query Integration

Owns Firestore server state and offline queries/mutations.

Representative query keys:
- `['subjects','active']`
- `['topics','active', subjectId]`
- `['notes','published', topicId]`
- `['note', noteId]`
- `['bookmarks', userId]`
- `['profile', uid]`
- `['offline','downloaded-notes']`

Admin mutations invalidate student/admin caches as appropriate.
