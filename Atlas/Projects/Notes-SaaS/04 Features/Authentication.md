# Authentication

## What it does
Supports email/password signup, login, logout, password reset, session restoration, and protected/public route behavior.

## APIs
[[Firebase Authentication Integration]].

## DB
[[Users Collection]] created on signup with `role = STUDENT`.

## Screens
[[Login Screen]], [[Signup Screen]], [[Forgot Password Screen]].

## Roles
All users begin as [[STUDENT]]. [[ADMIN]] is a role in the user document.

## Workflow
[[Signup Workflow]], [[Login Workflow]].

## Business rules
See [[Authentication Rules]].

## Change Impact
- [[Auth Module]]
- [[ProtectedRoute]]
- [[Router]]
- [[Users Collection]]
- [[Login Screen]]
- [[Signup Screen]]
- [[Forgot Password Screen]]
- Firestore user-creation rule
- Auth tests
- Production Firebase Auth configuration

### High-risk changes
Changing auth provider, session semantics, or user-role creation can lock users out or break authorization.
