# Production Reference

Before deployment verify:
- production build
- correct startup command
- health/readiness endpoints
- graceful shutdown
- production-safe logging
- restricted CORS
- secure cookies
- external secrets
- rate limiting
- safe errors
- webhook verification
- complete environment configuration
- `.env.example`
- migration strategy
- important indexes
- bounded queries
- production API URL
- authentication callback URLs
- webhook URLs
- storage/upload behavior
- deployment platform/runtime constraints

Verify the actual deployment platform instead of assuming a generic Node server model.
