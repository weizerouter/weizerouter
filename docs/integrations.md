# WeizeRouter Integrations Guide


This document describes how to integrate WeizeRouter into standard client tools.


## Cursor / Cline Integration


Configure Cursor or Cline to use a custom OpenAI-compatible endpoint:
- **API Base**: `https://weizerouter.web.id/v1`
- **API Key**: `wr-your-token-here`
- **Model**: Select the appropriate routing model name.


## Open WebUI / AnythingLLM / SillyTavern


Set the OpenAI API endpoint to:
- Base URL: `https://weizerouter.web.id/v1`
- API Key: your WeizeRouter token
- Model: any supported model (e.g. `wz/gpt-5.5`, `wz/grok-3`, etc.)


## LangChain / LlamaIndex / AutoGen


Use the OpenAI client with custom base URL:
```python
from openai import OpenAI

client = OpenAI(
    base_url="https://weizerouter.web.id/v1",
    api_key="wr-your-token-here"
)
```


## Notes


- Always use the correct base URL for your region.
- Tokens are scoped to the packages you purchased.
- Rate limits and fair-use rules apply per package tier.
