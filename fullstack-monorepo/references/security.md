# Security Reference

Baseline:
- Helmet
- strict CORS
- secure/httpOnly/SameSite cookies
- Secure cookies in production
- request body limits
- runtime validation
- authentication
- authorization
- rate limiting
- brute-force protection where appropriate
- webhook signature verification
- safe errors
- safe logging
- dependency hygiene

CORS must allow known origins in production. Configure origins through environment variables.

Authorization must verify resource ownership server-side. Never trust a role/permission sent by the client.

Rate-limit login, password reset, registration, verification, expensive, and sensitive mutation endpoints.

Webhook handlers must verify signatures and be designed for idempotency because providers can retry.

Never log passwords, tokens, API keys, secrets, or sensitive request bodies.
