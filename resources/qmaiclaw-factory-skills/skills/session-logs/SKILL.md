# Session Logs

**Source**: https://clawhub.ai/guogang1024/session-logs

Search your complete conversation history stored in session JSONL files.

## Trigger

Use when user asks about prior chats, parent conversations, or historical context.

## Location

Session logs: `~/.clawdbot/agents/<agentId>/sessions/`

- `sessions.json` - Index mapping session keys to IDs
- `.jsonl` - Full transcript per session

## Structure

Each `.jsonl` contains:
- `type`: "session" (metadata) or "message"
- `timestamp`: ISO timestamp
- `message.role`: "user", "assistant", or "toolResult"
- `message.content[]`: Text, thinking, or tool calls
- `message.usage.cost.total`: Cost per response

## Common Queries

### List all sessions by date/size
```bash
for f in ~/.clawdbot/agents/<agentId>/sessions/*.jsonl; do
  date=$(head -1 "$f" | jq -r '.timestamp' | cut -dT -f1)
  size=$(ls -lh "$f" | awk '{print $5}')
  echo "$date $size $(basename $f)"
done | sort -r
```

### Find sessions from specific day
```bash
for f in ~/.clawdbot/agents/<agentId>/sessions/*.jsonl; do
  head -1 "$f" | jq -r '.timestamp' | grep -q "2026-01-06" && echo "$f"
done
```

### Extract user messages
```bash
jq -r 'select(.message.role == "user") | .message.content[]? | select(.type == "text") | .text' <session>.jsonl
```

### Search for keyword in responses
```bash
jq -r 'select(.message.role == "assistant") | .message.content[]? | select(.type == "text") | .text' <session>.jsonl | rg -i "keyword"
```

### Get total cost for session
```bash
jq -s '[.[] | .message.usage.cost.total // 0] | add' <session>.jsonl
```

### Daily cost summary
```bash
for f in ~/.clawdbot/agents/<agentId>/sessions/*.jsonl; do
  date=$(head -1 "$f" | jq -r '.timestamp' | cut -dT -f1)
  cost=$(jq -s '[.[] | .message.usage.cost.total // 0] | add' "$f")
  echo "$date $cost"
done | awk '{a[$1]+=$2} END {for(d in a) print d, "$"a[d]}' | sort -r
```

### Search all sessions for phrase
```bash
rg -l "phrase" ~/.clawdbot/agents/<agentId>/sessions/*.jsonl
```

## Tips

- Sessions are append-only JSONL
- Large sessions can be several MB - use head/tail
- Deleted sessions have `.deleted.` suffix

---

*Install date: 2026-04-27*
