# Himalaya Email CLI

**Source**: https://clawhub.ai/lamelas/himalaya

CLI email client for managing emails via IMAP, SMTP, Notmuch, or Sendmail.

## Installation

```bash
# via cargo (Rust)
cargo install himalaya

# via brew
brew install himalaya
```

## Configuration

Run interactive wizard:
```bash
himalaya account configure
```

Or create `~/.config/himalaya/config.toml`:
```toml
[accounts.personal]
email = "you@example.com"
display-name = "Your Name"
default = true

backend.type = "imap"
backend.host = "imap.example.com"
backend.port = 993
backend.encryption.type = "tls"
backend.login = "you@example.com"
backend.auth.type = "password"
backend.auth.cmd = "pass show email/imap"

message.send.backend.type = "smtp"
message.send.backend.host = "smtp.example.com"
message.send.backend.port = 587
message.send.backend.encryption.type = "start-tls"
message.send.backend.login = "you@example.com"
message.send.backend.auth.type = "password"
message.send.backend.auth.cmd = "pass show email/smtp"
```

## Common Operations

### List / Search
```bash
himalaya folder list                    # List folders
himalaya envelope list                   # List emails in INBOX
himalaya envelope list --folder "Sent"  # List sent
himalaya envelope list --output json     # JSON output
himalaya envelope list from john subject meeting  # Search
```

### Read / Reply / Forward
```bash
himalaya message read 42                 # Read email by ID
himalaya message reply 42               # Reply
himalaya message reply 42 --all          # Reply all
himalaya message forward 42             # Forward
```

### Write / Send
```bash
himalaya message write                  # Interactive compose
himalaya message write -H "To:to@example.com" -H "Subject:Hi" "Body"
```

### Move / Copy / Delete
```bash
himalaya message move 42 "Archive"
himalaya message copy 42 "Important"
himalaya message delete 42
```

### Attachments
```bash
himalaya attachment download 42
himalaya attachment download 42 --dir ~/Downloads
```

## Multiple Accounts
```bash
himalaya account list
himalaya --account work envelope list
```

## Tips

- Store passwords securely using `pass` or system keyring
- Use `--output json` for programmatic access
- Message IDs are relative to current folder

---

*Install date: 2026-04-27*
