# Subject Browsing

## What it does
Shows active subjects ordered by `orderIndex` and links to `/subject/:subjectId`.

## APIs
Firestore `subjects` query via `subjectService.getActiveSubjects`.

## DB
[[Subjects Collection]]

## Screens
[[Home Screen]], [[Subject Screen]].

## Roles
Authenticated users.

## Workflow
[[Browse Notes Workflow]]

## Change Impact
- [[Subjects Module]]
- [[Home Screen]]
- [[Subject Screen]]
- [[Topics Module]]
- `subjects(isActive, orderIndex)` index
- subject service tests
- Firestore read rules
