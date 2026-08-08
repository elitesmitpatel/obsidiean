# Downloaded Notes Table

**Database:** `notesOfflineDB` via Dexie.

**Primary key:** `noteId`

## Fields

`noteId`, `subjectId`, `topicId`, `title`, `content`, `version`, `downloadedAt`, `sizeBytes`.

## Purpose

Persist explicitly downloaded Markdown notes for offline reading.

## Lifecycle

- Download inserts if not already present.
- Remove deletes by note ID.
- Update replaces content/version for an existing download.
- Downloads page lists all records.

## Migration

Dexie version 2 deletes the legacy `downloadedAttachments` store because PDF attachments were removed.

## Change Impact
Changing this table requires a Dexie migration strategy and affects [[Offline Module]], [[Downloads Screen]], offline reader, storage accounting, and local data compatibility.
