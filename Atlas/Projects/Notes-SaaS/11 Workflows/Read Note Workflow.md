# Read Note Workflow

1. `/note/:noteId` is protected.
2. [[Note Reader Screen]] calls `useNote`.
3. [[Offline Module]] also checks local Dexie content.
4. If local content exists, it can be displayed offline.
5. Markdown is rendered by [[Notes Module]].
6. User may bookmark or download.

## Change hotspots
[[Notes Collection]], note versioning, offline schema, Markdown renderer.
