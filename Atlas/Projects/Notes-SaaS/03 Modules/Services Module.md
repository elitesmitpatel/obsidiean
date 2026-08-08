# Services Module

**Location:** `src/services/`

## Responsibility
Central Firestore data-access boundary.

## Services
- `firestore.ts`
- `userService.ts`
- `subjectService.ts`
- `topicService.ts`
- `noteService.ts`
- `bookmarkService.ts`
- `searchableText.ts`

## Collections
[[Users Collection]], [[Subjects Collection]], [[Topics Collection]], [[Notes Collection]], [[Bookmarks Collection]].

## Change Impact
Service contracts are high fan-out points. Changing function signatures, query constraints, payload fields, or return types affects hooks, pages/components, tests, indexes, and security assumptions.
