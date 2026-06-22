---
name: gh-workflow-gpt
description: Analyze GitHub Actions workflows with AI to find failure root causes and suggest fixes.
homepage: https://github.com/steipete/gh-workflow-gpt
metadata: {"openclaw":{"emoji":"🤖","requires":{"bins":["gh-workflow-gpt"],"env":["OPENAI_API_KEY"]}}}
---

# gh-workflow-gpt

Analyze GitHub Actions workflow failures with AI.

## Install

- `go install github.com/steipete/gh-workflow-gpt/cmd/gh-workflow-gpt@latest`

## Quick start

- Analyze run: `gh-workflow-gpt analyze <run-id> --repo owner/repo`
- Explain failure: `gh-workflow-gpt explain <run-url>`
- JSON output: `gh-workflow-gpt analyze <run-id> --repo owner/repo --json`

## Notes

- Requires `OPENAI_API_KEY` env var
- Works best with failed workflow runs