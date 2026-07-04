# Operations

This document explains the general operation model of WeizeRouter.

## Runtime Components

- Telegram bot service
- Web platform service
- API gateway service
- Payment webhook endpoint
- Admin notification service

## Process Management

WeizeRouter uses PM2 to manage long-running Node.js services.

## Reverse Proxy

Nginx is used as a reverse proxy for public HTTPS routing.

## Monitoring

Important things to monitor:

- payment webhook success
- API gateway health
- provider availability
- user package activation
- transaction status
- usage and fair-use events
- service logs

## Backup

Important data should be backed up regularly:

- database
- configuration
- package data
- transaction records

Secrets should never be published in public repositories.
