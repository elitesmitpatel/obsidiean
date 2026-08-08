# Users Collection

**Path:** `users/{uid}`

## Fields

| Field | Type | Meaning |
|---|---|---|
| `uid` | string | Firebase Auth UID |
| `email` | string | Account email |
| `displayName` | string | User-facing name |
| `role` | `STUDENT \| ADMIN` | Authorization role |
| `createdAt` | Timestamp | Creation time |
| `updatedAt` | Timestamp | Last profile update |

## Writes

- Signup creates/merges the user's own document with `role = STUDENT`.
- Profile updates can change `displayName` and `updatedAt`.

## Consumers

[[Auth Module]], [[Profile Module]], [[Admin Module]].

## Security

Users can read authenticated profiles; users can only update their own profile and only permitted fields. Role escalation is prevented by rules.

## Change Impact
Changing `role` affects [[AdminRoute]] and Firestore admin authorization. Changing profile fields affects auth creation, profile UI, and rules.
