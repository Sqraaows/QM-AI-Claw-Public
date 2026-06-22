# Git Commands

**Source**: Custom workspace skill

Common Git commands and workflows.

## Setup

```bash
git config --global user.name "Your Name"
git config --global user.email "your@email.com"
git config --global core.editor vim
git config --global alias.st status
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.lg "log --oneline --graph --decorate"
```

## Daily Workflow

```bash
# Check status
git status
git st

# Add changes
git add file.txt           # Single file
git add .                  # All changes
git add -p                 # Interactive patch

# Commit
git commit -m "message"
git commit -am "message"   # Add + commit tracked files
git commit --amend         # Modify last commit

# Push
git push origin main
git push -u origin feature # Set upstream
```

## Branching

```bash
# List branches
git branch                 # Local
git branch -a              # All (local + remote)
git branch -r              # Remote only

# Create/switch
git branch new-feature
git checkout new-feature
git switch new-feature    # New Git
git checkout -b new-feat   # Create + switch

# Merge
git merge feature-branch
git merge --no-ff feature # No fast-forward

# Delete
git branch -d feature      # Safe delete
git branch -D feature      # Force delete
```

## Inspect

```bash
# Log
git log
git log --oneline
git log --graph --oneline --all
git log -p file.txt        # File history
git log --author="name"
git log --since="2 weeks"

# Diff
git diff                   # Working tree vs staging
git diff --staged          # Staging vs last commit
git diff HEAD~1            # vs previous commit
git diff branch1..branch2

# Blame
git blame file.txt
git blame -L 10,20 file.txt
```

## Undo

```bash
# Unstage
git reset HEAD file.txt
git reset .

# Revert to last commit (keep changes)
git checkout -- file.txt

# Reset (hard = delete changes)
git reset --soft HEAD~1    # Keep in staging
git reset --mixed HEAD~1   # Keep in working tree
git reset --hard HEAD~1    # Delete changes

# Revert a commit (safe)
git revert abc123
```

## Stash

```bash
git stash                  # Save changes
git stash pop              # Apply + delete
git stash apply           # Apply, keep stash
git stash list            # Show stashes
git stash drop            # Delete stash
git stash clear           # Delete all
```

## Remote

```bash
git remote -v
git remote add origin url
git remote remove origin
git fetch origin
git pull origin main
git pull --rebase origin main
```

## Tags

```bash
git tag v1.0.0
git tag -a v1.0.0 -m "Release"
git push origin v1.0.0
git tag -d v1.0.0           # Delete local
git push origin --delete v1.0.0  # Delete remote
```

## Tips

- Use `git lg` alias for pretty log
- `git commit -v` shows diff in editor
- `git add -u` stages only tracked files
- Use `.gitignore` to exclude files

---

*Install date: 2026-04-27*
