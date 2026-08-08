# Login Workflow

1. [[Login Screen]] submits credentials.
2. `AuthContext` calls auth service.
3. Firebase Auth validates credentials.
4. `onAuthStateChanged` updates context.
5. [[PublicOnlyRoute]] redirects to intended path or `/home`.

## Failure points
Invalid credentials, disabled user, network/auth provider errors.
