# Downloads Screen

## What it does
Lists all locally downloaded notes, total count, total storage, navigation to note reader, and remove actions.

## Data
[[Downloaded Notes Table]]

## APIs
`useDownloadedNotes` → `getAllDownloadedNotes`; `useRemoveDownload` → `removeDownload`.

## Route
`/downloads`, protected by [[ProtectedRoute]].

## Change Impact
- [[Offline Module]]
- [[Database Module]]
- [[Router]]
- [[Downloads Screen]]
- downloaded-note list tests
