# Search

## What it does
Searches published notes by title, tags, and `searchableText`.

## APIs
One Firestore published-notes read followed by client-side filtering.

## DB
[[Notes Collection]]

## Screens
[[Search Screen]], [[Search Result Card]]

## Rules
Query is normalized by trim + lowercase; input is debounced 300 ms.

## Change Impact
- [[Search Module]]
- [[Notes Module]]
- `searchableText` derivation
- Admin note mutation invalidation
- Search screen/result tests
- Query cache key
