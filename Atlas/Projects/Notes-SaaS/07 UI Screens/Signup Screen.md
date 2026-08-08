# Signup Screen

Route: `/signup`.

Guard: [[PublicOnlyRoute]].

Collects display name, email, password (minimum 6 chars) and calls signup.

Side effect: [[Users Collection]] creation.

Change Impact: [[Authentication]], user document rules, signup tests.
