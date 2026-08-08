# Subjects Module

**Location:** `src/features/subjects/`

## Responsibility
List active subjects for authenticated users and navigate to a subject's topics.

## Data
[[Subjects Collection]]

## Service
`subjectService.getActiveSubjects()` orders by `orderIndex ASC` and filters `isActive = true`.

## UI
[[Home Screen]], [[Subject Screen]]

## Change Impact
Changing subject fields affects cards, admin forms, Firestore schema/rules, ordering indexes, and topic relationships. Changing the query affects `subjects(isActive, orderIndex)` index requirements.
