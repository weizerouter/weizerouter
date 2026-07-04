# Payment Flow

WeizeRouter uses automated QRIS payment.

## User Flow

1. User opens the Telegram bot
2. User clicks Beli Paket
3. User selects a package
4. Bot generates a QRIS invoice
5. User scans QRIS and pays
6. Payment provider sends webhook confirmation
7. System activates package automatically
8. API key is delivered instantly

## No Manual Proof Required

Users do not need to send payment screenshots or proof manually.

The system confirms payment automatically through webhook.

## Example Payment Status

- pending_payment
- paid
- cancelled
- expired
- failed

## Benefits

- faster activation
- less admin work
- fewer manual errors
- better user experience
- real-time API key delivery
