# Browse Notes Workflow

1. Authenticated user enters [[Home Screen]].
2. `useActiveSubjects` queries active subjects.
3. User selects a subject.
4. [[Subject Screen]] loads active topics for `subjectId`.
5. User selects a topic.
6. [[Topic Screen]] loads published notes for `topicId`.
7. User selects a note.
8. [[Note Reader Screen]] loads the published note.

## Data
[[Subjects Collection]] → [[Topics Collection]] → [[Notes Collection]].
