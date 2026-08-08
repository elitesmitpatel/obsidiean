# Notes Collection

**Path:** `notes/{noteId}`

## Fields

| Field | Type | Meaning |
|---|---|---|
| `id` | string | Note ID |
| `subjectId` | string | Parent subject |
| `topicId` | string | Parent topic |
| `title` | string | Display title |
| `slug` | string | Slug |
| `content` | string | Markdown content |
| `searchableText` | string | Derived plain searchable representation |
| `tags` | string[] | Search/display tags |
| `version` | number | Offline content version |
| `orderIndex` | number | Topic ordering |
| `status` | `DRAFT \| PUBLISHED \| ARCHIVED` | Publication state |
| `createdAt` | Timestamp | Creation time |
| `updatedAt` | Timestamp | Last update |

## Read patterns

- Published topic list: `topicId + status + orderIndex`.
- Published by ID: direct lookup + status check.
- Search seed: all published notes.
- Admin list: `subjectId + orderIndex`.
- Admin direct lookup.

## Indexes

- `notes(topicId ASC, status ASC, orderIndex ASC)`
- `notes(subjectId ASC, orderIndex ASC)`

A stale production `notes(topicId,status)` index is intentionally retained and is not part of the current configuration.

## Version rule

`version` increments iff `content` changes. Metadata-only edits do not increment it.

## Search rule

`searchableText` is derived from Markdown content by [[Searchable Text Derivation]].

## Change Impact
This is the highest-impact data model. Changes affect reader, search, bookmarks, offline storage, admin forms, indexes, services, rules, and tests.
