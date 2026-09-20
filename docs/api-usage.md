# WeizeRouter API Usage Specification

WeizeRouter provides an OpenAI-compatible API gateway designed for high-performance, resilient, and cost-efficient LLM routing.

---

## Base URL & Authentication

All API calls must be directed to the official base URL with your active WeizeRouter API key included in the HTTP headers:

```http
POST https://weizerouter.web.id/v1/chat/completions
Authorization: Bearer wzr-live-your-api-key-here
Content-Type: application/json
```

---

## Endpoints

### `POST /v1/chat/completions`

Creates a model response for the given chat conversation.

#### Request Body Schema

| Parameter | Type | Required | Description |
| :--- | :---: | :---: | :--- |
| `model` | `string` | **Yes** | The model identifier (e.g. `wz/muse-spark-1.3-contributor`, `wz/gemini-3.8-flash-high`). |
| `messages` | `array` | **Yes** | List of message objects representing the conversation history. |
| `stream` | `boolean` | Optional | If `true`, returns Server-Sent Events (SSE) streaming chunks. Default is `false`. |
| `temperature` | `number` | Optional | Sampling temperature between `0` and `2`. |
| `max_tokens` | `integer` | Optional | The maximum number of tokens to generate in the completion. |

#### cURL Streaming Example

```bash
curl -N -sS https://weizerouter.web.id/v1/chat/completions \
  -H "Authorization: Bearer wzr-live-your-api-key-here" \
  -H "Content-Type: application/json" \
  -d '{
    "model": "wz/muse-spark-1.3-contributor",
    "messages": [
      {"role": "system", "content": "You are an expert systems programmer."},
      {"role": "user", "content": "Explain zero-copy I/O in modern Linux kernels."}
    ],
    "stream": true
  }'
```

---

### `GET /v1/models`

Lists all currently available models filtered by your active package permissions.

```bash
curl -sS https://weizerouter.web.id/v1/models \
  -H "Authorization: Bearer wzr-live-your-api-key-here"
```

---

## Response Headers

WeizeRouter provides transparency telemetry headers on every successful response:

- `x-weize-engine`: The active backend engine (`go-fast-proxy/1.0`, `9router-core`).
- `x-ratelimit-limit-rpm`: Your allocated requests-per-minute threshold.
- `x-ratelimit-remaining-rpm`: Remaining requests in the current rate limit window.
