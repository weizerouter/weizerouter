# WeizeRouter FAQ

## General

### What is WeizeRouter?
WeizeRouter is a unified AI routing layer designed for high-performance applications, allowing developers to route requests dynamically to various model backends with unified billing.

### How does dynamic billing work?
Billing is tracked in an internal SQLite database. Every token used is charged against your pre-paid balance. When the balance is depleted, the key is suspended until next top-up.
