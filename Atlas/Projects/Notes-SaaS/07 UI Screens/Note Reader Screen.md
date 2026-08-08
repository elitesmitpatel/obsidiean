# Note Reader Screen

Route: `/note/:noteId`.

Guard: [[ProtectedRoute]].

Displays Markdown, tags, updated date, bookmark control, download control, and offline state.

Data sources: Firestore + [[Downloaded Notes Table]].

Change Impact: [[Notes Module]], [[Bookmarks Module]], [[Offline Module]], Markdown rendering, note schema.
