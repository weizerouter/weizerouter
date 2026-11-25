# API and integration errors

Read the actual response body and request reference. Exact error names can vary by endpoint/model.

- **400:** invalid parameters, unsupported model or limits. Fix the request; do not loop retries.
- **401:** missing, invalid or inactive credentials. Confirm the correct product/account key privately.
- **402:** insufficient balance where used by the endpoint. Check the applicable wallet.
- **403:** package/model permission or policy restriction. A listed model is not universal entitlement.
- **429:** rate limit or temporary capacity restriction. Respect retry instructions and reduce load. Do not assume requests are automatically queued.
- **5xx:** gateway/upstream failure. Use bounded backoff and check status/support.

For interrupted streams, retain request time/reference and reconcile usage before retrying expensive work. A client timeout alone is not proof of a provider outage or an incorrect charge. Send relevant sanitized diagnostics privately to admin; never publish keys or full sensitive prompts.
