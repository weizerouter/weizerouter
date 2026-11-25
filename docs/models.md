# Models and permissions

Use `GET https://weizerouter.com/v1/models` with your account's key to discover exact model IDs. The website catalog presents current model families and capabilities; access depends on product, wallet and entitlement.

Do not hard-code a model from an old README merely because its vendor family sounds familiar. A catalog entry is discovery information, not proof of successful live inference. Model routes may be paused or unavailable.

## What to check

- Exact model ID and whether your key is authorized.
- Regular / Premium tier and applicable multiplier.
- Context and output token limits.
- Tool calling, streaming, reasoning and image-input support.
- Any additional reseller or package-specific eligibility.

Audio, image, video and adult-only text are separate products; their IDs and credentials are not automatically interchangeable with chat. Omni presents its own selectable catalog and credits.

The documentation deliberately avoids freezing model counts or vendor-generation tables that go stale quickly. Confirm a small supported request in your own account before relying on a model in production.
