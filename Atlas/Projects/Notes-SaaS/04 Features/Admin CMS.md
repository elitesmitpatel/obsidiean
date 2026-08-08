# Admin CMS

## What it does
ADMIN-only create/update/list/archive-style status management for subjects, topics, and notes.

## APIs
Firestore through [[Services Module]].

## DB
[[Subjects Collection]], [[Topics Collection]], [[Notes Collection]]

## Screens
[[Admin Dashboard Screen]], [[Admin Subjects Screen]], [[Admin Topics Screen]], [[Admin Notes Screen]]

## Roles
[[ADMIN]] only.

## Derived behavior
- Note `searchableText` generated from Markdown content.
- Note version increments iff content changes.
- Content status controls student visibility.

## Change Impact
- [[Admin Module]]
- [[AdminRoute]]
- all three content collections
- Firestore rules
- Firestore indexes
- [[Search]]
- [[Notes Reader]]
- [[Offline Downloads]]
- admin query invalidation
- admin tests
