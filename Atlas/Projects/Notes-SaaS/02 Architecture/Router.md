# Router

Source: `src/app/router.tsx`.

## Routes

### Protected

- `/`
- `/home`
- `/subject/:subjectId`
- `/topic/:topicId`
- `/note/:noteId`
- `/search`
- `/bookmarks`
- `/profile`
- `/downloads`

### Admin

- `/admin`
- `/admin/subjects`
- `/admin/subjects/new`
- `/admin/subjects/:subjectId/edit`
- `/admin/topics`
- `/admin/topics/new`
- `/admin/topics/:topicId/edit`
- `/admin/notes`
- `/admin/notes/new`
- `/admin/notes/:noteId/edit`

### Public

- `/login`
- `/signup`
- `/forgot-password`

### Fallback

- `*` → NotFoundPage

## Routing dependencies

[[App Shell Module]], [[Auth Module]], [[Admin Module]], [[Firebase Hosting]].

## Change impact

Route changes affect page imports, protected/admin guards, navigation links, direct-link behavior, Hosting SPA rewrites, and routing tests.
