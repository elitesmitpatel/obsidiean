# Database Module

**Location:** `src/db/`

## Responsibility
Dexie database for offline downloaded notes.

## Database
`notesOfflineDB`

## Tables
- `downloadedNotes`
- legacy `downloadedAttachments` table is removed through Dexie v2 migration.

See [[Downloaded Notes Table]].

## Change Impact
Database schema changes require Dexie versioning/migration and affect offline service, hooks, reader, downloads page, and existing client data.
