# Editors, agents and SDK integrations

Official guide: https://weizerouter.web.id/cli-guide.html. Main API origin: https://weizerouter.com.

## OpenAI-compatible tools

For a client that supports a custom provider, configure:

- Provider: OpenAI-compatible.
- Base URL: `https://weizerouter.com/v1`.
- API key: your own WeizeRouter key, stored in the client's private configuration.
- Model: exact model ID available to your key from `/v1/models`.

This pattern applies to compatible versions of Cursor, Cline, Roo Code, Continue, OpenCode, Kilo Code, Hermes Agent and custom SDK applications. Features and configuration names vary by client/version; consult its own documentation rather than assuming an invented setting exists.

## Anthropic-compatible tools

Use `https://weizerouter.com` as the origin for clients that append `/v1/messages`. Select an eligible model and configure the client using the current public integration guide. Claude Code and other tools may require provider-specific options; a successful catalog request does not prove all tool workflows work.

## SDKs

[Python and Node examples](api-usage.md) use environment variables, not embedded real keys. Never commit `.env`, private portal links or local credential stores.

## Integration checklist

1. Confirm the product/account and correct key.
2. Fetch its exact model IDs.
3. Send a small request and inspect the actual response.
4. Test streaming/tools only when the model supports them.
5. Confirm usage in the same product wallet.
6. Bound retries and respect rate-limit responses.

RPM is requests per minute, not concurrent requests. Do not build unbounded retry or fallback loops.
