# System Monitoring

**Source**: Custom workspace skill

Monitor system resources, logs, and health.

## CPU & Memory

```bash
# Quick overview
top
htop                    # Better (if installed)

# Detailed per process
ps aux --sort=-%cpu | head -20
ps aux --sort=-%mem | head -20

# Memory info
free -h
vmstat 1 5

# CPU info
lscpu
cat /proc/cpuinfo
```

## Disk

```bash
# Disk usage
df -h
du -sh *
du -h --max-depth=1 | sort -h

# I/O stats
iostat -x 1 5
iotop                     # If installed
```

## Network

```bash
# Connections
ss -tulpn
netstat -tulpn

# Bandwidth
nethogs                  # Per process
iftop                    # Per connection

# DNS
dig example.com
nslookup example.com
```

## Process Monitoring

```bash
# Watch process
watch -n 1 'ps aux | grep python'

# Kill by pattern
pkill -f "python script.py"

# Restart if not running
pgrep -f "python script.py" || python script.py &
```

## Log Monitoring

```bash
# Follow logs
tail -f /var/log/syslog
journalctl -f

# Search logs
grep -i error /var/log/syslog
rg -i "error" /var/log/

# Last lines
tail -n 100 /var/log/syslog
```

## System Health

```bash
# Uptime
uptime

# Load average
cat /proc/loadavg

# Temperature (if available)
sensors
vcgencmd measure_temp    # Raspberry Pi
```

## Alerts

```bash
# Disk alert (>80%)
df -h | awk '{print $5 " " $6}' | while read usage mount; do
  pct=${usage%\%}
  [ "$pct" -gt 80 ] && echo "Warning: $mount at $usage"
done

# Memory alert (>90%)
free | awk '/Mem/{printf("Memory: %.2f%%\n"), $3/$2 * 100}'
```

---

*Install date: 2026-04-27*
