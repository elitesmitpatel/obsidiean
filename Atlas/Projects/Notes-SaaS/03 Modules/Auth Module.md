# Auth Module

**Location:** `src/features/auth/`

## Responsibility
Own Firebase Authentication operations, auth session state, user document creation, error mapping, and public/protected route guards.

## Files
- `auth-service.ts`
- `auth-context.tsx`
- `protected-route.tsx`
- `index.ts`

## APIs
- Firebase Auth: `createUserWithEmailAndPassword`
- `signInWithEmailAndPassword`
- `signOut`
- `sendPasswordResetEmail`
- `onAuthStateChanged`
- Firestore `setDoc` for user document creation

## DB
[[Users Collection]]

## Screens
[[Login Screen]], [[Signup Screen]], [[Forgot Password Screen]], [[Home Screen]]

## Roles
[[STUDENT]], [[ADMIN]]

## Change Impact
Changing auth state shape affects [[ProtectedRoute]], [[PublicOnlyRoute]], pages using `useAuth`, and route tests. Changing signup user-document fields affects [[Users Collection]] and Firestore rules. Changing Firebase provider configuration affects [[Firebase Authentication Integration]] and production configuration.
