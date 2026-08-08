# Note Change Impact

Changing notes is the highest-risk content change.

## Directly affected

- [[Notes Module]]
- [[Notes Collection]]
- [[Note Reader Screen]]
- [[Topic Screen]]
- [[Admin Notes Screen]]
- [[Admin Note Form]]

## Indirectly affected

- [[Search Module]] via `searchableText`
- [[Bookmarks Module]] because bookmarks point to `noteId`
- [[Offline Module]] because downloaded records mirror note content/version
- [[Downloads Screen]]
- Firestore composite indexes
- Firestore rules
- note tests

## If `content` changes

- `searchableText` changes
- `version` increments
- existing offline downloads may show update available

## If `title/tags/orderIndex/status` changes

- `version` does not increment
- search/reader/admin listing may change depending on field
- status can change visibility

## If IDs/relationships change

Expect broad hierarchy and routing impacts.
