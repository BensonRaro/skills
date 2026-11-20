# Documentation Reference

Recommended:
```text
docs/
├── architecture.md
├── setup.md
├── api.md
├── authentication.md
├── database.md
├── deployment.md
└── decisions.md
```

Document architecture, setup, API behavior, authentication/authorization, database decisions, integrations, deployment, non-obvious business rules, and important technical decisions.

Comments should explain WHY, constraints, or non-obvious behavior.

Good:
```ts
// Keep this authorization check server-side because the client can modify the submitted role.
```

Avoid comments that simply restate the code.
