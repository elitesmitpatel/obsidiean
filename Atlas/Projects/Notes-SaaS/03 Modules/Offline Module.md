# Offline Module

**Location:** `src/features/offline/`

## Responsibility
Download published note content to IndexedDB, read it locally, compare versions, and remove downloads.

## Persistence
[[Downloaded Notes Table]]

## Service
`offlineService.ts` provides download, remove, lookup, list, storage-size, and update functions.

## Hooks
- `useDownloadedNotes`
- `useOfflineNote`
- `useDownloadNote`
- `useRemoveDownload`

## UI
[[Note Reader Screen]], [[Downloads Screen]], [[Download Button]], [[Offline Badge]].

## Important behavior
`useOfflineNote` checks Dexie first. If no local note exists, it falls back to the published Firestore note.

## Change Impact
Changing offline schema affects Dexie migrations and all offline hooks. Changing note version semantics affects update availability. Changing stored note fields affects offline reader, downloads list, storage calculation, and existing local data. Never silently change Dexie schema without a migration plan.
