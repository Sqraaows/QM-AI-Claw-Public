---
name: gh-stars
description: List, search, and manage GitHub starred repositories with the gh-stars CLI.
homepage: https://github.com/steipete/gh-stars
metadata: {"openclaw":{"emoji":"⭐","requires":{"bins":["gh-stars"]}}}
---

# gh-stars

Manage your GitHub starred repositories.

## Install

- `go install github.com/steipete/gh-stars/cmd/gh-stars@latest`

## Quick start

- List: `gh-stars list`
- Search: `gh-stars search "rust"` or `gh-stars search "python tensorflow"`
- Add tag: `gh-stars tag add "machine-learning" --repo owner/repo`
- Remove tag: `gh-stars tag remove "python" --repo owner/repo`
- List tags: `gh-stars tags`

## Notes

- Auth: `gh auth login` (stars are per-user)
- Default output is human; use `--json` for scripts