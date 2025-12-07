# GitHub Practice Guide

This guide contains step-by-step instructions for practicing GitHub workflows using Cursor IDE, from connecting to committing and saving changes.

## Table of Contents

1. [Connecting to GitHub](#1-connecting-to-github)
2. [Creating a Repository](#2-creating-a-repository)
3. [Cloning a Repository](#3-cloning-a-repository)
4. [Creating a Branch](#4-creating-a-branch)
5. [Switching Between Branches](#5-switching-between-branches)
6. [Making Changes](#6-making-changes)
7. [Staging Changes](#7-staging-changes)
8. [Committing Changes](#8-committing-changes)
9. [Pushing to GitHub](#9-pushing-to-github)
10. [Pulling from GitHub](#10-pulling-from-github)
11. [Viewing Commit History](#11-viewing-commit-history)
12. [Creating a Pull Request](#12-creating-a-pull-request)
13. [Merging Branches](#13-merging-branches)
14. [Resolving Merge Conflicts](#14-resolving-merge-conflicts)
15. [Reverting Changes](#15-reverting-changes)

---

## 1. Connecting to GitHub

### Step-by-Step:

1. **Open Cursor Settings**
   - Press `Cmd + ,` (Mac) or `Ctrl + ,` (Windows/Linux)
   - Or go to `Cursor` → `Settings`

2. **Search for GitHub**
   - In the settings search bar, type "GitHub"

3. **Sign in to GitHub**
   - Click on "Sign in with GitHub"
   - A browser window will open
   - Authorize Cursor to access your GitHub account
   - You'll be redirected back to Cursor

4. **Verify Connection**
   - Check the bottom-left corner of Cursor
   - You should see your GitHub username or avatar

---

## 2. Creating a Repository

### Option A: Create Repository on GitHub.com

1. **Go to GitHub.com**
   - Navigate to [github.com](https://github.com)
   - Sign in to your account

2. **Create New Repository**
   - Click the "+" icon in the top-right corner
   - Select "New repository"

3. **Configure Repository**
   - Enter a repository name
   - Add a description (optional)
   - Choose public or private
   - **Don't** initialize with README (we'll do this locally)
   - Click "Create repository"

4. **Connect Local Folder to Repository**
   - Open terminal in Cursor (`Ctrl + ~` or `View` → `Terminal`)
   - Navigate to your project folder:
     ```bash
     cd /path/to/your/project
     ```
   - Initialize Git (if not already done):
     ```bash
     git init
     ```
   - Add remote repository:
     ```bash
     git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO_NAME.git
     ```
   - Verify remote:
     ```bash
     git remote -v
     ```

### Option B: Create Repository from Cursor

1. **Open Source Control Panel**
   - Click the Source Control icon in the left sidebar (looks like a branch)
   - Or press `Ctrl + Shift + G`

2. **Initialize Repository**
   - Click "Initialize Repository"
   - Select your project folder

3. **Create Repository on GitHub**
   - Use GitHub CLI (if installed):
     ```bash
     gh repo create YOUR_REPO_NAME --public --source=. --remote=origin --push
     ```
   - Or follow Option A steps 2-4 above

---

## 3. Cloning a Repository

### Step-by-Step:

1. **Get Repository URL**
   - Go to the GitHub repository page
   - Click the green "Code" button
   - Copy the HTTPS or SSH URL

2. **Clone in Cursor**
   - Open Command Palette: `Cmd + Shift + P` (Mac) or `Ctrl + Shift + P` (Windows/Linux)
   - Type "Git: Clone"
   - Paste the repository URL
   - Select a folder to clone into
   - Click "Open" when prompted

**OR** use Terminal:
```bash
git clone https://github.com/YOUR_USERNAME/YOUR_REPO_NAME.git
cd YOUR_REPO_NAME
```

---

## 4. Creating a Branch

### Step-by-Step:

1. **Open Source Control**
   - Click Source Control icon in sidebar (`Ctrl + Shift + G`)

2. **Create Branch**
   - Click on the branch name at the bottom-left (usually says "main" or "master")
   - Select "Create new branch..."
   - Enter branch name (e.g., `feature/new-feature` or `bugfix/fix-issue`)
   - Press Enter

**OR** use Terminal:
```bash
git checkout -b feature/new-feature
```

### Branch Naming Conventions:
- `feature/` - for new features
- `bugfix/` or `fix/` - for bug fixes
- `hotfix/` - for urgent fixes
- `docs/` - for documentation updates
- `refactor/` - for code refactoring

---

## 5. Switching Between Branches

### Step-by-Step:

1. **View All Branches**
   - Click on branch name at bottom-left
   - Or use Command Palette: `Cmd + Shift + P` → "Git: Checkout to..."

2. **Switch Branch**
   - Select the branch you want to switch to
   - Cursor will automatically switch your workspace

**OR** use Terminal:
```bash
git checkout branch-name
# or
git switch branch-name
```

---

## 6. Making Changes

### Step-by-Step:

1. **Edit Files**
   - Open any file in your project
   - Make your changes
   - Save the file (`Cmd + S` or `Ctrl + S`)

2. **View Changes**
   - Open Source Control panel (`Ctrl + Shift + G`)
   - You'll see modified files listed under "Changes"
   - Click on a file to see the diff (what changed)

---

## 7. Staging Changes

### Step-by-Step:

1. **Open Source Control**
   - Click Source Control icon (`Ctrl + Shift + G`)

2. **Stage Individual Files**
   - Hover over a file in "Changes"
   - Click the "+" icon next to the file name
   - Or right-click → "Stage Changes"

3. **Stage All Changes**
   - Click the "+" icon next to "Changes"
   - Or use Command Palette: `Cmd + Shift + P` → "Git: Stage All Changes"

**OR** use Terminal:
```bash
# Stage specific file
git add filename.txt

# Stage all changes
git add .
```

---

## 8. Committing Changes

### Step-by-Step:

1. **Stage Your Changes** (see section 7)

2. **Write Commit Message**
   - In Source Control panel, type your commit message in the text box at the top
   - Use clear, descriptive messages:
     - Good: "Add user authentication feature"
     - Bad: "fix stuff"

3. **Commit**
   - Press `Cmd + Enter` (Mac) or `Ctrl + Enter` (Windows/Linux)
   - Or click the checkmark icon (✓) next to the message box

**OR** use Terminal:
```bash
git commit -m "Your commit message here"
```

### Commit Message Best Practices:
- Use present tense: "Add feature" not "Added feature"
- Be specific and concise
- First line should be short (50 chars or less)
- Add details in body if needed (press Enter twice for multi-line)

---

## 9. Pushing to GitHub

### Step-by-Step:

1. **Commit Your Changes** (see section 8)

2. **Push to GitHub**
   - Click the "..." menu in Source Control panel
   - Select "Push"
   - Or use Command Palette: `Cmd + Shift + P` → "Git: Push"

3. **First Time Push**
   - If pushing a new branch, Cursor will ask to set upstream
   - Click "OK" or "Yes"
   - Or manually set upstream:
     ```bash
     git push -u origin branch-name
     ```

**OR** use Terminal:
```bash
# Push current branch
git push

# Push specific branch
git push origin branch-name

# Push and set upstream (first time)
git push -u origin branch-name
```

---

## 10. Pulling from GitHub

### Step-by-Step:

1. **Pull Latest Changes**
   - Click the "..." menu in Source Control panel
   - Select "Pull"
   - Or use Command Palette: `Cmd + Shift + P` → "Git: Pull"

2. **Pull with Rebase** (optional)
   - Command Palette → "Git: Pull (Rebase)"
   - This keeps a cleaner commit history

**OR** use Terminal:
```bash
# Pull changes
git pull

# Pull with rebase
git pull --rebase
```

**Always pull before pushing** to avoid conflicts!

---

## 11. Viewing Commit History

### Step-by-Step:

1. **Open Git Graph**
   - Command Palette: `Cmd + Shift + P` → "Git: View History"
   - Or install "Git Graph" extension for visual history

2. **View in Terminal**
   ```bash
   # View commit history
   git log
   
   # View with graph
   git log --oneline --graph --all
   
   # View last 10 commits
   git log -10
   ```

3. **View File History**
   - Right-click on a file in Explorer
   - Select "Open Timeline" or "Git: View File History"

---

## 12. Creating a Pull Request

### Step-by-Step:

1. **Push Your Branch** (see section 9)
   - Make sure all changes are committed and pushed

2. **Create PR on GitHub**
   - Go to your repository on GitHub.com
   - You'll see a banner suggesting to create a PR
   - Click "Compare & pull request"

3. **Fill PR Details**
   - Add a descriptive title
   - Write a description explaining your changes
   - Add reviewers (if working in a team)
   - Click "Create pull request"

4. **Using GitHub CLI** (if installed):
   ```bash
   gh pr create --title "Your PR Title" --body "Description"
   ```

---

## 13. Merging Branches

### Option A: Merge via Pull Request (Recommended)

1. **Create Pull Request** (see section 12)
2. **Review Changes**
3. **Merge on GitHub**
   - Click "Merge pull request"
   - Choose merge type:
     - **Create a merge commit** - preserves full history
     - **Squash and merge** - combines all commits into one
     - **Rebase and merge** - linear history

### Option B: Merge Locally

1. **Switch to Main Branch**
   ```bash
   git checkout main
   git pull origin main
   ```

2. **Merge Feature Branch**
   ```bash
   git merge feature-branch-name
   ```

3. **Push Changes**
   ```bash
   git push origin main
   ```

---

## 14. Resolving Merge Conflicts

### Step-by-Step:

1. **Identify Conflicts**
   - When merging/pulling, Cursor will highlight conflicted files
   - Files will have conflict markers:
     ```
     <<<<<<< HEAD
     Your changes
     =======
     Incoming changes
     >>>>>>> branch-name
     ```

2. **Resolve Conflicts**
   - Open the conflicted file
   - Choose which version to keep (or combine both)
   - Remove conflict markers (`<<<<<<<`, `=======`, `>>>>>>>`)

3. **Mark as Resolved**
   - Stage the resolved file:
     ```bash
     git add filename.txt
     ```
   - Or use Source Control panel → Stage Changes

4. **Complete Merge**
   - Commit the merge:
     ```bash
     git commit
     ```
   - Or use Source Control panel to commit

---

## 15. Reverting Changes

### Discard Uncommitted Changes:

1. **In Source Control Panel**
   - Right-click on file → "Discard Changes"
   - Or click the undo icon next to the file

2. **Discard All Changes**
   - Command Palette → "Git: Discard All Changes"

**OR** use Terminal:
```bash
# Discard changes to specific file
git checkout -- filename.txt

# Discard all changes
git checkout -- .
```

### Revert Committed Changes:

```bash
# Revert last commit (keeps changes in working directory)
git reset --soft HEAD~1

# Revert last commit (discards changes)
git reset --hard HEAD~1

# Revert specific commit
git revert commit-hash
```

---

## Quick Reference Commands

```bash
# Check status
git status

# View changes
git diff

# View staged changes
git diff --staged

# Rename branch
git branch -m old-name new-name

# Delete branch
git branch -d branch-name

# Delete remote branch
git push origin --delete branch-name

# View remotes
git remote -v

# Update remote URL
git remote set-url origin NEW_URL
```

---

## Tips & Best Practices

1. **Commit Often**: Make small, frequent commits rather than large ones
2. **Write Good Messages**: Clear commit messages help you and your team
3. **Pull Before Push**: Always pull latest changes before pushing
4. **Use Branches**: Create branches for features, fixes, and experiments
5. **Review Before Commit**: Check your changes in the diff view
6. **Keep Main Clean**: Don't commit directly to main/master; use branches

---

## Troubleshooting

### "Repository not found" error
- Check your GitHub connection in Cursor settings
- Verify repository URL: `git remote -v`
- Ensure you have access to the repository

### "Permission denied" error
- Check SSH keys or GitHub token
- Re-authenticate in Cursor settings

### "Merge conflict" error
- See section 14 for resolving conflicts
- Consider using `git pull --rebase` to avoid merge commits

---

*Happy coding! 🚀*

