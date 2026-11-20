# API Conventions Reference

Prefer:
```text
GET    /api/resources
GET    /api/resources/:id
POST   /api/resources
PATCH  /api/resources/:id
DELETE /api/resources/:id
```

Use plural resource names and lowercase kebab-case.

Use a consistent error shape:
```json
{
  "error": {
    "code": "RESOURCE_NOT_FOUND",
    "message": "Resource not found"
  }
}
```

Validate query/filter values. Bound list endpoints with pagination and a server-side maximum. Use idempotency where duplicate requests could cause harmful side effects, especially payments.
