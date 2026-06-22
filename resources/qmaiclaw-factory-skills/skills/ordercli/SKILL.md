---
name: ordercli
description: Check past Foodora orders and track active order status via ordercli CLI.
homepage: https://ordercli.sh
metadata: {"openclaw":{"emoji":"🛵","requires":{"bins":["ordercli"]}}}
---

# ordercli

Use `ordercli` to check past orders and track active order status (Foodora only right now).

## Quick start (Foodora)

- `ordercli foodora countries`
- `ordercli foodora config set --country AT`
- `ordercli foodora login --email you@example.com --password-stdin`
- `ordercli foodora orders`
- `ordercli foodora history --limit 20`
- `ordercli foodora history show <orderCode>`

## Active Orders

- List active: `ordercli foodora orders`
- Watch live: `ordercli foodora orders --watch`
- Detail: `ordercli foodora order <orderCode>`
- History detail JSON: `ordercli foodora history show <orderCode> --json`

## Reorder (adds to cart)

- Preview: `ordercli foodora reorder <orderCode>`
- Confirm: `ordercli foodora reorder <orderCode> --confirm`
- With address: `ordercli foodora reorder <orderCode> --confirm --address-id <id>`

## Notes

- Always confirm before reorder or cart-changing actions
- Use `--config /tmp/ordercli.json` for testing