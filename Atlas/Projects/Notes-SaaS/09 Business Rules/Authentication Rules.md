# Authentication Rules

- Email/password only.
- Signup creates a Firestore user document with `role = STUDENT`.
- Firebase Auth session is restored with `onAuthStateChanged`.
- Public-only routes redirect authenticated users.
- Protected routes redirect unauthenticated users.
