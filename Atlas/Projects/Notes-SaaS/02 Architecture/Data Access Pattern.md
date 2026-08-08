# Data Access Pattern

## Firestore

`Page/Component → Hook → Service → Firestore`

Examples:

- [[Subjects Module]] → `useActiveSubjects` → `subjectService.getActiveSubjects`
- [[Topics Module]] → `useActiveTopics` → `topicService.getActiveTopicsBySubject`
- [[Notes Module]] → `usePublishedNotes` / `useNote` → `noteService`
- [[Bookmarks Module]] → bookmark hooks → `bookmarkService`
- [[Profile Module]] → profile hooks → `userService`
- [[Admin Module]] → admin hooks → subject/topic/note services

## Offline

`Page/Component → Offline Hook → offlineService → Dexie`

## Why this matters

Changing a service contract propagates upward to hooks, then components/pages, and usually tests. See [[Change Impact Index]].
