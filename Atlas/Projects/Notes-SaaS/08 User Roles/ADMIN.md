# ADMIN

## Capabilities

Everything a [[STUDENT]] can do, plus:

- Access `/admin/*`.
- Create/update subjects.
- Activate/archive subjects.
- Create/update topics.
- Activate/archive topics.
- Create/update notes.
- Change note status.
- Restore archived notes through the admin status workflow.

## Authorization source

`users/{uid}.role == ADMIN` in Firestore rules and `AdminRoute`.

## Important

Client UI is not the authoritative security boundary; Firestore rules are.
