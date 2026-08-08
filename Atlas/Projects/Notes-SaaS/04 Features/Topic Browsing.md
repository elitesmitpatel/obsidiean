# Topic Browsing

## What it does
Shows active topics for a subject ordered by `orderIndex` and links to `/topic/:topicId`.

## APIs
Firestore `topics` query via `topicService.getActiveTopicsBySubject`.

## DB
[[Topics Collection]]

## Screens
[[Subject Screen]], [[Topic Screen]]

## Change Impact
- [[Topics Module]]
- [[Subject Screen]]
- [[Topic Screen]]
- [[Notes Module]]
- topic composite index
- Firestore read rules
- topic tests
