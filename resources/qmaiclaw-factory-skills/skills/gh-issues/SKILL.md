---
name: gh-issues
description: Manage GitHub issues via the gh-issues CLI (create, comment, list, search, label, assign, close).
homepage: https://github.com/steipete/gh-issues
metadata: {"openclaw":{"emoji":"🐙","requires":{"bins":["gh-issues"]}}}
---

# gh-issues

Manage GitHub issues from the command line.

## Install

- `go install github.com/steipete/gh-issues/cmd/gh-issues@latest`

## Quick start

- List issues: `gh-issues list --repo owner/repo`
- Create issue: `gh-issues create --repo owner/repo --title "Bug: something is broken" --body "Description"`
- Comment: `gh-issues comment --repo owner/repo 42 --body "Fixed in commit abc123"`
- Close: `gh-issues close --repo owner/repo 42`
- Label: `gh-issues label add --repo owner/repo 42 --label bug`
- Search: `gh-issues search "is:open assignee:@me" --repo owner/repo`

## Notes

- Requires GitHub CLI (`gh`) and `gh auth login`
- Default output is human; use `--json` for scripts