# Firestore API

## SDK operations used

- `collection`
- `doc`
- `getDoc`
- `getDocs`
- `query`
- `where`
- `orderBy`
- `setDoc`
- `updateDoc`
- `deleteDoc`
- `serverTimestamp`

## Collections

[[Users Collection]], [[Subjects Collection]], [[Topics Collection]], [[Notes Collection]], [[Bookmarks Collection]].

## Change Impact

Changing queries can require index changes. Changing writes must remain consistent with [[Security Architecture]] and document schemas.
