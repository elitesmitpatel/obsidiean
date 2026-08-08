# Testing Overview

The repository uses Vitest + Testing Library and behavior-focused tests.

## Test categories

- Auth service/context/route tests
- Subject/topic hook/component tests
- Notes hook/component/reader tests
- Bookmark component/hook tests
- Search hook/component/page tests
- Offline service/hook/component/reader tests
- Profile hook/component tests
- Admin guard/form/list/mutation/routing tests
- Firebase configuration tests
- Firestore security tests

## Current verification baseline from project reports

383 tests passed before `/downloads` remediation; the remediation added 11 tests, producing a 394-test baseline in the supplied Phase 9 remediation report.

Always rerun the repository's current `npm run test` before treating this historical count as current.
