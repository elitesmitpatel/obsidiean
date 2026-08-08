# Security Architecture

## Firestore

Authorization is enforced by `firestore.rules`, not only by UI guards.

Key rules:

- Authenticated users can read permitted content.
- A user can create their own `users/{uid}` document with `role = STUDENT`.
- Users can update only `displayName` and `updatedAt` on their own profile.
- ADMIN status is read from the user document by the rules.
- Subjects/topics/notes writes require ADMIN.
- Bookmarks are owner-bound by `userId`.
- Client deletes are denied for content collections.
- Deny-by-default catch-all remains active.

## UI guards

- [[ProtectedRoute]] prevents unauthenticated navigation.
- [[AdminRoute]] prevents non-admin UI access.

UI guards are convenience controls; Firestore rules remain authoritative.

## Attachment boundary

Firebase Storage and PDF attachments were removed. See [[Attachment Removal Decision]].
