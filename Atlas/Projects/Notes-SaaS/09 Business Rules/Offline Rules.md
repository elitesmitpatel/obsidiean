# Offline Rules

- Downloads are explicit user actions.
- Duplicate downloads are ignored.
- Local content is stored in Dexie.
- Offline reader prefers local content.
- Firestore is fallback when no local copy exists.
- No background sync.
- No service-worker precaching of note content.
