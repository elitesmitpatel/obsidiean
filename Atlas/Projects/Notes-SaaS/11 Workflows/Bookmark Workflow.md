# Bookmark Workflow

1. Reader determines whether note ID exists in user bookmarks.
2. [[BookmarkButton]] calls bookmark mutation.
3. `addBookmark` writes deterministic `userId_noteId`.
4. Query invalidation refreshes bookmark state.
5. Delete removes the bookmark document.

## Security
[[Bookmark Ownership Rule]] is enforced by Firestore rules.
