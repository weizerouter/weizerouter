# API Usage

WeizeRouter provides an OpenAI-compatible API endpoint.

## Base URL

```txt
https://weizerouter.web.id/v1
```

## Chat Completions Example

```bash
curl https://weizerouter.web.id/v1/chat/completions   -H "Authorization: Bearer wzr_live_xxx_demo"   -H "Content-Type: application/json"   -d '{
    "model": "demo-model",
    "messages": [
      {
        "role": "user",
        "content": "Say hello from WeizeRouter"
      }
    ]
  }'
```

## Authentication

Use the API key provided by the WeizeRouter Telegram bot.

Example:

```txt
Authorization: Bearer wzr_live_xxx_demo
```

Never expose your real API key publicly.

## Model Access

Model access depends on the active package.

Example package levels:

- Mini Trial
- Trial
- Pro
- Ultimate

## Error Handling

Common API responses may include:

- invalid API key
- package expired
- model not available for package
- fair-use cooldown active
- provider unavailable
- gateway error
