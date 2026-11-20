# Testing Reference

Prioritize correctness over arbitrary coverage.

Backend:
- services
- validators
- authorization
- important routes
- authentication
- destructive operations
- payments/webhooks
- state transitions

Frontend:
- shared hooks
- query behavior
- important user flows
- forms
- critical state transitions

Include negative cases such as unauthenticated access, wrong role, wrong owner, malformed input, invalid auth, duplicate mutations, and unauthorized state transitions.
