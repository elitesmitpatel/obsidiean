# Profile

## What it does
Displays email, display name, role, membership date and allows display-name editing.

## APIs
Firestore user document via [[Profile Module]].

## DB
[[Users Collection]]

## Screens
[[Profile Screen]], [[Profile Card]], [[Profile Form]]

## Change Impact
- [[Profile Module]]
- [[Users Collection]]
- Firestore profile update rule
- [[AdminRoute]] because role is read from profile
- profile tests
