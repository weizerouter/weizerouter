# API usage

## Choose the correct product and key

Main developer API: `https://weizerouter.com/v1`. Existing `.web.id` API addresses remain supported. Bot, website and product-specific keys/balances are not automatically interchangeable.

Read the current catalog with your own key:

```bash
curl --fail-with-body https://weizerouter.com/v1/models \
  -H "Authorization: Bearer $WEIZEROUTER_API_KEY"
```

Select an exact returned model ID; set `WEIZEROUTER_MODEL` to that ID. Never publish your environment values.

## Python (OpenAI SDK)

```python
import os
from openai import OpenAI
client = OpenAI(api_key=os.environ["WEIZEROUTER_API_KEY"],
                base_url="https://weizerouter.com/v1")
response = client.chat.completions.create(
    model=os.environ["WEIZEROUTER_MODEL"],
    messages=[{"role": "user", "content": "Hello!"}],
)
print(response.choices[0].message.content)
```

## Node.js streaming

```javascript
import OpenAI from 'openai';
const client = new OpenAI({
  apiKey: process.env.WEIZEROUTER_API_KEY,
  baseURL: 'https://weizerouter.com/v1',
});
const stream = await client.chat.completions.create({
  model: process.env.WEIZEROUTER_MODEL,
  messages: [{role: 'user', content: 'Hello!'}],
  stream: true,
});
for await (const chunk of stream) {
  process.stdout.write(chunk.choices[0]?.delta?.content ?? '');
}
```

## Anthropic-compatible clients

For supported models, use origin `https://weizerouter.com` and endpoint `POST /v1/messages`; the website also documents `/v1/messages/count_tokens`. Set the client's API key and exact supported model according to the live integration guide. Avoid a duplicated `/v1/v1` path.

## Compatibility limits

Context length, output limits, image input, tools, reasoning and streaming vary by model. OpenAI-compatible does not mean every native vendor feature is available. Optional headers and exact errors may vary; do not depend on undocumented telemetry headers.

Retry transient failures with bounded exponential backoff. Do not retry invalid credentials or insufficient balance indefinitely. A client disconnect or timeout needs reconciliation before resending expensive work; never assume an interrupted client received the final result.

[Models](models.md) · [Integrations](integrations.md) · [Errors](error-codes.md)
