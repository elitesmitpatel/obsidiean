# Signup Workflow

1. [[Signup Screen]] collects display name/email/password.
2. [[Auth Module]] calls Firebase `createUserWithEmailAndPassword`.
3. `createUserDocument` writes `users/{uid}` with `role = STUDENT`.
4. Auth state is observed by `AuthProvider`.
5. Protected routes become available.

## Affected systems
[[Firebase Authentication Integration]], [[Users Collection]], [[ProtectedRoute]].

## Failure point
Auth user can exist without Firestore user document if the post-signup Firestore write fails.
