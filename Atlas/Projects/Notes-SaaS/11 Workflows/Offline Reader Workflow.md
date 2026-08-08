# Offline Reader Workflow

1. Reader requests note ID.
2. `useOfflineNote` checks [[Downloaded Notes Table]] first.
3. If found, local note is displayed and [[Offline Badge]] appears.
4. If not found, the hook falls back to published Firestore note.
5. `hasUpdateAvailable(remote.version, local.version)` detects newer content.

## Version rule
See [[Note Versioning Rule]].
