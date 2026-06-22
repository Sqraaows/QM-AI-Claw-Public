# Code Search

**Source**: Custom workspace skill

Search code across your projects using grep, ripgrep, and sourcegraph.

## ripgrep (rg)

```bash
# Basic search
rg "search term"

# Case insensitive
rg -i "search term"

# Whole word match
rg -w "functionName"

# Show line numbers
rg -n "pattern"

# Only show matches (no context)
rg -o "pattern"

# Files with matches
rg -l "pattern"

# Files without matches
rg -L "pattern"

# File type (js, ts, py, etc)
rg -t js "pattern"

# Glob patterns
rg "pattern" --glob "*.md"

# Count matches
rg -c "pattern"

# Context lines
rg -A 2 -B 2 "pattern"  # After/Before

# JSON output
rg --json "pattern"
```

## Search in Specific Locations

```bash
# Current directory
rg "pattern" .

# Specific path
rg "pattern" /path/to/project

# Exclude directories
rg "pattern" --ignore-dir node_modules --ignore-dir .git

# Only certain files
rg "pattern" "**/*.ts" "**/*.tsx"
```

## Git Search

```bash
# Search in git diffs
git log -p -S "pattern"
git log -p --grep="pattern"

# Search staged files
git diff --staged -S "pattern"

# Blame
git blame file.ts | rg "pattern"
```

## Tips

- Use `-F` for fixed string (faster)
- Use `--no-ignore` to search ignored files
- Use `--hidden` to search hidden files
- Combine with `xargs` for batch operations

---

*Install date: 2026-04-27*
