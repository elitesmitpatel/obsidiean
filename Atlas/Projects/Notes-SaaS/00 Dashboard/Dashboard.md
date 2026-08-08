# Dashboard

## Project

[[Project Overview]] — Notes SaaS knowledge base.

## Architecture at a glance

- UI → [[Hooks]] → [[Services]] → [[Firestore]] / [[IndexedDB]]
- Authentication state is owned by [[Auth Module]] via React Context.
- Server state is owned by [[TanStack Query]].
- Offline state is persisted in [[IndexedDB]] through [[Offline Module]].
- Routing is centralized in [[Router]] and protected by [[ProtectedRoute]] / [[AdminRoute]].

## Modules

- [[Auth Module]]
- [[App Shell Module]]
- [[Subjects Module]]
- [[Topics Module]]
- [[Notes Module]]
- [[Bookmarks Module]]
- [[Search Module]]
- [[Offline Module]]
- [[Profile Module]]
- [[Admin Module]]
- [[Services Module]]
- [[Firebase Module]]
- [[Database Module]]

## Core features

- [[Authentication]]
- [[Subject Browsing]]
- [[Topic Browsing]]
- [[Notes Reader]]
- [[Bookmarks]]
- [[Search]]
- [[Offline Downloads]]
- [[Downloads Screen]]
- [[Profile]]
- [[Admin CMS]]
- [[PWA]]

## Screens

- [[Login Screen]]
- [[Signup Screen]]
- [[Forgot Password Screen]]
- [[Home Screen]]
- [[Subject Screen]]
- [[Topic Screen]]
- [[Note Reader Screen]]
- [[Search Screen]]
- [[Bookmarks Screen]]
- [[Downloads Screen]]
- [[Profile Screen]]
- [[Admin Dashboard Screen]]
- [[Admin Subjects Screen]]
- [[Admin Topics Screen]]
- [[Admin Notes Screen]]

## Data

- [[Users Collection]]
- [[Subjects Collection]]
- [[Topics Collection]]
- [[Notes Collection]]
- [[Bookmarks Collection]]
- [[Downloaded Notes Table]]

## Roles

- [[STUDENT]]
- [[ADMIN]]

## Workflows

- [[Signup Workflow]]
- [[Login Workflow]]
- [[Browse Notes Workflow]]
- [[Read Note Workflow]]
- [[Bookmark Workflow]]
- [[Search Workflow]]
- [[Download Workflow]]
- [[Offline Reader Workflow]]
- [[Profile Update Workflow]]
- [[Admin Content Workflow]]
- [[Production Deployment Workflow]]

## Integrations

- [[Firebase Integration]]
- [[Firebase Authentication Integration]]
- [[Firestore Integration]]
- [[Dexie Integration]]
- [[PWA Integration]]
- [[React Router Integration]]
- [[TanStack Query Integration]]

## Recent changes

1. **Phase 13 — Production Deployment:** Firebase Hosting configuration and production project alias were finalized; production verification was completed.
2. **Phase 9 remediation:** `/downloads` was added as a protected route backed by existing Dexie download infrastructure.
3. **Attachment removal:** Firebase Storage/PDF attachment support was removed; notes are Markdown-only. Cloudinary was intentionally not introduced.

## Current risks / impact hotspots

- Changing `NoteDocument` affects reader, search, bookmarks, offline storage/versioning, admin CMS, and multiple Firestore queries.
- Changing `UserDocument.role` affects [[AdminRoute]], Firestore rules, and admin workflows.
- Changing note `version` semantics affects offline update detection.
- Changing Firestore query constraints can require matching composite indexes.
- Changing route structure affects [[Router]], Hosting SPA rewrites, navigation links, and route tests.

## Change-control entry point

Start with [[Change Impact Index]] before modifying a cross-cutting feature.
