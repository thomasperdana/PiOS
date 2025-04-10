# Terminal Interaction Log

This document logs terminal interactions during the development of the Bible Operating System (PiOS) project.

## Session: Initial Repository Setup - [Current Date]

### Git Repository Initialization
```bash
# Initialize a new Git repository
git init
# Output: Initialized empty Git repository in /Volumes/162TB/PiOS/.git/

# Check repository status
git status
# Output:
# On branch main
# Changes not staged for commit:
#   (use "git add/rm <file>..." to update what will be committed)
#   (use "git restore <file>..." to discard changes in working directory)
# 	deleted:    README.md
# 	deleted:    ROADMAP.md
#
# Untracked files:
#   (use "git add <file>..." to include in what will be committed)
# 	.env
# 	.env.example
#
# no changes added to commit (use "git add" and/or "git commit -a")

# Add files to Git
git add IDEAS.md
git add README.md ROADMAP.md

# Commit files
git commit -m "Initial commit: Add IDEAS.md, README.md, and ROADMAP.md"
# Output:
# [main (root-commit) d188045] Initial commit: Add IDEAS.md, README.md, and ROADMAP.md
#  3 files changed, 88 insertions(+)
#  create mode 100644 IDEAS.md
#  create mode 100644 README.md
#  create mode 100644 ROADMAP.md
```

### Adding Environment Files and Pushing to GitHub
```bash
# Add all files to Git
git add .

# Check status
git status
# Output:
# On branch main
# Changes to be committed:
#   (use "git restore --staged <file>..." to unstage)
# 	new file:   .env
# 	new file:   .env.example
# 	modified:   README.md
# 	modified:   ROADMAP.md
# 	new file:   TerminalLog.md

# Commit changes
git commit -m "Add environment files, update README and ROADMAP, add TerminalLog"
# Output:
# [main 7ca449f] Add environment files, update README and ROADMAP, add TerminalLog
#  5 files changed, 97 insertions(+), 4 deletions(-)
#  create mode 100644 .env
#  create mode 100644 .env.example
#  create mode 100644 TerminalLog.md

# Check for remote repositories
git remote -v
# No output (no remotes configured)

# Find GitHub repository URL from .env file
grep GITHUB_REPO_URL .env
# Output: GITHUB_REPO_URL="https://github.com/thomasperdana/PiOS.git"

# Add GitHub as remote
git remote add origin https://github.com/thomasperdana/PiOS.git

# Set main branch
git branch -M main

# Attempt to push to GitHub (failed due to secrets in .env file)
git push -u origin main
# Output: Push rejected due to GitHub secret scanning protection

# Create .gitignore file to exclude sensitive files
# Added .env to .gitignore

# Remove .env from Git tracking (but keep on disk)
git rm --cached .env
# Output: rm '.env'

# Add .gitignore and commit
git add .gitignore
git commit -m "Add .gitignore and remove .env from tracking"
# Output:
# [main a357d05] Add .gitignore and remove .env from tracking
#  2 files changed, 32 insertions(+), 25 deletions(-)
#  delete mode 100644 .env
#  create mode 100644 .gitignore

# Second push attempt (still failed due to .env in commit history)

# Clean repository history to remove sensitive files
git filter-branch --force --index-filter "git rm --cached --ignore-unmatch .env" --prune-empty --tag-name-filter cat -- --all
# Output: Ref 'refs/heads/main' was rewritten

git filter-branch --force --index-filter "git rm --cached --ignore-unmatch .env.example" --prune-empty --tag-name-filter cat -- --all
# Output: Ref 'refs/heads/main' was rewritten

# Create clean .env.example file
# Added .env.example with placeholder values

# Add and commit clean .env.example
git add .env.example
git commit -m "Add clean .env.example file"
# Output:
# [main cc3c27d] Add clean .env.example file
#  1 file changed, 25 insertions(+)
#  create mode 100644 .env.example
```
