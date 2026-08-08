# Topics Collection

**Path:** `topics/{topicId}`

## Fields

`id`, `subjectId`, `title`, `slug`, optional `description`, `orderIndex`, `isActive`, `createdAt`, `updatedAt`.

## Read patterns

- Active student list by subject: `subjectId + isActive + orderIndex`.
- Admin list by subject: `subjectId + orderIndex`.
- Direct lookup.

## Relationships

Each topic belongs to one subject and is referenced by notes.

## Indexes

- `topics(subjectId ASC, isActive ASC, orderIndex ASC)`
- `topics(subjectId ASC, orderIndex ASC)`

## Change Impact
Changing `subjectId` or `orderIndex` affects hierarchy/navigation and query indexes. Changing active state affects student visibility.
