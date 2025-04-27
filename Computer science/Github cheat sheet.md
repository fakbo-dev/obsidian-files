Here's the reformatted version with consistent syntax and organization:

## SETUP & CONFIGURATION  
### User Identity  
```bash  
git config --global user.name "[Firstname Lastname]"  
# Set identifiable name for commit attribution  

git config --global user.email "[valid-email]"  
# Set email associated with commits  

git config --global color.ui auto  
# Enable colored terminal output  
```

### Repository Setup  
```bash  
git init  
# Initialize new local repository  

git clone [url]  
# Clone existing repository from URL  
```

---

## WORKFLOW FUNDAMENTALS  
### Staging & Committing  
```bash  
git status  
# Show modified/staged files  

git add [file]  
# Stage specific file  

git add .  
# Stage all changes  

git reset [file]  
# Unstage file while keeping changes  

git commit -m "[Descriptive message]"  
# Commit staged changes  
```

### Changes Inspection  
```bash  
git diff  
# Show unstaged changes  

git diff --staged  
# Show staged changes  

git diff branchB..branchA  
# Compare branches  
```

---

## BRANCHING & MERGING  
```bash  
git branch  
# List branches (* = current)  

git branch [branch-name]  
# Create new branch  

git checkout [branch-name]  
# Switch branches  

git merge [branch-name]  
# Merge branch into current  

git rebase [branch]  
# Reapply commits on top of another branch  
```

---

## HISTORY & INSPECTION  
```bash  
git log  
# Show commit history  

git log --stat -M  
# Show history with file stats  

git log --follow [file]  
# Track file through renames  

git log branchB..branchA  
# Show branch-exclusive commits  

git show [SHA]  
# Display specific commit details  
```

---

## COLLABORATION  
```bash  
git remote add [alias] [url]  
# Add remote repository  

git fetch [alias]  
# Download remote changes  

git push [alias] [branch]  
# Upload local commits  

git pull  
# Fetch + merge remote changes (≡ fetch + merge)  
```

---

## FILE MANAGEMENT  
```bash  
git rm [file]  
# Delete file and stage removal  

git mv [old] [new]  
# Rename/move file and stage change  
```

---

## IGNORING FILES  
### .gitignore Patterns  
```gitignore  
logs/  
*.notes  
pattern*/  
```

### Global Ignore  
```bash  
git config --global core.excludesfile [file]  
# Set system-wide ignore patterns  
```

---

## TEMPORARY CHANGES  
```bash  
git stash  
# Save working directory changes  

git stash list  
# List stashed changes  

git stash pop  
# Restore most recent stash  

git stash drop  
# Discard most recent stash  
```

---

## HISTORY REWRITING  
```bash  
git reset --hard [commit]  
# Reset to specific commit (⚠️ destructive!)  

git commit --amend  
# Modify last commit  
```

This version features:  
1. Consistent command formatting  
2. Logical section grouping  
3. Clear hierarchy with --- separators  
4. Syntax highlighting for code blocks  
5. Concise explanations  
6. Warning emojis for dangerous operations  
7. Standardized bash syntax formatting