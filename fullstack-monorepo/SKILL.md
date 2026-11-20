---
name: fullstack-monorepo
description: Production-ready architecture and engineering standards for two-service MERN/PERN monorepos using React/TypeScript and Express/TypeScript.
---

# Full-Stack Monorepo Skill

Use this skill for production-ready full-stack applications with separate frontend and backend services, especially MERN/PERN projects.

## Core workflow
1. Inspect the existing repository and package manifests.
2. Identify the existing frontend, backend, database, auth, runtime, and deployment stack.
3. Read the relevant references in this skill.
4. Reuse existing patterns; do not introduce parallel architecture without a reason.
5. Keep frontend and backend responsibilities separate.
6. Keep files focused and small.
7. Build production-ready code, not demo code.
8. Update documentation and `.env.example` when behavior or configuration changes.
9. Run relevant verification before declaring work complete.

## Default monorepo
```text
project/
├── backend/
│   ├── src/
│   │   ├── server.ts
│   │   ├── app.ts
│   │   ├── config/
│   │   ├── controllers/
│   │   ├── services/
│   │   ├── repositories/      # only when useful
│   │   ├── validators/
│   │   ├── routes/
│   │   ├── middlewares/
│   │   ├── lib/
│   │   ├── utils/
│   │   ├── types/
│   │   └── health/
│   ├── prisma/ or database/
│   ├── tests/
│   ├── .env
│   ├── .env.example
│   └── package.json
├── frontend/
│   ├── src/ or app/
│   │   ├── routes/
│   │   ├── features/
│   │   ├── components/
│   │   │   ├── ui/
│   │   │   └── globals/
│   │   ├── hooks/
│   │   ├── lib/
│   │   ├── services/
│   │   ├── types/
│   │   └── styles/
│   ├── .env
│   ├── .env.example
│   └── package.json
├── docs/
├── AGENTS.md
├── README.md
└── package.json
```
Adapt the structure to the actual project. Do not create empty directories just to match the template.

## Architecture
Default backend flow:
```text
Route → Middleware → Controller → Service → Repository/ORM → Database
```
- Routes define HTTP paths, methods, middleware, and controller references.
- Controllers translate HTTP requests/responses and remain thin.
- Services contain business logic and orchestration.
- Repositories are optional; use them when persistence logic is complex, repeated, or benefits from isolation.
- Validators perform runtime input validation.
- Middleware handles cross-cutting concerns.
- Database access stays on the backend.

Do not put database queries or business logic directly in routes.

## File size
Preferred target: ~100 lines or less.
Normal maximum: 200 lines.
If a file approaches 200 lines, split by responsibility. Do not split mechanically just to satisfy a number. A justified exception is better than artificial fragmentation.

Examples:
- controller → controller + service
- service → service + focused helper/repository
- React page → page + feature components
- form → form + field sections/hooks
- repeated logic → shared utility/hook when genuinely reusable

## Server architecture
Prefer:
```text
backend/src/app.ts
backend/src/server.ts
```
`app.ts` configures Express. `server.ts` starts the process and stays small.

`app.ts` should normally configure:
- helmet
- restricted cors
- express.json with an intentional body-size limit
- express.urlencoded when needed
- cookie-parser
- morgan or the project's structured logger
- request/correlation ID when useful
- health/readiness endpoints
- API routes
- 404 handling
- centralized error handling

Use one configuration loader rather than scattering `dotenv.config()` throughout feature files.

`server.ts` should normally:
1. import the configured app
2. read validated configuration
3. start listening
4. handle startup failures
5. handle graceful shutdown

Do not put route definitions or business logic in `server.ts`.

## Health checks
Provide `GET /health` for process liveness. When useful, provide a readiness endpoint such as `GET /ready` that checks required dependencies. Never expose secrets or sensitive infrastructure details.

## Security baseline
Security is architectural:
- Helmet
- strict CORS allowlists
- secure/httpOnly/SameSite cookies as appropriate
- Secure cookies in production
- body-size limits
- runtime validation
- authentication
- server-side authorization
- rate limiting, especially auth/sensitive endpoints
- brute-force protection where appropriate
- webhook signature verification
- safe errors
- dependency hygiene
- secret management
- safe logging

Never trust client-provided roles, permissions, ownership, prices, account IDs, or privileged state transitions.

## Environment variables
All environment-specific configuration belongs in environment variables.

Maintain relevant:
```text
backend/.env
backend/.env.example
frontend/.env
frontend/.env.example
```
Every new variable must be added to `.env.example`.

Use envs for database URLs, frontend/backend/API URLs, auth URLs/secrets, OAuth callbacks, external service endpoints, webhook URLs, storage endpoints, AI configuration, and deployment-specific origins.

Never hardcode production URLs. Frontend public variables must use the framework's public prefix. Never expose server secrets.

## API conventions
Prefer predictable REST:
```text
GET    /api/resources
GET    /api/resources/:id
POST   /api/resources
PATCH  /api/resources/:id
DELETE /api/resources/:id
```
Use plural resources and lowercase kebab-case. Use consistent status codes and error shapes. Paginate large collections and cap the maximum page size.

Example error:
```json
{"error":{"code":"RESOURCE_NOT_FOUND","message":"Resource not found"}}
```
Never return raw ORM/database errors or production stack traces.

## Validation
Validate all untrusted input: body, query, params, relevant headers, uploads, webhook payloads, and external responses where needed. Prefer the project's existing validation system, commonly Zod. TypeScript types do not replace runtime validation.

## Error handling
Use centralized error handling. Expected errors have stable codes, safe messages, and correct status codes. Unexpected errors are logged securely and return generic production-safe responses. Never leak secrets, stack traces, filesystem paths, database details, or sensitive request data.

## Logging
Use useful structured logging in production. Log startup/shutdown, errors, security events, important business events, and external service failures. Never log passwords, tokens, session secrets, API keys, payment secrets, or sensitive request bodies.

## Database
Database access belongs behind the backend boundary.
- validate inputs
- authorize before sensitive reads/writes
- index important query patterns
- paginate large collections
- avoid N+1 queries
- select only necessary fields where useful
- use transactions for multi-write invariants
- use atomic operations for counters/inventory where supported
- never trust client-supplied derived values

For financial values, use the smallest currency unit rather than floating point values.

## Frontend architecture
The frontend consumes the backend API and does not duplicate backend business rules.

Prefer feature organization:
```text
features/
├── admissions/
├── students/
├── teachers/
└── payments/
```
Feature-specific components stay with the feature. Shared primitives go in `components/ui/`; cross-feature application components go in `components/globals/`. Promote components only when reuse is real or justified.

## Frontend data access
Prefer:
```text
Component → Hook/Query → Central API Client → Backend
```
Centralize base URL, credentials, headers, auth behavior, and error normalization. Never put backend secrets in browser code.

## Types
Avoid manually maintaining the same API contract in unrelated places. Prefer types derived from validation schemas, generated API types, or carefully selected DTOs. Never expose server-only types or secrets.

## Documentation
Keep the codebase documented as it evolves. Prefer self-explanatory code. Comments explain why, constraints, or non-obvious behavior rather than restating obvious code.

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
Update documentation when a significant feature changes architecture, configuration, API behavior, security, or data behavior.

## Testing
Prioritize service/business logic, authorization, validators, important API flows, authentication, destructive operations, payment/webhook behavior, and state transitions. For frontend prioritize hooks, queries, forms, and critical user flows. Test negative/security cases, not only happy paths.

## Production readiness
Before declaring a meaningful feature complete, verify as applicable:
- typecheck
- lint
- tests
- production build
- environment validation
- authentication/authorization
- validation/error handling
- loading/empty/error states
- pagination/bounded queries
- Helmet/CORS/cookies/rate limits
- webhook verification
- secrets protection
- documentation
- deployment configuration
- health/readiness checks

Never claim a check was performed unless it was actually run.

## Git
Prefer focused conventional commits:
`feat:`, `fix:`, `refactor:`, `chore:`, `docs:`, `test:`, `security:`.
Do not mix unrelated work.

## Definition of done
- [ ] Existing architecture was inspected and followed.
- [ ] Controllers remain thin.
- [ ] Business logic is in services.
- [ ] Input is validated.
- [ ] Authorization is enforced server-side.
- [ ] Environment-specific values are not hardcoded.
- [ ] `.env.example` is updated.
- [ ] Sensitive information is not logged/exposed.
- [ ] Database access is efficient and authorized.
- [ ] Frontend loading/empty/error states exist where needed.
- [ ] Relevant tests exist.
- [ ] Documentation is updated.
- [ ] Files remain focused and reasonably small.
- [ ] Production configuration is considered.
- [ ] Verification passes.
