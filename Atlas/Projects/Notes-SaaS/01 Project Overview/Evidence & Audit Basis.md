# Evidence & Audit Basis

This knowledge base was generated from the supplied `Notes-SaaS` project ZIP and the project reports available in the conversation.

## Source inspected

- `src/`
- `docs/`
- `firebase.json`
- `firestore.rules`
- `firestore.indexes.json`
- `package.json`
- `README.md`
- `AGENTS.md`
- project configuration files

The ZIP contained `node_modules`, `.git`, and Firebase emulator/build artifacts, but those were excluded from the knowledge-base source analysis because they are generated/dependency data rather than application architecture.

## Credential handling

No `.env` secret values, Firebase API key values, passwords, tokens, or service-account credentials are reproduced here.

## Important source-vs-history distinction

The current source tree is the primary basis for code-level relationships. Phase/deployment reports from the conversation are used only for historical status and recent-change context.

Where a runtime production fact cannot be proven from source code alone, it is described as a project-reported verification rather than inferred from code.
