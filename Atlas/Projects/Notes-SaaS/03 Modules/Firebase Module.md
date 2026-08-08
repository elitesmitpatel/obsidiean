# Firebase Module

**Location:** `src/firebase/`

## Responsibility
Initialize Firebase app, Auth, and Firestore instances and optionally connect them to local emulators.

## Current products
- Firebase Authentication
- Cloud Firestore
- Firebase Hosting

## Removed
Firebase Storage is not part of the current application.

## Configuration
Required environment variables are defined in `docs/24-ENVIRONMENT.md` and `.env.example`. The API key is environment-provided and is not stored in this knowledge base.

## Change Impact
Changing Firebase configuration affects auth, Firestore, production hosting assumptions, emulator tests, and environment documentation.
