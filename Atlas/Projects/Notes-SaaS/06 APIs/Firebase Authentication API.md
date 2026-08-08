# Firebase Authentication API

## Operations

- `createUserWithEmailAndPassword`
- `signInWithEmailAndPassword`
- `signOut`
- `sendPasswordResetEmail`
- `onAuthStateChanged`

## Used by

[[Auth Module]]

## Side effects

Signup also creates `users/{uid}` in Firestore.

## Change Impact

Provider/operation changes affect authentication screens, session restoration, route guards, production Firebase configuration, and auth tests.
