# Notes Reader

## What it does
Displays published Markdown notes, tags, updated date, bookmark state, and offline/download controls.

## APIs
Firestore `notes` via `getPublishedNoteById`; IndexedDB via [[Offline Module]] when locally available.

## DB
[[Notes Collection]], [[Downloaded Notes Table]], [[Bookmarks Collection]]

## Screens
[[Note Reader Screen]]

## Roles
Authenticated users; ADMIN authors content through [[Admin CMS]].

## Change Impact
- [[Notes Module]]
- [[Offline Module]]
- [[Bookmarks Module]]
- [[Search Module]]
- [[Admin Module]]
- Markdown rendering dependencies
- note Firestore queries/indexes
- note versioning
- reader tests
