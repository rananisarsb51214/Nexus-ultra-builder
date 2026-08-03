# API_REGISTRY — API Standards & Examples

This document standardizes how APIs in Nexus Ultra Builder are designed and consumed.

Design Principles

- Versioned: /api/v1/... then evolve to /api/v2
- Consistent error schema: {"code": "string", "message": "string", "details": object}
- Use HTTP status codes properly: 200/201/202 for success, 4xx for client errors, 5xx for server errors
- Pagination: cursor-based with `next_cursor` and `limit`
- Rate limiting: return 429 with Retry-After header

Authentication & Authorization

- Prefer JWT for service-to-service and session cookies with SameSite=Strict for browser sessions.
- OAuth2 for third-party integrations.

Sample endpoints

- POST /api/ai/generate — Body: {model: string, prompt: string, context: object}
- POST /api/websites — Create website
- GET /api/websites/{id}/pages — List pages

Error example

400 Bad Request

```
{
  "code": "invalid_payload",
  "message": "Website spec missing 'name' field",
  "details": {"field": "name"}
}
```

API Lifecycle

- Document new endpoints in API_REGISTRY.md and add OpenAPI specs in /Yaml when ready.
- Apply semantic versioning for breaking changes and provide migration guides.
