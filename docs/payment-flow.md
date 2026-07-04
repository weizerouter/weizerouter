# Payment Flow

WeizeRouter uses fully automated QRIS payment via Pakasir payment gateway. No manual approval or payment proof submission required.

---

## Overview

The payment flow is **completely automated** from order to API key delivery:

1. User selects package
2. QRIS invoice generated
3. User pays via QRIS
4. Webhook confirms payment
5. Package activated instantly
6. API key delivered to user

**Total time:** 5-10 seconds from payment to API key delivery

---

## Step-by-Step Flow

### Step 1: User Selects Package

**Channels:**
- Telegram Bot: [@WeizeRouterBot](https://t.me/WeizeRouterBot)
- Website: [https://weizerouter.web.id/dashboard](https://weizerouter.web.id/dashboard)

User chooses from available packages:
- Mini Trial (Rp 600 / 2 Hours)
- Trial (Rp 2.000 / 1 Day)
- Pro (Rp 7.000 / 1 Day)
- Ultimate (Rp 15.000 / 1 Day)

---

### Step 2: QRIS Invoice Generated

**Process:**
1. WeizeRouter sends request to Pakasir API
2. Pakasir generates dynamic QRIS invoice
3. QR code image URL returned to WeizeRouter
4. Invoice displayed to user via Telegram Bot or Website

**Invoice Details:**
- Unique transaction ID
- Package name and price
- QR code for scanning
- Expiry time (typically 30 minutes)

---

### Step 3: User Pays via QRIS

**Supported Payment Methods:**
- GoPay
- OVO
- DANA
- ShopeePay
- LinkAja
- Bank apps with QRIS support
- Any Indonesian e-wallet with QRIS

**User Actions:**
1. Open any supported e-wallet app
2. Scan the QR code
3. Confirm payment
4. Payment processed instantly

---

### Step 4: Webhook Confirms Payment

**Automated Process:**
1. User completes payment in e-wallet
2. Pakasir receives payment confirmation from payment processor
3. Pakasir sends webhook POST request to WeizeRouter webhook endpoint
4. WeizeRouter validates webhook signature
5. WeizeRouter confirms transaction ID matches pending order

**Webhook Payload Example:**
```json
{
  "transaction_id": "TRX123456",
  "status": "paid",
  "amount": 15000,
  "timestamp": "2026-07-05T12:34:56Z"
}
```

**Security:**
- Webhook signature validation
- Transaction ID verification
- Amount verification
- Idempotency checks (prevents duplicate activation)

---

### Step 5: Package Activated Instantly

**Activation Process:**
1. WeizeRouter receives webhook confirmation
2. Database updated with package activation:
   - `user_id` → package tier updated
   - `expiry_time` → calculated based on package duration
   - `api_key` → generated if new user, or existing key extended
   - `transaction_log` → recorded for admin monitoring
3. Admin notification sent via Telegram

**Database Update:**
- User package tier: `mini_trial`, `trial`, `pro`, or `ultimate`
- Expiry time: Current time + package duration
- API key status: `active`
- Model access: Updated based on package tier

**Timing:** Database update completes in <1 second

---

### Step 6: API Key Delivered to User

**Delivery Method:**
- **Telegram Bot:** API key sent as direct message to user
- **Website:** API key displayed in dashboard, success notification shown

**API Key Format:**
```
wzr_live_XXXXXXXX
```

**Message Content:**
- API key value
- Package tier activated
- Expiry time
- Quick start guide link
- API endpoint URL

**Example Telegram Message:**
```
✅ Payment confirmed!

Your Ultimate package is now active.

API Key: wzr_live_abc123xyz

Expiry: 2026-07-06 12:34:56 WIB

Use this API key at:
https://weizerouter.web.id/v1

Documentation:
https://github.com/weizerouter/weizerouter/tree/main/docs
```

---

## Error Handling

### Payment Failed
- User notified via Telegram/Website
- Invoice marked as expired
- No charge applied
- User can retry with new invoice

### Webhook Timeout
- Retry mechanism (Pakasir retries webhook 3 times)
- Manual admin verification if webhook fails
- User contacted for support

### Duplicate Payment
- Idempotency check prevents double activation
- Second payment refunded automatically
- User notified

---

## Admin Monitoring

**Real-time Notifications:**
- Admin receives Telegram notification for every successful transaction
- Notification includes:
  - User ID
  - Package purchased
  - Amount paid
  - Transaction timestamp

**Admin Dashboard:**
- Transaction history
- Payment status tracking
- Failed payment logs
- Revenue analytics

---

## Payment Security

**Security Measures:**
1. **Webhook Signature Validation** — Ensures webhook is from Pakasir
2. **HTTPS Only** — All communication encrypted
3. **Transaction ID Verification** — Prevents replay attacks
4. **Amount Verification** — Confirms payment matches package price
5. **Idempotency** — Prevents duplicate activation
6. **Rate Limiting** — Prevents abuse

**Data Privacy:**
- WeizeRouter does NOT store:
  - User payment card details
  - E-wallet account information
  - Bank account details
- Only transaction metadata stored (amount, timestamp, status)

---

## Frequently Asked Questions

**Q: How long does payment take?**  
A: 5-10 seconds from payment confirmation to API key delivery.

**Q: What if payment fails?**  
A: You'll be notified immediately. Try again with a new invoice. No charge applied for failed payments.

**Q: Can I pay with credit card?**  
A: QRIS supports payment via any Indonesian e-wallet. Some e-wallets support credit card top-up.

**Q: What if I don't receive API key after payment?**  
A: Contact support via [@WeizeRouterBot](https://t.me/WeizeRouterBot). Admin can manually verify and activate.

**Q: Can I get a refund?**  
A: Refunds are handled case-by-case. Contact admin via Telegram.

---

## Technical Details

**Pakasir Integration:**
- API Version: Latest
- Webhook Endpoint: `https://weizerouter.web.id/webhook/pakasir`
- Invoice Expiry: 30 minutes
- Retry Policy: 3 attempts with exponential backoff

**WeizeRouter Webhook Processing:**
- Timeout: 10 seconds
- Queue: Background job processing
- Logging: All webhooks logged for audit
- Monitoring: Real-time webhook health monitoring

---

## Support

Payment issues? Contact:
- Telegram Bot: [@WeizeRouterBot](https://t.me/WeizeRouterBot)
- LinkedIn: [Wang Weize](https://www.linkedin.com/in/weize-wang-4262b7406)

---

**Last Updated:** July 2026
