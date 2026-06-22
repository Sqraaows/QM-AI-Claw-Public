---
name: notion-qa
description: Ask questions over a Notion workspace and get AI-powered answers with citations. Use when user wants to query their Notion workspace with natural language.
homepage: https://github.com/steipete/notion-qa
metadata: {"openclaw":{"emoji":"🧠","requires":{"bins":["notion-qa"],"env":["NOTION_KEY"]}}}
---

# notion-qa

Ask questions over a Notion workspace using AI.

## Install

- `go install github.com/steipete/notion-qa/cmd/notion-qa@latest`

## Setup

```bash
export NOTION_KEY="your-notion-api-key"
```

## Quick start

- Ask: `notion-qa ask "What was the decision made in last week's sprint retrospective?"`
- JSON output: `notion-qa ask "..." --json`

## Notes

- May take 10–20 seconds for first query (embedding computation)
- Requires `NOTION_KEY` with access to target pages