# WeizeRouter Error Codes Reference

This document outlines common error responses returned by the WeizeRouter API.

## HTTP Status Codes

- `400 Bad Request`: Missing mandatory parameters or invalid JSON body.
- `401 Unauthorized`: Invalid or expired API token.
- `402 Payment Required`: Account quota exceeded. Top-up is required to continue.
- `429 Too Many Requests`: Rate limit hit for the current tier.
- `500 Internal Server Error`: An error occurred upstream. Auto-failover is triggered if configured.
