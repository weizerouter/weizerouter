# Payments and order flow

**Looking for the merchant product?** See [WeizePay](weizepay.md). This page describes purchasing ecosystem products through checkout, not WeizePay merchant onboarding.

Current public payment integration uses **Midtrans**. The old Pakasir-only QRIS description is historical, not the current purchase guide.

## Website

1. Sign in at https://weizerouter.com/.
2. Select the desired product and package in that account.
3. Review token allocation, product-specific balance, IDR amount and terms.
4. Choose an available payment method in checkout.
5. Complete payment, then check the invoice status and corresponding wallet.

## Telegram

1. Open https://t.me/WeizeRouterBot and choose the package.
2. Select a payment method first.
3. For QRIS, use the QR image displayed in the bot chat. For bank/card flows, follow the selected invoice payment page.
4. Check payment/order status in the same bot account.

Available options may include QRIS, GoPay, Mandiri Bill, eligible bank Virtual Accounts, Visa and Mastercard. Availability depends on product, invoice limits, bank and provider authorization. All settlement is in **IDR**; other currencies displayed are estimates.

A checkout page, successful HTTP request or QR image alone does not prove payment settled or balance credited. If a debit occurred but the order remains pending, contact admin with the invoice/reference and time; never post banking credentials publicly.

Do not pay stale invoices or create duplicate payments to fix a display delay. Keep manual and partially paid arrangements truthful; they are not automatic provider settlements.
