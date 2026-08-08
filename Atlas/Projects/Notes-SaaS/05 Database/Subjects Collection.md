# Subjects Collection

**Path:** `subjects/{subjectId}`

## Fields

`id`, `name`, `slug`, `description`, optional `iconUrl`, `orderIndex`, `isActive`, `createdAt`, `updatedAt`.

## Read patterns

- Active student list: `where(isActive == true)` + `orderBy(orderIndex ASC)`.
- Admin list: `orderBy(orderIndex ASC)`.
- Direct lookup by ID.

## Writes

ADMIN only through [[Admin CMS]].

## Index

`subjects(isActive ASC, orderIndex ASC)` supports active listing.

## Relationships

A subject is the parent of [[Topics Collection]] and is referenced by notes.

## Change Impact
Field changes affect subject cards, admin forms, topic relationships, query indexes, and services.
