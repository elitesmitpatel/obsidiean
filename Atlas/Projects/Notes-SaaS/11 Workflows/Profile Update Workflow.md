# Profile Update Workflow

1. [[Profile Screen]] loads user document.
2. User enters a new display name.
3. Form trims input and prevents empty/unchanged saves.
4. `updateUserProfile` updates `displayName` + `updatedAt`.
5. Profile query is invalidated.

## Security
[[Profile Update Rule]].
