# Scheduled Tasks (Cron)

**Source**: Custom workspace skill

Set up automated tasks with cron and OpenClaw cron.

## Cron Format

```
* * * * * 
│ │ │ │ │
│ │ │ │ └── Day of week (0-7, 0/7 = Sunday)
│ │ │ └──── Month (1-12)
│ │ └────── Day of month (1-31)
│ └──────── Hour (0-23)
└────────── Minute (0-59)
```

## Common Examples

| Format | Meaning |
|--------|---------|
| `0 * * * *` | Every hour |
| `*/15 * * * *` | Every 15 minutes |
| `0 0 * * *` | Daily at midnight |
| `0 9 * * 1-5` | Weekdays at 9 AM |
| `0 9 * * *` | Daily at 9 AM |
| `30 2 * * *` | Daily at 2:30 AM |
| `0 0 1 * *` | First of month |
| `0 0 * * 0` | Weekly on Sunday |

## System Cron

```bash
# Edit crontab
crontab -e

# List crontab
crontab -l

# Remove all
crontab -r

# Example
0 9 * * * /path/to/backup.sh
*/15 * * * * /usr/local/bin/health-check.sh
```

## OpenClaw Cron

```bash
# Add cron job
openclaw cron add \
  --name "Daily Backup" \
  --cron "0 2 * * *" \
  --tz "Asia/Shanghai" \
  --session isolated \
  --deliver \
  --message "Run daily backup task"

# List jobs
openclaw cron list

# Remove job
openclaw cron remove "Daily Backup"

# Run now
openclaw cron run "Daily Backup"
```

## Task Ideas

- Daily backup
- Weekly cleanup
- Periodic health checks
- Scheduled reports
- Currency/price monitoring
- News aggregation
- Social media posting

---

*Install date: 2026-04-27*
