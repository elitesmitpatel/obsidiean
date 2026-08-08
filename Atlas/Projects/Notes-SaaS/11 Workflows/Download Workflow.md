# Download Workflow

1. User opens [[Note Reader Screen]] online.
2. `useDownloadNote` receives the published `NoteDocument`.
3. `downloadNote` checks Dexie for an existing record.
4. If absent, content/version/metadata are stored in [[Downloaded Notes Table]].
5. Query caches are invalidated.
6. `/downloads` lists the local record.

## No file storage
Only Markdown note content is persisted locally.
