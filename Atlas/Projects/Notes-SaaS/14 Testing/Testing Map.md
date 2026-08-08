# Testing Map

| Area | Representative tests |
|---|---|
| Auth | `src/features/auth/__tests__/` |
| Subjects | `src/features/subjects/**/__tests__/` |
| Topics | `src/features/topics/**/__tests__/` |
| Notes | `src/features/notes/**/__tests__/` |
| Bookmarks | `src/features/bookmarks/**/__tests__/` |
| Search | `src/features/search/**/__tests__/` |
| Offline | `src/features/offline/**/__tests__/` |
| Profile | `src/features/profile/**/__tests__/` |
| Admin | `src/features/admin/**/__tests__/` |
| Firebase | `src/firebase/index.test.ts` |
| DB | `src/db/index.test.ts` |

## Test discipline

No snapshots are needed for architectural verification. Tests should verify behavior, not merely render trees.
