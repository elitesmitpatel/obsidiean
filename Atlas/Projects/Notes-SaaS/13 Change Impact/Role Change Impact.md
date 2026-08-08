# Role Change Impact

Changing `UserRole` or role semantics affects:

- [[Auth Module]]
- [[Profile Module]]
- [[Admin Module]]
- [[AdminRoute]]
- [[STUDENT]]
- [[ADMIN]]
- `firestore.rules`
- production admin verification

Never add client-side role editing as a convenience feature.
