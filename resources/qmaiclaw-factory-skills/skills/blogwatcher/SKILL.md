# Blogwatcher

**Source**: https://clawhub.ai/steipete/blogwatcher

Monitor blogs and RSS/Atom feeds for updates using the blogwatcher CLI.

## Installation

```bash
# Install via Go
go install github.com/Hyaxia/blogwatcher/cmd/blogwatcher@latest
```

## Usage

```bash
# Add a feed to monitor
blogwatcher add "https://example.com/feed.xml"

# Scan all feeds for updates
blogwatcher scan

# List all monitored feeds
blogwatcher list

# Read a specific feed entry
blogwatcher read <feed-id>

# Remove a feed
blogwatcher remove <feed-id>
```

## Setup Cron for Auto-Scan

```bash
# Add to cron for periodic checks
openclaw cron add \
  --name "Blog Updates" \
  --cron "0 */6 * * *" \
  --session isolated \
  --deliver \
  --message "Run blogwatcher scan and report new posts"
```

## Tips

- Use with RSS/Atom feeds from blogs, news sites, newsletters
- Set up periodic scans to get notified of new content
- Works well with openclaw's cron system

---

*Install date: 2026-04-27*
