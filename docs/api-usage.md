# API Usage Guide

This guide explains how to use the WeizeRouter API Gateway.

---

## Base URL

```
https://weizerouter.web.id/v1
```

All API requests should be made to this base URL.

---

## Authentication

WeizeRouter uses **Bearer token authentication** compatible with OpenAI SDK.

**Header format:**
```
Authorization: Bearer YOUR_API_KEY
```

**API Key format:**
- Telegram Bot keys: `wzr_live_XXXXXXXX`
- Web Platform keys: `wzr_live_XXXXXXXX`

Get your API key from:
- Telegram Bot: [@WeizeRouterBot](https://t.me/WeizeRouterBot)
- Web Dashboard: [https://weizerouter.web.id/dashboard](https://weizerouter.web.id/dashboard)

---

## Available Models

### Mini Trial Package (1 Model)
- `ag/gemini-3.5-flash-extra-low` — Ultra-low cost Gemini 3.5 Flash

### Trial Package (1 Model)
- `ag/gemini-3.5-flash-extra-low` — Ultra-low cost Gemini 3.5 Flash

### Pro Package (4 Models)
- `ag/gemini-3.5-flash-low` — Low cost Gemini 3.5 Flash
- `ag/gemini-3-flash` — Standard Gemini 3 Flash
- `ag/gemini-3-flash-agent` — Gemini 3 Flash optimized for agents
- `weizerouter/glm-5` — GLM 5 (Zhipu AI)

### Ultimate Package (All Models)
- All Pro models +
- `ag/gemini-pro-agent` — Gemini Pro optimized for agents
- `ag/gemini-3.1-pro-low` — Gemini 3.1 Pro (low cost)
- `weizerouter/kimi-k2.7-code` — Kimi K2.7 optimized for coding
- `ag/claude-sonnet-4-6` — Claude Sonnet 4.6
- `ag/claude-opus-4-6-thinking` — Claude Opus 4.6 with extended thinking
- And more models as available

**Note:** Model availability depends on your active package tier.

---

## Endpoints

### Chat Completions

**Endpoint:** `POST /v1/chat/completions`

Standard OpenAI-compatible chat completions endpoint.

**Request format:**
```json
{
  "model": "ag/gemini-3.5-flash-low",
  "messages": [
    {"role": "system", "content": "You are a helpful assistant."},
    {"role": "user", "content": "Hello!"}
  ],
  "temperature": 0.7,
  "max_tokens": 1000
}
```

**Response format:**
```json
{
  "id": "chatcmpl-xxx",
  "object": "chat.completion",
  "created": 1234567890,
  "model": "ag/gemini-3.5-flash-low",
  "choices": [
    {
      "index": 0,
      "message": {
        "role": "assistant",
        "content": "Hello! How can I help you today?"
      },
      "finish_reason": "stop"
    }
  ],
  "usage": {
    "prompt_tokens": 20,
    "completion_tokens": 10,
    "total_tokens": 30
  }
}
```

---

## Code Examples

### cURL

```bash
curl https://weizerouter.web.id/v1/chat/completions \
  -H "Authorization: Bearer wzr_live_xxx_demo" \
  -H "Content-Type: application/json" \
  -d '{
    "model": "ag/gemini-3.5-flash-low",
    "messages": [
      {"role": "user", "content": "Explain AI in simple terms"}
    ]
  }'
```

### JavaScript (Node.js with OpenAI SDK)

```javascript
import OpenAI from 'openai';

const client = new OpenAI({
  baseURL: 'https://weizerouter.web.id/v1',
  apiKey: 'wzr_live_xxx_demo'
});

async function main() {
  const response = await client.chat.completions.create({
    model: 'ag/gemini-3.5-flash-low',
    messages: [
      { role: 'user', content: 'Explain AI in simple terms' }
    ]
  });
  
  console.log(response.choices[0].message.content);
}

main();
```

### Python (OpenAI SDK)

```python
from openai import OpenAI

client = OpenAI(
    base_url="https://weizerouter.web.id/v1",
    api_key="wzr_live_xxx_demo"
)

response = client.chat.completions.create(
    model="ag/gemini-3.5-flash-low",
    messages=[
        {"role": "user", "content": "Explain AI in simple terms"}
    ]
)

print(response.choices[0].message.content)
```

### TypeScript (OpenAI SDK)

```typescript
import OpenAI from 'openai';

const client = new OpenAI({
  baseURL: 'https://weizerouter.web.id/v1',
  apiKey: 'wzr_live_xxx_demo'
});

async function main() {
  const response = await client.chat.completions.create({
    model: 'ag/gemini-3.5-flash-low',
    messages: [
      { role: 'user', content: 'Explain AI in simple terms' }
    ]
  });
  
  console.log(response.choices[0].message.content);
}

main();
```

---

## Error Handling

### Common Error Codes

**401 Unauthorized:**
- Invalid or expired API key
- Missing Authorization header

**403 Forbidden:**
- Package expired
- Model not available in your package tier
- Fair use cooldown active

**429 Too Many Requests:**
- Rate limit exceeded
- Fair use cooldown protection triggered

**500 Internal Server Error:**
- Gateway error
- Model provider unavailable

**Example error response:**
```json
{
  "error": {
    "message": "Invalid API key",
    "type": "invalid_request_error",
    "code": "invalid_api_key"
  }
}
```

---

## Best Practices

1. **Store API keys securely** — Never commit API keys to public repositories
2. **Handle errors gracefully** — Implement retry logic with exponential backoff
3. **Monitor usage** — Check your dashboard for token consumption
4. **Choose appropriate models** — Balance cost vs. capability based on your use case
5. **Implement timeouts** — Set reasonable request timeouts (30-60 seconds)
6. **Cache responses** — Cache repeated queries to save costs

---

## Rate Limits

Rate limits depend on your package tier:

- **Mini Trial / Trial:** Basic fair use limits
- **Pro:** Higher limits for regular usage
- **Ultimate:** Unlimited fair use with cooldown protection

See [Fair Use Policy](fair-use.md) for details.

---

## Support

Need help?
- Telegram Bot: [@WeizeRouterBot](https://t.me/WeizeRouterBot)
- LinkedIn: [Wang Weize](https://www.linkedin.com/in/weize-wang-4262b7406)

---

**Last Updated:** July 2026
