# WeizeRouter API Usage Specification

WeizeRouter provides an OpenAI-compatible API gateway designed for high-performance and automated operations routing.

## Base URL

```
https://weizerouter.web.id/v1
```

## Authentication

All requests must include your WeizeRouter token in the Authorization header:

```http
Authorization: Bearer YOUR_WEIZEROUTER_API_KEY
```

## Endpoints

### POST /chat/completions

Sends a completion request to a specific model. Custom client setups should route requests here.

**Request Headers:**
- `Authorization: Bearer YOUR_WEIZEROUTER_API_KEY`
- `Content-Type: application/json`

**Request Body (example):**

```json
{
  "model": "wz/gpt-5.5",
  "messages": [
    {"role": "user", "content": "Hello from WeizeRouter"}
  ]
}
```

**cURL example:**

```bash
curl https://weizerouter.web.id/v1/chat/completions \
  -H "Authorization: Bearer YOUR_WEIZEROUTER_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "model": "wz/gpt-5.5",
    "messages": [{"role":"user","content":"Hello from WeizeRouter"}]
  }'
```

## Error Codes

See [error-codes.md](./error-codes.md) for full list of error responses.
