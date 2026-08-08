# State Ownership

| State | Owner | Example |
|---|---|---|
| Auth session | React Context | `AuthProvider` |
| Firestore/server state | TanStack Query | `useActiveSubjects` |
| Form-local state | React component | Admin forms |
| Offline persisted content | Dexie/IndexedDB | `downloadedNotes` |
| URL state | React Router | `subjectId`, `topicId`, `noteId` |

Changing state ownership can ripple through hooks, components, tests, and invalidation behavior. See [[Change Impact Index]].
