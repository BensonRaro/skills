# Environment Reference

All environment-specific values belong in configuration.

Backend examples:
```env
NODE_ENV=development
PORT=5000
BACKEND_URL=http://localhost:5000
FRONTEND_URL=http://localhost:5173
DATABASE_URL=...
AUTH_SECRET=...
STRIPE_SECRET_KEY=...
STRIPE_WEBHOOK_SECRET=...
```

Frontend example:
```env
VITE_API_URL=http://localhost:5000
```

Rules:
- `.env` is private/local.
- `.env.example` is committed.
- Every new env variable must be documented in `.env.example`.
- Validate required variables at startup.
- Never hardcode production URLs.
- Never expose backend secrets through public frontend variables.
- OAuth callback URLs, webhook URLs, external service endpoints, and deployment-specific origins should be configurable.
