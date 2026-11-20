# Architecture Reference

Use a two-service monorepo:
```text
project/
├── backend/
└── frontend/
```

Backend owns database access, authentication, authorization, business logic, integrations, and sensitive operations.

Frontend owns presentation, interaction, UI state, API consumption, and client-side UX validation. It is never the security authority.

Default backend flow:
```text
Route → Middleware → Controller → Service → Repository/ORM → Database
```

Keep responsibilities clear:
- Route: path, method, middleware, controller
- Controller: HTTP translation
- Service: business rules/workflows
- Repository: persistence isolation only when justified
- Validator: runtime input validation
- Middleware: cross-cutting concerns
