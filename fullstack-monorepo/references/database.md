# Database Reference

Database access stays behind the backend.

Rules:
- validate before persistence
- authorize before sensitive reads/writes
- index important query patterns
- paginate large collections
- avoid N+1 queries
- select only necessary fields when useful
- use transactions for multi-write invariants
- use atomic operations for counters/inventory where supported
- never trust client-supplied derived values

Schema changes should update the schema/migrations, services, types, tests, and documentation.

For money, use the smallest currency unit rather than floating point values and keep amount/currency semantics consistent across API, database, frontend, and payment provider.
