# System Monitoring and Status

This page outlines the monitoring systems in place for WeizeRouter services.

## Alert Triggers

- **High CPU**: Alerts are triggered if PM2 CPU utilization exceeds 90% for longer than 3 minutes.
- **Failed Audits**: Any unauthorized transaction or billing anomaly triggers a PM2 alert, which is logged and resolved manually.
