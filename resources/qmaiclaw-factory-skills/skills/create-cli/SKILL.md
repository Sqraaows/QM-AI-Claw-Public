---
name: create-cli
description: > Design command-line interface parameters and UX: arguments, flags, subcommands, help text, output formats, error messages, exit codes, prompts, config/env precedence, and safe/dry-run behavior. Use when designing a CLI spec or refactoring an existing CLI.
homepage: https://github.com/openclaw/skills/tree/main/skills/steipete/create-cli
metadata: {"openclaw":{"emoji":"🛠️"}}
---

# Create CLI

Design CLI surface area (syntax + behavior), human-first, script-friendly.

## Do This First

- Read `agent-scripts/skills/create-cli/references/cli-guidelines.md` and apply it as the default rubric.
- Upstream/full guidelines: https://clig.dev/

## Clarify (fast)

Ask, then proceed with best-guess defaults if user is unsure:
- Command name + one-sentence purpose.
- Primary user: humans, scripts, or both.
- Input sources: args vs stdin; files vs URLs; secrets (never via flags).
- Output contract: human text, `--json`, `--plain`, exit codes.
- Interactivity: prompts allowed? need `--no-input`? confirmations for destructive ops?
- Config model: flags/env/config-file; precedence; XDG vs repo-local.
- Platform/runtime constraints: macOS/Linux/Windows; single binary vs runtime.

## Deliverables (what to output)

When designing a CLI, produce a compact spec:
- Command tree + USAGE synopsis.
- Args/flags table (types, defaults, required/optional, examples).
- Subcommand semantics.
- Output rules: stdout vs stderr; TTY detection; `--json`/`--plain`.
- Error + exit code map.
- Safety rules: `--dry-run`, confirmations, `--force`.
- Config/env rules + precedence.
- Shell completion story.
- 5–10 example invocations.

## Default Conventions

- `-h/--help` always shows help and ignores other args.
- `--version` prints version to stdout.
- Primary data to stdout; diagnostics/errors to stderr.
- Add `--json` for machine output; consider `--plain` for stable line-based text.
- Destructive operations: interactive confirmation + non-interactive requires `--force`.
- Respect `NO_COLOR`, `TERM=dumb`; provide `--no-color`.
