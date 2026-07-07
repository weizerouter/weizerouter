# WeizeRouter API Usage Specification

WeizeRouter provides an OpenAI-compatible API gateway designed for high-performance and automated operations routing.

## Base URL

```
https://api.weizerouter.io/v1
```

## Authentication

All requests must include your WeizeRouter token in the Authorization header:

```http
Authorization: Bearer wr-your-api-token-here
```

## Endpoints

### POST /chat/completions

Sends a completion request to a specific model. Custom client setups should route requests here.

**Request Headers:**
- `Authorization: Bearer wr-xxxxxx`
- `Content-Type: application/json`
