
# NOTES — SOFTWARE REQUIREMENTS SPECIFICATION

## AI-Assisted Development Specification

Version: MVP 1.0  
Status: Development Baseline

---

# 00. DOCUMENT AUTHORITY

This repository is the source of truth for the Notes project.

When requirements conflict, follow this priority:

1. `00-PROJECT-CONSTITUTION.md`
    
2. `07-DATABASE-SCHEMA.md`
    
3. `14-SECURITY.md`
    
4. `09-TECH-STACK.md`
    
5. `11-ROUTING.md`
    
6. `04-FUNCTIONAL-REQUIREMENTS.md`
    
7. Feature-specific documentation
    
8. Existing implementation
    
9. AI assumptions
    

If documentation conflicts with existing code, STOP and report the conflict.

Do not silently choose one.

Never invent:

- database fields
    
- routes
    
- dependencies
    
- Firebase collections
    
- roles
    
- environment variables
    
- business rules
    

If required information is missing, STOP and ask.

---

# 01. PROJECT OVERVIEW

## Product Name

Notes

## Product Type

Mobile-first Progressive Web Application.

## Purpose

Provide students with structured syllabus-based study notes so they can study from one organized platform instead of collecting material from multiple books and sources.

## Core Hierarchy

Subject  
→ Topic  
→ Note

Architecture must allow Course/Semester layers to be added later without rewriting the entire application.

## MVP Users

### Student

Can:

- Register
    
- Login
    
- Browse subjects
    
- Browse topics
    
- Read notes
    
- Search notes
    
- Bookmark notes
    
- Download notes
    
- Read downloaded notes offline
    
- Manage profile
    

### Admin

Can:

- Create/edit/archive subjects
    
- Create/edit topics
    
- Create/edit/archive notes
    
- Manage content
    

Admin functionality exists inside the same application under protected `/admin/*` routes.

---

# 02. MVP SCOPE

## Included

Authentication

Subject browsing

Topic browsing

Notes

Search

Bookmarks

Offline downloads

PWA installation

Profile

Minimal admin CMS

Responsive design

Security rules

Error handling

Testing

Deployment

---

# 03. OUT OF SCOPE

Do NOT implement unless requirements are explicitly changed.

- Payments
    
- Subscriptions
    
- AI tutor
    
- Flashcards
    
- Quiz generation
    
- Comments
    
- Ratings
    
- Social features
    
- Push notifications
    
- Cloud Functions
    
- Dedicated backend server
    
- Redux
    
- Zustand
    
- Algolia
    
- Typesense
    
- Elasticsearch
    
- Social authentication
    

---

# 04. FUNCTIONAL REQUIREMENTS

## FR-AUTH-001 Signup

Student can create an account using:

- email
    
- password
    
- display name
    

Firebase Authentication creates the identity.

A corresponding Firestore user document must be created.

---

## FR-AUTH-002 Login

Registered users can login using email/password.

---

## FR-AUTH-003 Logout

Authenticated users can securely terminate their session.

---

## FR-AUTH-004 Protected Routes

Unauthenticated users cannot access protected student or admin routes.

---

## FR-BROWSE-001 Subjects

Authenticated users can view active subjects ordered by `orderIndex`.

---

## FR-BROWSE-002 Topics

Users can open a subject and view its topics ordered by `orderIndex`.

---

## FR-NOTE-001 Notes

Users can open a topic and view published notes.

---

## FR-NOTE-002 Reader

Primary note format:

Markdown.

Notes may additionally contain optional downloadable attachments.

---

## FR-SEARCH-001 Search

MVP search supports:

- note title
    
- tags
    
- searchable text content
    

Search is client-side for MVP.

Dedicated full-text search infrastructure is NOT part of MVP.

---

## FR-BOOKMARK-001 Bookmark

Authenticated users can:

- add bookmark
    
- remove bookmark
    
- view bookmarks
    

Bookmarks belong to a specific Firebase UID.

---

## FR-OFFLINE-001 Download

Users can explicitly download supported notes for offline reading.

Downloaded content is stored in IndexedDB.

---

## FR-OFFLINE-002 Offline Reader

When opening a downloaded note:

1. Check local IndexedDB.
    
2. Determine whether network content/version is available.
    
3. Use current remote version when available.
    
4. Fall back to downloaded content when remote access fails.
    
5. Never block reading solely because the browser reports offline status.
    

---

# 05. NON-FUNCTIONAL REQUIREMENTS

## Performance

Target:

- fast mobile interaction
    
- route-level code splitting
    
- lazy loading where appropriate
    
- avoid unnecessary Firestore reads
    

## Accessibility

Use:

- semantic HTML
    
- keyboard navigation
    
- accessible form labels
    
- ARIA attributes when required
    
- sufficient contrast
    

## Reliability

Every async feature must support:

- Loading
    
- Success
    
- Empty
    
- Error
    

Offline-capable features additionally require:

- Offline
    
- Stale/update-available state where relevant
    

---

# 06. USER FLOW

Unauthenticated:

Landing  
→ Login / Signup

Authenticated:

Home  
→ Subject  
→ Topic  
→ Note

From Note:

→ Bookmark

or

→ Download

or

→ Offline Reading

Admin:

Login  
→ Admin Dashboard  
→ Subjects / Topics / Notes  
→ Create / Edit / Archive

---

# 07. DATABASE SCHEMA

THIS FILE IS AUTHORITATIVE.

Do not create fields not defined here without approval.

---

## users/{uid}

```ts
interface UserDocument {
  uid: string;
  email: string;
  displayName: string;
  role: 'STUDENT' | 'ADMIN';
  createdAt: Timestamp;
  updatedAt: Timestamp;
}
```

Document ID MUST equal Firebase Authentication UID.

---

## subjects/{subjectId}

```ts
interface SubjectDocument {
  id: string;
  name: string;
  slug: string;
  description: string;
  iconUrl?: string;
  orderIndex: number;
  isActive: boolean;
  createdAt: Timestamp;
  updatedAt: Timestamp;
}
```

---

## topics/{topicId}

```ts
interface TopicDocument {
  id: string;
  subjectId: string;
  title: string;
  slug: string;
  description?: string;
  orderIndex: number;
  isActive: boolean;
  createdAt: Timestamp;
  updatedAt: Timestamp;
}
```

---

## notes/{noteId}

```ts
interface NoteDocument {
  id: string;

  subjectId: string;
  topicId: string;

  title: string;
  slug: string;

  content: string;

  searchableText: string;

  tags: string[];

  attachmentPath?: string;
  attachmentType?: 'PDF';

  version: number;

  orderIndex: number;

  status: 'DRAFT' | 'PUBLISHED' | 'ARCHIVED';

  createdAt: Timestamp;
  updatedAt: Timestamp;
}
```

`subjectId` is intentionally denormalized.

Firestore does not support relational joins.

`version` MUST increase whenever downloadable note content changes.

---

## bookmarks/{bookmarkId}

```ts
interface BookmarkDocument {
  id: string;
  userId: string;
  noteId: string;
  createdAt: Timestamp;
}
```

Recommended deterministic document ID:

`{uid}_{noteId}`

This prevents duplicate bookmarks.

---

# 08. INDEXEDDB SCHEMA

Library:

Dexie.js

Database:

`notesOfflineDB`

---

## downloadedNotes

```ts
interface DownloadedNote {
  noteId: string;

  subjectId: string;
  topicId: string;

  title: string;

  content: string;

  version: number;

  downloadedAt: number;

  sizeBytes: number;
}
```

Primary key:

`noteId`

---

## downloadedAttachments

Only required when a note has an attachment.

```ts
interface DownloadedAttachment {
  noteId: string;
  blob: Blob;
  mimeType: string;
  version: number;
  downloadedAt: number;
}
```

---

# 09. TECH STACK

The stack is locked for MVP.

## Frontend

React

Vite

TypeScript

---

## Styling

Tailwind CSS

shadcn/ui

Lucide React

---

## Routing

React Router

---

## Authentication

Firebase Authentication

Email/password only.

---

## Database

Firebase Firestore

---

## File Storage

Firebase Storage

---

## Server State

TanStack Query

Responsibilities:

- Firestore query state
    
- caching
    
- loading/error handling
    
- invalidation
    

---

## Auth State

React Context.

React Context must only contain authentication/session information.

---

## Local UI State

React component state.

Do NOT introduce Redux or Zustand.

---

## Offline Content

Dexie.js / IndexedDB.

---

## PWA

vite-plugin-pwa

---

## Hosting

Firebase Hosting.

---

# 10. STATE OWNERSHIP

This section exists to prevent multiple competing state systems.

Firebase Auth:

Authentication identity.

React AuthContext:

Current authentication/session representation.

TanStack Query:

Remote Firestore data.

Dexie:

Explicitly downloaded offline content.

Component state:

Temporary UI state.

URL:

Navigation/filter state where appropriate.

Never duplicate the same state across multiple systems without a documented reason.

---

# 11. ROUTING

## Public

`/`

`/login`

`/signup`

`/forgot-password`

---

## Student Protected

`/home`

`/subject/:subjectId`

`/topic/:topicId`

`/note/:noteId`

`/search`

`/bookmarks`

`/profile`

`/downloads`

---

## Admin Protected

`/admin`

`/admin/subjects`

`/admin/subjects/new`

`/admin/subjects/:subjectId/edit`

`/admin/topics`

`/admin/topics/new`

`/admin/topics/:topicId/edit`

`/admin/notes`

`/admin/notes/new`

`/admin/notes/:noteId/edit`

---

## Guards

`PublicOnlyRoute`

`ProtectedRoute`

`AdminRoute`

Admin authorization MUST NOT rely only on hiding UI.

Firestore Security Rules remain authoritative.

---

# 12. DATA ACCESS ARCHITECTURE

UI components MUST NOT directly call Firestore.

Required flow:

Component  
↓  
Feature Hook  
↓  
TanStack Query  
↓  
Service  
↓  
Firebase SDK  
↓  
Firestore

Example:

`SubjectList`

↓

`useSubjects()`

↓

`subjectService.getActiveSubjects()`

↓

Firestore

This separation is mandatory.

---

# 13. FIREBASE CONFIGURATION

Required Firebase products:

- Authentication
    
- Firestore
    
- Storage
    
- Hosting
    

Do not enable Cloud Functions for MVP.

Required repository files:

`firebase.json`

`firestore.rules`

`firestore.indexes.json`

`storage.rules`

`.firebaserc`

---

# 14. SECURITY MODEL

Security Rules are mandatory before production data is added.

## Default Principle

Deny by default.

Grant only explicitly required access.

---

## Users

Users may read/update only permitted profile fields on their own user document.

Users must NEVER be able to promote themselves to ADMIN.

Client-side updates to `role` must be rejected.

---

## Subjects / Topics / Notes

Authenticated users:

READ published/active educational content.

Admins:

CREATE/UPDATE/ARCHIVE content.

Student writes to educational content are forbidden.

---

## Bookmarks

A user can only:

create

read

delete

their own bookmarks.

A user cannot access another user's bookmarks.

---

## Admin Authorization

Admin access must be enforced by:

Firestore Security Rules

AND

UI route guard.

UI guards are convenience only.

Security Rules are authoritative.

---

# 15. FIRESTORE INDEXES

Create required indexes as queries are introduced.

Do not create arbitrary indexes.

Expected query patterns include:

Topics:

subjectId + isActive + orderIndex

Notes:

topicId + status + orderIndex

Notes:

subjectId + status

Bookmarks:

userId + createdAt

All required indexes must be committed in:

`firestore.indexes.json`

---

# 16. OFFLINE ARCHITECTURE

There are TWO different offline mechanisms.

Do not mix them.

## Layer A — Firestore Persistence

Used for:

- subject metadata
    
- topic metadata
    
- remote query caching where supported
    

This is NOT the explicit note download system.

---

## Layer B — Dexie / IndexedDB

Used for:

- downloaded Markdown content
    
- downloaded attachments
    
- offline note metadata
    
- note version
    

Explicit downloads MUST survive:

- browser restart
    
- app restart
    
- loss of network
    

---

# 17. OFFLINE VERSIONING

Each note has:

`version`

Example:

Remote:

version = 4

Local:

version = 3

Result:

Update available.

When online:

compare versions.

When remote version > local version:

show:

"Update available"

Do not automatically destroy local content before the replacement is successfully stored.

---

# 18. SEARCH SYSTEM

## MVP

Search against a controlled local/cached searchable dataset.

Fields:

title

tags

searchableText

Use normalization:

- lowercase
    
- trim
    
- basic token matching
    

Use input debounce.

Do not perform a Firestore query for every keystroke.

---

## Scaling Trigger

Client-side search must be reevaluated when:

- searchable note count becomes materially large
    
- initial search payload becomes expensive
    
- search latency becomes poor
    
- fuzzy/full-text relevance becomes necessary
    

Future candidates:

Typesense

Algolia

Meilisearch

Not MVP dependencies.

---

# 19. PWA REQUIREMENTS

Use:

vite-plugin-pwa

Required:

manifest

service worker

installability

standalone mode

icons

theme color

app-shell caching

---

## Important Boundary

Service Worker:

Application shell/static assets.

Dexie:

Explicitly downloaded educational content.

Do not blindly precache the entire notes library.

---

# 20. UI / UX SYSTEM

Design:

Minimal.

Mobile-first.

Primary background:

Neutral/white.

Accent:

One primary accent color.

Avoid:

- excessive gradients
    
- excessive shadows
    
- unnecessary animation
    
- decorative UI without function
    

---

## Mobile Navigation

Bottom navigation:

Home

Search

Bookmarks

Profile

---

## Desktop

Use centered responsive layout.

Navigation may transition to top/side navigation where appropriate.

---

## Required UI States

Every data-driven page:

Loading

Empty

Error

Success

Use skeleton loaders for content loading where appropriate.

---

# 21. PROJECT STRUCTURE

```text
src/
│
├── app/
│
├── components/
│   └── ui/
│
├── features/
│   ├── auth/
│   ├── subjects/
│   ├── topics/
│   ├── notes/
│   ├── search/
│   ├── bookmarks/
│   ├── offline/
│   ├── profile/
│   └── admin/
│
├── pages/
│
├── hooks/
│
├── services/
│
├── firebase/
│
├── db/
│
├── types/
│
├── utils/
│
└── assets/
```

Feature-specific code should stay inside its feature directory where practical.

---

# 22. CODING STANDARDS

TypeScript:

Strict mode.

Forbidden:

`any`

`@ts-ignore`

unexplained ESLint disables.

---

## Components

Keep components focused.

Do not enforce arbitrary 50-line limits.

Instead:

split components when they have multiple responsibilities.

Prefer readable code over artificial fragmentation.

---

## Styling

Tailwind CSS.

Avoid arbitrary inline styles.

---

## Duplication

Do not duplicate:

Firebase query logic

domain types

validation schemas

offline logic

auth logic

---

## Error Handling

Do not swallow errors.

User-facing failures require understandable messages.

Developer-facing failures should retain enough information for debugging.

---

# 23. TESTING POLICY

A feature is NOT complete merely because it renders.

Before marking a feature complete:

1. TypeScript check passes.
    
2. Lint passes.
    
3. Production build passes.
    
4. Relevant automated tests pass.
    
5. Acceptance criteria pass.
    
6. Security behavior is verified where relevant.
    

---

## Critical Tests

Authentication

Protected routes

Admin route protection

Firestore rules

Bookmark ownership

Offline downloads

Offline reading

Version update

Search

PWA installability

---

# 24. ENVIRONMENT VARIABLES

Required:

```env
VITE_FIREBASE_API_KEY=
VITE_FIREBASE_AUTH_DOMAIN=
VITE_FIREBASE_PROJECT_ID=
VITE_FIREBASE_STORAGE_BUCKET=
VITE_FIREBASE_MESSAGING_SENDER_ID=
VITE_FIREBASE_APP_ID=
```

Create:

`.env.example`

Never commit `.env`.

Firebase client configuration values are not treated as server secrets; authorization must be enforced through Firebase Security Rules.

---

# 25. AI AGENT CONSTITUTION

This section applies to OpenCode, Claude Code, Cursor, or other coding agents.

## Rule 1

Never build the entire project in one pass.

## Rule 2

One task must have one explicit acceptance boundary.

## Rule 3

Before modifying code:

READ relevant documentation.

READ existing related implementation.

READ current project state.

## Rule 4

Never invent missing requirements.

If a decision affects:

database

security

architecture

dependencies

routing

offline behavior

STOP and ask.

## Rule 5

Do not change the locked stack without explicit permission.

## Rule 6

Do not install a package when existing dependencies can reasonably solve the requirement.

## Rule 7

Never modify unrelated working features.

## Rule 8

Before marking a task complete:

run typecheck

run lint

run tests

run production build

## Rule 9

Report:

Files created

Files modified

Tests performed

Remaining TODOs

Known limitations

## Rule 10

Update project state after every completed feature.

---

# 26. AGENT CONTEXT PROTOCOL

Every coding session follows:

READ

↓

PLAN

↓

IMPLEMENT

↓

VERIFY

↓

REPORT

↓

UPDATE STATE

↓

COMMIT

Never skip directly from READ to mass implementation.

---

# 27. CURRENT STATE

Create:

`docs/27-CURRENT-STATE.md`

Template:

```md
# Current State

## Current Phase

Foundation

## Last Completed Task

None

## Completed

- [ ] Repository initialized

## In Progress

None

## Next Task

Project scaffolding

## Blockers

None

## Architecture Decisions

- React + Vite + TypeScript
- Firebase
- TanStack Query
- React Context for Auth
- Dexie for explicit offline content

## Known Technical Debt

None
```

Update this file after EVERY accepted task.

---

# 28. DECISION LOG

Create:

`docs/28-DECISIONS.md`

Example:

```md
# Architecture Decision Log

## ADR-001

Decision:
Use Firebase directly from client.

Reason:
MVP does not require custom backend.

Status:
Accepted.

---

## ADR-002

Decision:
Use Dexie for explicit offline downloads.

Reason:
Need structured IndexedDB access and versioning.

Status:
Accepted.
```

Never silently reverse an accepted decision.

---

# 29. DEVELOPMENT PHASES

## PHASE 0 — FOUNDATION

Do NOT build UI features yet.

Tasks:

Repository initialization

Vite

React

TypeScript

Tailwind

shadcn

React Router

TanStack Query

Firebase packages

Dexie

vite-plugin-pwa

Folder structure

Environment configuration

Linting

Testing framework

Firebase emulator setup

Security rule skeleton

Firestore indexes file

PWA baseline

Expected result:

Application builds and deploys with no business feature.

---

# PHASE 1 — DATA + SECURITY FOUNDATION

Build:

TypeScript domain types

Firebase initialization

Firestore service layer

Security rules

Storage rules

Firebase emulator configuration

Basic query infrastructure

Acceptance:

No schema field exists outside documented schema.

Security rules tested.

---

# PHASE 2 — AUTHENTICATION

Build:

Signup

Login

Logout

Forgot Password

AuthContext

ProtectedRoute

AdminRoute

User document creation

Acceptance:

Unauthenticated users blocked.

Students blocked from admin.

Users cannot modify role.

---

# PHASE 3 — APP SHELL

Build:

Router

Student layout

Bottom navigation

Desktop responsive navigation

404

Global loading/error handling

---

# PHASE 4 — SUBJECT BROWSING

Build:

Subject service

useSubjects hook

Subject page

Loading

Empty

Error

---

# PHASE 5 — TOPICS

Build:

Topic service

useTopics hook

Topic list

Navigation

---

# PHASE 6 — NOTES

Build:

Note service

Notes list

Markdown reader

Published-note filtering

Attachments

Version support

---

# PHASE 7 — BOOKMARKS

Build:

Bookmark service

Bookmark toggle

Bookmarks page

Ownership security

Optimistic update only if safely implemented.

---

# PHASE 8 — SEARCH

Build:

Search dataset

Normalization

Debounced search

Search results

Empty state

---

# PHASE 9 — OFFLINE ENGINE

Data-layer offline architecture should already have been anticipated earlier.

Now implement user-facing offline functionality:

Download note

Dexie storage

Downloaded state

Offline reader

Version comparison

Update download

Remove download

Storage size display

---

# PHASE 10 — PWA

Finalize:

Manifest

Icons

Service worker

Install flow

Offline app shell

Standalone verification

---

# PHASE 11 — ADMIN CMS

Build:

Admin dashboard

Subject CRUD

Topic CRUD

Note CRUD

Markdown editor

Publish/archive

Attachment upload

Admin security verification

---

# PHASE 12 — HARDENING

Test:

Mobile

Desktop

Offline

Auth

Security Rules

PWA

Error states

Slow network

Build output

Firestore read patterns

Accessibility

---

# PHASE 13 — DEPLOYMENT

Deploy:

Firebase Hosting

Firestore Rules

Storage Rules

Indexes

Environment configuration

Custom domain later if required.

---

# 30. TASK EXECUTION TEMPLATE

Every OpenCode task should use this structure:

```text
TASK:
[one specific feature]

READ FIRST:
[list relevant documentation]

EXISTING CODE TO INSPECT:
[list related files/directories]

DO:
[exact requirements]

DO NOT:
[scope exclusions]

ACCEPTANCE CRITERIA:
[testable conditions]

VERIFY:
npm run typecheck
npm run lint
npm run test
npm run build

AFTER COMPLETION:
Update docs/27-CURRENT-STATE.md.
Report files changed.
Report tests performed.
Report remaining issues.

Do not begin another feature.
```

---

# 31. FIRST OPENCODE PROMPT

Use this only after all SRS files are placed inside the repository.

```text
You are beginning development of the Notes PWA.

This is NOT a request to build the application.

Your first task is repository and architecture inspection.

Read:

docs/00-PROJECT-CONSTITUTION.md
docs/01-PROJECT-OVERVIEW.md
docs/07-DATABASE-SCHEMA.md
docs/09-TECH-STACK.md
docs/14-SECURITY.md
docs/21-PROJECT-STRUCTURE.md
docs/22-CODING-STANDARDS.md
docs/25-AI-AGENT-CONSTITUTION.md
docs/27-CURRENT-STATE.md
docs/28-DECISIONS.md

Then:

1. Summarize your understanding of the architecture.
2. Identify contradictions or missing information.
3. Identify any dependency/version compatibility concerns.
4. Propose the exact Phase 0 implementation plan.
5. List the files you intend to create.
6. Do NOT write or modify application code yet.

Wait for approval.
```

---

# 32. PHASE 0 PROMPT

After the architecture review is approved:

```text
TASK:
Implement Phase 0 Foundation only.

READ FIRST:

docs/09-TECH-STACK.md
docs/19-PWA-REQUIREMENTS.md
docs/21-PROJECT-STRUCTURE.md
docs/22-CODING-STANDARDS.md
docs/23-TESTING-POLICY.md
docs/24-ENVIRONMENT-VARIABLES.md
docs/25-AI-AGENT-CONSTITUTION.md
docs/27-CURRENT-STATE.md

DO:

Initialize/configure the documented project stack.

Create the required project structure.

Configure TypeScript strict mode.

Configure Tailwind and shadcn/ui.

Configure React Router baseline.

Configure TanStack Query provider.

Install/configure Firebase SDK without implementing business features.

Configure Dexie baseline.

Configure vite-plugin-pwa baseline.

Create .env.example.

Configure linting.

Configure testing.

Ensure development and production builds work.

DO NOT:

Build Login.

Build Signup.

Build Subjects.

Build Notes.

Build Admin.

Create undocumented Firestore fields.

Implement future features.

Change the tech stack.

ACCEPTANCE CRITERIA:

Application starts successfully.

TypeScript strict mode passes.

Lint passes.

Tests run.

Production build succeeds.

PWA configuration compiles.

No business feature has been implemented.

AFTER COMPLETION:

Update docs/27-CURRENT-STATE.md.

Report:

files created

files modified

packages installed

commands executed

test/build results

remaining issues

Then STOP.
```

---

# 33. DEVELOPMENT RULE

Never prompt:

"Build my Notes app."

Never prompt:

"Continue building everything."

Never prompt:

"Fix everything."

Instead:

one bounded task

relevant documentation

existing code

acceptance criteria

verification

STOP.

This is the primary mechanism used to reduce AI context drift and uncontrolled architectural changes.