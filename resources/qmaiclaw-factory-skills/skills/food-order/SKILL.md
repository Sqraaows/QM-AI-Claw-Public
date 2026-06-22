---
name: food-order
description: Reorder Foodora orders + track ETA/status with ordercli. Triggers: order food, reorder, track ETA. Never confirm without explicit user approval.
homepage: https://ordercli.sh
metadata: {"openclaw":{"emoji":"🥡","requires":{"bins":["ordercli"]}}}
---

# Food order (Foodora via ordercli)

Goal: reorder a previous Foodora order safely (preview first; confirm only on explicit user "yes/confirm/place the order").

## Hard Safety Rules

- Never run `ordercli foodora reorder ... --confirm` unless user explicitly confirms.
- Prefer preview-only steps first; show what will happen; ask for confirmation.
- If user is unsure: stop at preview and ask questions.

## Setup (once)

- Country: `ordercli foodora countries` → `ordercli foodora config set --country AT`
- Login: `ordercli foodora login --email you@example.com --password-stdin`
- Or via Chrome session: `ordercli foodora session chrome --url https://www.foodora.at/ --profile "Default"`

## Find What to Reorder

- Recent list: `ordercli foodora history --limit 10`
- Details: `ordercli foodora history show <orderCode>`
- JSON format: `ordercli foodora history show <orderCode> --json`

## Preview Reorder (no cart changes)

- `ordercli foodora reorder <orderCode>`

## Place Reorder (cart change; explicit confirmation required)

- `ordercli foodora reorder <orderCode> --confirm`
- Multiple addresses? Ask for `--address-id` then run:
  - `ordercli foodora reorder <orderCode> --confirm --address-id <id>`

## Track the Order

- ETA/status: `ordercli foodora orders`
- Live updates: `ordercli foodora orders --watch`
- Single order: `ordercli foodora order <orderCode>`

## Debug / Safe Testing

- Use a throwaway config: `ordercli --config /tmp/ordercli.json ...`