# WeizeRouter Architecture Guide

This guide explains how WeizeRouter coordinates routing, token accounting, and failovers.

## System Architecture Flow

```
[User Client] --> [API Gateway (Node.js)] --> [Routing Engine (9Router)] --> [Upstream Provider]
                      | (Check Quota & Logs)
                      v
               [SQLite billing DB]
```

## Key Sanitization

WeizeRouter ensures security by dynamically sanitizing upstream responses before sending them back to clients. Any proprietary upstream token formats or headers are automatically mapped to standardized WeizeRouter responses, keeping the underlying infrastructure confidential.
