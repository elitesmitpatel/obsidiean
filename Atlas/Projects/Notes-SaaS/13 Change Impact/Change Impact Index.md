# Change Impact Index

Use this note before changing any cross-cutting feature.

| Change | Primary impact |
|---|---|
| Auth/session | Auth Context, route guards, login/signup, user docs |
| User role | AdminRoute, Firestore rules, admin access |
| Subject schema/query | Subject UI, topics, admin, indexes |
| Topic schema/query | Subject/topic UI, notes, admin, indexes |
| Note schema/content | Reader, search, bookmarks, offline, admin, indexes |
| Note version | Offline update detection and downloaded records |
| Searchable text | Search results + admin note writes |
| Bookmark identity | Reader, bookmarks page, rules |
| Dexie schema | Offline service, migrations, reader, downloads |
| Route | Router, pages, navigation, Hosting rewrites |
| App shell | Every protected screen |
| PWA build | Hosting, service worker, installability |
| Firebase config | Auth, Firestore, emulator/prod behavior |

## Required process

1. Identify affected [[Modules]].
2. Check affected [[Database Overview]] entities.
3. Check [[Service API Catalog]].
4. Check affected [[UI Screens]].
5. Check [[Business Rules]].
6. Update tests.
7. Verify indexes/rules if query/security semantics change.
8. Verify production behavior for infrastructure changes.
