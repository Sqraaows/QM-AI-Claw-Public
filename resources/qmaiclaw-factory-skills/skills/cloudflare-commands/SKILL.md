# Cloudflare Commands

**Source**: Custom workspace skill

Manage Cloudflare DNS, Workers, Pages, and more.

## Setup

```bash
# Install wrangler (Workers CLI)
npm install -g wrangler

# Login
wrangler login

# Config
wrangler whoami
```

## DNS

```bash
# List records
curl -X GET "https://api.cloudflare.com/client/v4/zones/$ZONE_ID/dns_records" \
  -H "Authorization: Bearer $TOKEN" \
  -H "Content-Type: application/json"

# Add record
curl -X POST "https://api.cloudflare.com/client/v4/zones/$ZONE_ID/dns_records" \
  -H "Authorization: Bearer $TOKEN" \
  -H "Content-Type: application/json" \
  -d '{"type":"A","name":"example.com","content":"1.2.3.4"}'
```

## Workers

```bash
# Create project
wrangler generate my-worker

# Deploy
wrangler deploy

# Local dev
wrangler dev

# Secrets
wrangler secret put API_KEY
wrangler secret list

# KV namespace
wrangler kv:namespace create "MY_NAMESPACE"
wrangler kv:key put "key" "value" --namespace-id="..."
```

## Pages

```bash
# Deploy
wrangler pages deploy dist/

# Create project
wrangler pages project create my-site

# List
wrangler pages project list
```

## R2 (S3-compatible storage)

```bash
# Configure in wrangler.toml
# [[r2_buckets]]
# binding = "BUCKET"
# bucket_name = "my-bucket"

# Upload
wrangler r2 object put my-file.txt --file=./my-file.txt

# Download
wrangler r2 object get my-file.txt --file=./downloaded.txt

# List
wrangler r2 object list
```

## Tips

- Get API token from Cloudflare Dashboard > Profile > API Tokens
- Use "Edit zone DNS" template for DNS-only access
- Workers have 10ms CPU time limit (free tier)
- R2 is S3-compatible, use AWS SDK

---

*Install date: 2026-04-27*
