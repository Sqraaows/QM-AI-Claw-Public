# API Testing

**Source**: Custom workspace skill

Test REST APIs with curl, httpie, and other tools.

## curl

```bash
# GET
curl https://api.example.com/users

# POST
curl -X POST https://api.example.com/users \
  -H "Content-Type: application/json" \
  -d '{"name":"John","email":"john@example.com"}'

# PUT
curl -X PUT https://api.example.com/users/1 \
  -H "Content-Type: application/json" \
  -d '{"name":"Jane"}'

# DELETE
curl -X DELETE https://api.example.com/users/1

# With headers
curl -H "Authorization: Bearer TOKEN" \
     -H "Accept: application/json" \
     https://api.example.com/protected

# Authentication
curl -u user:pass https://api.example.com
curl --basic -u user:pass https://api.example.com

# Save response
curl -o response.json https://api.example.com/data

# Follow redirects
curl -L https://api.example.com

# Verbose
curl -v https://api.example.com
curl --verbose https://api.example.com
```

## httpie (Recommended)

```bash
# Install
pip install httpie

# GET
http GET api.example.com/users

# POST
http POST api.example.com/users name="John" email="john@example.com"

# PUT
http PUT api.example.com/users/1 name="Jane"

# DELETE
http DELETE api.example.com/users/1

# With auth
http GET api.example.com/protected Authorization:"Bearer TOKEN"

# Headers
http GET api.example.com Accept:application/json

# Download file
http --download api.example.com/file
```

## jq (JSON processing)

```bash
# Pretty print
curl -s api.example.com/users | jq .

# Get field
curl -s api.example.com/users | jq '.[0].name'

# Filter
curl -s api.example.com/users | jq '.[] | select(.active==true)'

# Map
curl -s api.example.com/users | jq 'map(.email)'

# Parse
curl -s api.example.com/data | jq -r '.result'
```

## Postman/cURL Import

```bash
# Export from Postman as cURL, then use:
# curl -k --location 'https://api.example.com' \
#   --header 'Content-Type: application/json' \
#   --data '{"key":"value"}'
```

## Tips

- Use `-s` (curl) or `httpie` for cleaner output
- `--insecure` or `-k` bypasses SSL verification (dev only)
- `-w "%{http_code}"` shows status code
- Use `http --session` for persistent cookies

---

*Install date: 2026-04-27*
