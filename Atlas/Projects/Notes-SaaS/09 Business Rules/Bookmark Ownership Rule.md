# Bookmark Ownership Rule

A bookmark's `userId` must match `request.auth.uid` for owner operations. Bookmark IDs are deterministic `${userId}_${noteId}`.
