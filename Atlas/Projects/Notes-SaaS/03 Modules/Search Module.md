# Search Module

**Location:** `src/features/search/`

## Responsibility
Search cached published notes by title, tags, and derived searchable text.

## Behavior
- Fetches published notes once through TanStack Query.
- 300 ms input debounce.
- Trims and lowercases query.
- Empty query returns all loaded published notes.
- Filtering is client-side.

## Data
[[Notes Collection]], especially `title`, `tags`, `searchableText`.

## UI
[[Search Screen]], [[Search Result Card]].

## Change Impact
Changing `searchableText` derivation affects search recall and admin note writes. Changing query keys affects cache reuse/invalidation. Changing note fields affects search filters. Changing debounce behavior affects UX and tests.
