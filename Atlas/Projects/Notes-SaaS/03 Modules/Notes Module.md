# Notes Module

**Location:** `src/features/notes/`

## Responsibility
List published notes and render a Markdown note reader.

## Data
[[Notes Collection]]

## Services
- `getPublishedNotesByTopic`
- `getPublishedNoteById`
- admin CRUD methods in `noteService`

## UI
[[Topic Screen]], [[Note Reader Screen]]

## Cross-cutting
Notes also feed [[Search Module]], [[Bookmarks Module]], [[Offline Module]], and [[Admin Module]].

## Change Impact
This is a high-impact module. Changing `NoteDocument` fields, publication status, content, ordering, or versioning can affect reader rendering, search, bookmarks, offline storage/update detection, admin forms, Firestore indexes/rules, and many tests.
