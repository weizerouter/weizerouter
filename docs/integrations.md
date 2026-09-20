# WeizeRouter Developer Integrations Guide

Because WeizeRouter provides an official **OpenAI-Compatible `/v1`** API interface, you can integrate it seamlessly into almost every modern developer tool, IDE extension, and AI framework without modifying application logic.

---

## 🎯 Cursor IDE

Cursor is the developer favorite for WeizeRouter users.

1. Open **Cursor Settings** (gear icon) ➡️ **Models**.
2. Scroll to **OpenAI API Key**:
   - Turn **ON** `Override OpenAI Base URL`.
   - Set Base URL to: `https://weizerouter.web.id/v1`
   - Paste your active API key: `wzr-live-your-key-here`
3. Under **Model Names**, add the models you want to use:
   - `wz/muse-spark-1.3-contributor` *(Recommended for massive repositories - 1M context)*
   - `wz/gemini-3.8-flash-high` *(Recommended for ultra-fast inline code editing)*
   - `wz/grok-4.5`
4. Verify by opening Cursor Chat (`Cmd+L` or `Ctrl+L`) and asking a coding question.

---

## 🤖 Roo Code & Cline (VS Code Extensions)

1. Open **Roo Code** or **Cline** in the VS Code sidebar.
2. Click the **Settings** (gear icon) at the top right.
3. In **API Provider**, select: `OpenAI Compatible`.
4. Fill in the connection parameters:
   - **Base URL:** `https://weizerouter.web.id/v1`
   - **API Key:** `wzr-live-your-key-here`
   - **Model ID:** `wz/muse-spark-1.3-contributor` *(or `wz/gemini-3.8-flash-high`)*
5. Click **Done** / **Save**.

---

## 🌊 Continue.dev & Windsurf

In your `~/.continue/config.json`:

```json
{
  "models": [
    {
      "title": "WeizeRouter - Muse Spark 1.3 (1M)",
      "provider": "openai",
      "model": "wz/muse-spark-1.3-contributor",
      "apiKey": "wzr-live-your-key-here",
      "apiBase": "https://weizerouter.web.id/v1"
    },
    {
      "title": "WeizeRouter - Gemini 3.8 Flash High",
      "provider": "openai",
      "model": "wz/gemini-3.8-flash-high",
      "apiKey": "wzr-live-your-key-here",
      "apiBase": "https://weizerouter.web.id/v1"
    }
  ]
}
```

---

## 🌐 Open WebUI / AnythingLLM

1. Navigate to **Admin Panel** ➡️ **Settings** ➡️ **Connections**.
2. Under **OpenAI API**:
   - **URL:** `https://weizerouter.web.id/v1`
   - **Key:** `wzr-live-your-key-here`
3. Click **Verify Connection**. All active models from WeizeRouter will automatically populate your model selector.

---

## 🐍 Python (OpenAI SDK v1.x)

```python
from openai import OpenAI

client = OpenAI(
    api_key="wzr-live-your-key-here",
    base_url="https://weizerouter.web.id/v1"
)

# Non-streaming example
completion = client.chat.completions.create(
    model="wz/muse-spark-1.3-contributor",
    messages=[{"role": "user", "content": "Write an idiomatic LRU cache in Rust."}]
)
print(completion.choices[0].message.content)

# Streaming example
stream = client.chat.completions.create(
    model="wz/gemini-3.8-flash-high",
    messages=[{"role": "user", "content": "Explain raft consensus in 3 bullet points."}],
    stream=True
)
for chunk in stream:
    print(chunk.choices[0].delta.content or "", end="", flush=True)
print()
```

---

## ⚡ Node.js (Official OpenAI SDK)

```javascript
import OpenAI from 'openai';

const client = new OpenAI({
  apiKey: 'wzr-live-your-key-here',
  baseURL: 'https://weizerouter.web.id/v1',
});

const response = await client.chat.completions.create({
  model: 'wz/muse-spark-1.3-contributor',
  messages: [{ role: 'user', content: 'Design a scalable database schema for high-throughput messaging.' }],
});

console.log(response.choices[0].message.content);
```
