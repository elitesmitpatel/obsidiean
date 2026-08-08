# Bookmarks

## What it does
Creates/deletes a deterministic user-note bookmark and displays bookmarked published notes.

## APIs
Firestore [[Bookmarks Collection]] and published note reads.

## DB
[[Bookmarks Collection]], [[Notes Collection]]

## Screens
[[Bookmarks Screen]], [[Note Reader Screen]]

## Roles
Authenticated users; ownership enforced by `userId`.

## Change Impact
- [[Bookmarks Module]]
- [[Bookmark Workflow]]
- Firestore bookmark rules
- bookmark document ID convention
- note availability behavior
- reader/bookmarks screens
