# Github_snippets

**Domain**:: #version_control #CLI
**Expertise**:: `⚡️ Intermediate`
**Last Used**:: 2025-05-31
**Related**:: [[Bash_Commands]]
**Tags**:: #cheatsheet #reference #git #github

## Core Syntax & Operations

```bash
# Repository initialization
git init
git clone https://github.com/user/repo.git

# Basic workflow
git add .
git commit -m "Descriptive message"
git push origin main
```

## Productivity Shortcuts

```bash
# Short status
git status -sb

# Quick commit
git commit -am "Quick update"

# Visual log
git log --graph --oneline --all
```

## Common Patterns

### Basic Usage

```bash
# Stage specific changes
git add -p  # Interactive staging

# Undo last commit
git reset --soft HEAD~1

# Fix last commit
git commit --amend
```

### Composite Workflow

```bash
# Feature branch flow
git checkout -b feature
git add .
git commit -m "Implement feature"
git push -u origin feature
gh pr create  # Create GitHub PR
```

## Debugging Guide

```bash
# Recover deleted file
git checkout HEAD -- path/to/file

# Common error:
ERROR: "Updates were rejected"
FIX: "git pull --rebase origin branch"
```

## Real-World Examples

### Collaboration Workflow

```bash
# Fork & PR workflow
gh repo fork user/repo --clone
git checkout -b fix
# Make changes
git push -u origin fix
gh pr create --fill
```

### Release Management

```bash
# Semantic versioning
git tag v1.0.0
git push origin v1.0.0

# Create release
gh release create v1.0.0 --notes "Initial release"
```

## Advanced Techniques

```bash
# Interactive rebase
git rebase -i HEAD~5

# Partial checkout (large repos)
git clone --filter=blob:none --sparse https://github.com/user/repo
git sparse-checkout add dir/subdir
```

## Configuration Snippets

### Minimal Setup

```bash
# ~/.gitconfig essentials
[user]
  name = Your Name
  email = your@email.com
[core]
  editor = nvim
  autocrlf = input
[color]
  ui = auto
```

### Optimized Setup

```bash
# Advanced aliases
[alias]
  co = checkout
  br = branch
  st = status -sb
  lg = log --graph --abbrev-commit --decorate --format=format:'%C(bold blue)%h%C(reset) - %C(bold green)(%ar)%C(reset) %C(white)%s%C(reset) %C(dim white)- %an%C(reset)%C(bold yellow)%d%C(reset)'
```

## Cross-Tool Integration

```bash
# With GitHub CLI
gh issue create
gh repo view --web
gh pr checkout 123

# With difftastic (better diffs)
git config --global diff.tool difftastic
git difftool -x "difft --display=side-by-side"
```

## Version-Specific Notes

| Version | Changes         | Compatibility |
| ------- | --------------- | ------------- |
| 2.23+   | Switch to main  | New repos     |
| 2.30+   | Sparse checkout | Large repos   |

## Pro Tips

```bash
# Search commit history
git log -S "function_name"

# Find when bug was introduced
git bisect start
git bisect bad
git bisect good v1.0
# Test and mark bad/good
git bisect reset
```

> **Remember**: Never force push to shared branches

## Reference Links

1. [Git Official Documentation](https://git-scm.com/doc)
2. [GitHub CLI Docs](https://cli.github.com/)
3. [Advanced Git Techniques](https://github.com/git-tips/tips)

---

### Complete Command Reference

```markdown
## SETUP & CONFIGURATION

git config --global user.name "Name" # Set identity
git config --global user.email "email" # Set email
git config --global core.editor nvim # Set editor

## WORKFLOW FUNDAMENTALS

git status -s # Short status
git add -p # Interactive staging
git commit -m "Message" # Commit changes
git restore --staged file # Unstage file

## BRANCHING & MERGING

git switch -c new-branch # Create and switch
git merge --no-ff feature # Merge with history
git rebase main # Rebase onto main

## HISTORY INSPECTION

git log --oneline # Compact history
git show HEAD~3 # View specific commit
git blame file # Line-by-line history

## COLLABORATION

git fetch --all # Get remote changes
git pull --rebase # Update with rebase
git push --force-with-lease # Safer force push

## GITHUB SPECIFIC

gh pr create # Create pull request
gh issue list # List issues
gh repo clone user/repo # Clone via CLI
```

### GitHub Workflow Patterns

```markdown
1. **Fork Workflow**:
   - Fork repository
   - Clone your fork
   - Create feature branch
   - Push changes
   - Open PR to upstream

2. **Feature Flags**:
   - Use branch-per-feature
   - Merge via PR
   - Cleanup after merge

3. **Release Strategy**:
   - main branch always deployable
   - Tag releases
   - Semantic versioning
```

### .gitignore Templates

```gitignore
# Common ignores
*.log
*.tmp
*.swp
.DS_Store
node_modules/
.env
.venv/
dist/
build/
```

### Danger Zone (⚠️ Use Carefully)

```bash
# Rewrite history (destructive)
git reset --hard HEAD~3

# Force push (only for personal branches)
git push --force
```
