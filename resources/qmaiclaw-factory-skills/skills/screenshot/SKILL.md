---
name: screenshot
description: Take high-quality screenshots of URLs with the screenshot CLI, supporting retina displays and various output formats.
homepage: https://screenshot-cli.sh
metadata: {"openclaw":{"emoji":"📸","requires":{"bins":["screenshot"]}}}
---

# screenshot

Take high-quality screenshots from the command line.

## Install

- `go install github.com/steipete/screenshot/cmd/screenshot@latest`

## Quick start

- Basic: `screenshot https://example.com`
- Full page: `screenshot https://example.com --full-page`
- Retina: `screenshot https://example.com --retina`
- Output: `screenshot https://example.com -o screenshot.png`

## Options

- `--full-page` — capture entire scrollable page
- `--retina` — high-DPI screenshot
- `--wait <ms>` — wait before capture
- `-o, --output <path>` — output file path
- `--format png|jpg` — output format

## Notes

- Requires a browser to be installed
- Use `--wait` for pages that need JavaScript rendering