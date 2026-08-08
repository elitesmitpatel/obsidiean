# Topics Module

**Location:** `src/features/topics/`

## Responsibility
List active topics within a subject and navigate to a topic's notes.

## Data
[[Topics Collection]]

## Service
`topicService.getActiveTopicsBySubject()` filters `subjectId`, `isActive`, and orders by `orderIndex ASC`.

## UI
[[Subject Screen]], [[Topic Screen]]

## Change Impact
Changing topic fields affects subject navigation, note relationships, admin forms, Firestore indexes, and topic listing tests. Changing ordering/query constraints affects composite indexes.
