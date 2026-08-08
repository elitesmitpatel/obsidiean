# Bookmarks Collection

**Path:** `bookmarks/{bookmarkId}`

## Fields

`id`, `userId`, `noteId`, `createdAt`.

## Identity

Bookmark ID is deterministic: `${userId}_${noteId}`.

## Operations

- Query by `userId`.
- Create with owner userId.
- Delete by bookmark ID.
- No update operation.

## Security

Ownership is enforced in Firestore rules.

## Change Impact
Changing ID strategy or ownership fields affects bookmark toggling, queries, rules, and UI state.
