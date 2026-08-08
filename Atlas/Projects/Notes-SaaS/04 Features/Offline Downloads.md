# Offline Downloads

## What it does
Stores Markdown note content locally for offline reading and reports whether a newer remote version exists.

## APIs
IndexedDB/Dexie; Firestore only as fallback in [[Offline Reader Workflow]].

## DB
[[Downloaded Notes Table]]

## Screens
[[Note Reader Screen]], [[Downloads Screen]]

## Version rule
Version changes when note `content` changes.

## Change Impact
- [[Offline Module]]
- [[Database Module]]
- Dexie schema/migrations
- note `version`
- reader/offline badge
- downloads list
- storage-size calculations
