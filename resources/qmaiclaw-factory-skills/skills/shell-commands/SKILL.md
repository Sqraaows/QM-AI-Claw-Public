# Shell Commands

**Source**: Custom workspace skill

Common shell commands and patterns for productivity.

## File Operations

```bash
# List files
ls -la              # Detailed list
ls -lh              # Human readable sizes
ls -lt              # Sort by time
ls -lS              # Sort by size
ls -a               # Include hidden

# Navigate
cd ~                # Home
cd -                # Previous directory
pushd /path         # Save and cd
popd                # Return to saved

# Copy/Move
cp file dir/        # Copy
cp -r dir dir2/    # Copy recursively
mv file dir/        # Move
mv oldname newname  # Rename

# Remove
rm file             # Delete file
rm -rf dir/         # Delete recursively
trash file          # Move to trash (recoverable)
```

## Search

```bash
# Find files
find . -name "*.txt"
find . -type d -name "node_modules"
find /path -mtime -7  # Modified in 7 days

# Find by content
grep -r "pattern" .
rg "pattern" .        # ripgrep (faster)

# Locate
locate filename
updatedb              # Update locate database
```

## Process

```bash
# List processes
ps aux               # All processes
ps aux | rg python   # Filter

# Top processes
htop                 # Interactive
top                  # Standard

# Kill process
kill PID             # Graceful
kill -9 PID          # Force kill
pkill -f "name"      # Kill by name
```

## Network

```bash
# Check ports
netstat -tulpn       # Listening ports
lsof -i :8080        # What's using port 8080

# Ping
ping example.com

# Curl
curl -I url          # Headers only
curl -s url | jq .   # JSON response

# SSH
ssh user@host
ssh -i key.pem user@host
ssh -L 8080:local:80 user@host  # Tunnel
```

## Disk Usage

```bash
df -h                # Disk space
du -sh dir/          # Directory size
du -h --max-depth=1  # Size per subdir
ncdu                 # Interactive disk analyzer
```

## Archives

```bash
# Extract
tar -xvf file.tar.gz
unzip file.zip
gunzip file.gz

# Create
tar -cvf archive.tar dir/
zip -r archive.zip dir/
```

## System

```bash
# OS info
uname -a
cat /etc/os-release
sw_vers              # macOS

# Resources
free -h              # Memory
uptime               # Load
whoami               # Current user
```

---

*Install date: 2026-04-27*
