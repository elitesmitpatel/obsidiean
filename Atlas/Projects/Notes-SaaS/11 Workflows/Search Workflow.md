# Search Workflow

1. [[Search Screen]] captures query.
2. [[Search Module]] debounces 300 ms.
3. TanStack Query loads published notes once.
4. Query is trimmed/lowercased.
5. Client filters title, tags, and searchableText.
6. Results link to `/note/:noteId`.

## Important
No Firestore query is issued per keystroke.
