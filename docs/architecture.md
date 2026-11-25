# Public architecture overview

```text
Developer application / editor
             |
      WeizeRouter public API
             |
 Authentication + model/package permission
             |
 Supported model routing and response streaming
             |
 Product-specific usage/accounting
```

Website accounts and Telegram accounts have distinct management surfaces. Regular and Premium balances are separate. Omni, Audio, image, video, Unlimited and adult-only text each have their own product rules; the common brand does not imply a shared key or wallet.

Checkout uses the current payment integration; order confirmation and wallet fulfillment are distinct from merely opening a payment page.

Internal topology, server addresses, account inventory, credentials and implementation configuration are intentionally not documented publicly. This repository is documentation, not the production gateway source.
