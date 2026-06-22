---
name: bear-notes
description: Create, search, and manage Bear notes via grizzly CLI on macOS.
homepage: https://bear.app
metadata: {"clawdbot":{"emoji":"🐻","os":["darwin"],"requires":{"bins":["grizzly"]},"install":[{"id":"go","kind":"go","module":"github.com/tylerwince/grizzly/cmd/grizzly@latest","bins":["grizzly"],"label":"Install grizzly (go)"}]}}
---

# Bear Notes

Use `grizzly` to create, read, and manage notes in Bear on macOS.

## Requirements

- Bear app installed and running
- For some operations (add-text, tags, open-note --selected), a Bear app token (stored in `~/.config/grizzly/token`)

## Getting a Bear Token

1. Open Bear → Help → API Token → Copy Token
2. Save it: `echo "YOUR_TOKEN" > ~/.config/grizzly/token`

## Common Commands

- Create: `echo "Note content here" | grizzly create --title "My Note" --tag work`
- Open/read by ID: `grizzly open-note --id "NOTE_ID" --enable-callback --json`
- Append text: `echo "More content" | grizzly add-text --id "NOTE_ID" --mode append --token-file ~/.config/grizzly/token`
- List tags: `grizzly tags --enable-callback --json --token-file ~/.config/grizzly/token`
- Search via tag: `grizzly open-tag --name "work" --enable-callback --json`

## Options

- `--dry-run` — Preview the URL without executing
- `--print-url` — Show the x-callback-url
- `--enable-callback` — Wait for Bear's response
- `--json` — Output as JSON
- `--token-file PATH` — Path to Bear API token file

## Notes

- Bear must be running for commands to work
- Note IDs are Bear's internal IDs
- macOS only