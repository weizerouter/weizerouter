# WeizeRouter Payment & Transaction Pipeline

This guide explains how transactions are processed and credited to user balances.

## Flowchart

```
[User Payment (DANA)] --> [Payment Hook] --> [Verify & Log] --> [Credit Account DB] --> [Key Reactivated]
```

## Verification Rules

All webhook callbacks are signed and checked against transaction hashes before DB records are updated. If a hash mismatch occurs, the transaction is marked as `failed_audit` and sent to PM2 alert monitoring.
