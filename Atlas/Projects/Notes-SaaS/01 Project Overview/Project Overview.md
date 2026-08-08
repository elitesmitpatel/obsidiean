# Project Overview

## Purpose

Notes SaaS is an authenticated notes application with hierarchical content browsing, Markdown reading, bookmarks, search, offline downloads, profile management, and an ADMIN content-management surface.

## Current product boundary

- Authentication: email/password only.
- Content hierarchy: Subject → Topic → Note.
- Notes are Markdown/text only.
- Firebase Storage/PDF attachments are removed from the MVP.
- Cloudinary is not used.
- Offline downloads are stored locally in IndexedDB.
- Production hosting is Firebase Hosting.

## Roles

- [[STUDENT]] — normal authenticated content consumer.
- [[ADMIN]] — authenticated user with `users/{uid}.role = ADMIN`; can manage subjects, topics, and notes.

## Technology

See [[Technology Stack]] and [[Dependencies]].

## Phase history

- Foundation / data/security
- Authentication
- Subjects
- Application shell
- Topics
- Notes + reader
- Bookmarks
- Search
- Offline engine
- Profile
- Admin CMS
- Security hardening
- Production deployment
- `/downloads` routing remediation

The repository's authoritative roadmap ends at Phase 13; the `/downloads` work closed a remaining Phase 9 routing contract gap rather than creating a Phase 14.

## Production

Production Firebase project: `notes-oo`.

Production Hosting URL: https://notes-oo.web.app

No credentials are stored in this knowledge base.
