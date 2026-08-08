# Profile Module

**Location:** `src/features/profile/`

## Responsibility
Read a user's Firestore profile and update display name.

## Data
[[Users Collection]]

## Service
`userService.getUserProfile`, `updateUserProfile`.

## UI
[[Profile Screen]], [[Profile Card]], [[Profile Form]].

## Security
Firestore rules restrict users to their own profile updates and allow only `displayName` + `updatedAt`.

## Change Impact
Changing profile fields affects auth-created user documents, profile UI, admin authorization when `role` is involved, Firestore rules, and profile tests. Never allow client-side role editing.
