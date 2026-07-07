# WeizeRouter Operations Manual

Operational runbooks for maintaining WeizeRouter instances.

## Service Status Check

To check the active server instances via PM2:
```bash
pm2 list
```

To view real-time log outputs:
```bash
pm2 logs weizerouter-bot
```

## Database Backups

SQLite databases are backed up automatically every day at midnight. Daily snapshots are saved under `/var/backups/weizerouter/`.
