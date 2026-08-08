# Bookmarks Module

**Location:** `src/features/bookmarks/`

## Responsibility
Create/delete user-owned note bookmarks and display bookmarked published notes.

## Data
[[Bookmarks Collection]] plus [[Notes Collection]].

## Services
`bookmarkService.getUserBookmarks`, `addBookmark`, `deleteBookmark`.

## UI
[[Bookmarks Screen]], [[Note Reader Screen]] via [[BookmarkButton]].

## Change Impact
Changing bookmark identity or ownership affects Firestore rules, bookmark queries, toggle mutations, bookmark page, and reader state. Changing note availability affects whether bookmarked notes can still render.
