# 📝 Git Cheatsheet
A quick and clear reference guide to the most common Git commands with explanations.

---

## 🔧 Initial Setup
| Command | Description |
|--------|-------------|
| `git config --global user.name "Your Name"` | Sets your name for commits |
| `git config --global user.email "your@email"` | Sets your email for commits |
| `git config --global init.defaultBranch main` | Uses “main” as the default primary branch |
| `git config --global color.ui auto` | Enables colored CLI output | 
| `git config --global core.editor "code --wait"` | Uses VS Code for commit, rebase, etc |
| `git config --global alias.st "status -sb"` | Handy alias: short status |
| `git config --global alias.lg "log --oneline --graph --decorate --all"` | Alias: compact, visual history |

> View your config with paths: `git config --list --show-origin`
<br>

## 🗂️ Initialize and Clone Repos
| Command | Description |
|--------|-------------|
| `git init` | Creates a Git repo in the current folder |
| `git clone <url>` | Clones a remote repository |
| `git remote -v` | Shows configured remotes |
| `git remote add origin <url>` | Adds the “origin” remote |
| `git remote set-url origin <url>` | Changes the remote URL |
<br>

## 📦 Basic Cycle: status → add → commit
| Command | Description |
|--------|-------------|
| `git status` | Shows repo status |
| `git status -sb` | Short, readable status |
| `git diff` | Unstaged changes |
| `git diff --staged` | Differences staged for commit |
| `git add <file>` | Adds a file to staging |
| `git add .` | Stages all changes |
| `git reset <file>` | Unstages a file, keeps edits |
| `git commit -m "message"` | Creates a commit |
| `git commit -am "message"` | Adds and commits already tracked files |
| `git commit --amend -m "new message"` | Edits the last commit |

Message tips:
- Line 1: short imperative summary.
- Line 2: blank.
- Then: details and context if needed.
<br>

## 🔍 History and Search
| Command | Description |
|--------|-------------|
| `git log --oneline` | Compact history |
| `git log --oneline --graph --decorate --all` | Visual history graph |
| `git log -- <file>` | History for a specific file |
| `git blame <file>` | Who changed each line |
| `git reflog` | HEAD movement log to recover states |
<br>

## 🌿 Branches
| Command | Description |
|--------|-------------|
| `git branch` | Lists local branches |
| `git branch -r` | Lists remote branches |
| `git switch <branch>` | Switches to a branch |
| `git switch -c <branch>` | Creates and switches to a new branch |
| `git branch -m <new>` | Renames the current branch |
| `git branch -d <branch>` | Deletes a merged branch |
| `git branch -D <branch>` | Forces branch deletion |
| `git push -u origin <branch>` | Publishes branch and sets upstream |
| `git switch --detach <hash>` | Checks out a specific commit (detached HEAD) |
<br>

## 🔀 Integration: merge and rebase
| Command | Description |
|--------|-------------|
| `git merge <branch>` | Merges the branch into the current one |
| `git rebase <branch>` | Reapplies commits on top of another branch |
| `git rebase -i origin/main` | Interactive rebase to reorder or squash |
| `git merge --abort` | Aborts a conflicted merge |
| `git rebase --abort` | Aborts a rebase |
| `git merge --continue` | Continues after resolving conflicts |
| `git rebase --continue` | Continues rebase after conflicts |

Advice:
- Rebase: keeps history linear before a PR.
- Merge: preserve the original history as it happened.
<br>

## ☁️ Remotes: fetch, pull, push
| Command | Description |
|--------|-------------|
| `git fetch` | Retrieves remote refs without integrating |
| `git pull` | Fetch + merge into current branch |
| `git pull --rebase` | Fetch + rebase for cleaner history |
| `git push` | Sends commits to the remote |
| `git push -u origin <branch>` | First push and upstream setup |
| `git push origin --delete <branch>` | Deletes a remote branch |
<br>

## 🔄 Undo and Recover
| Command | Description |
|--------|-------------|
| `git reset <file>` | Unstages a file, keeps changes |
| `git reset --hard HEAD` | Discards local changes and staging back to last commit |
| `git revert <hash>` | Creates a safe inverse commit |
| `git restore <file>` | Restores a file from the last commit |
| `git restore --staged <file>` | Removes a file from staging |

When to use:
- `revert`: safe on shared branches.
- `reset --hard`: destructive, use with care.
- `restore`: file-focused recovery.
<br>

## 💼 Stash
| Command | Description |
|--------|-------------|
| `git stash push -m "WIP message"` | Saves uncommitted changes |
| `git stash -u` | Includes untracked files |
| `git stash list` | Lists stashes |
| `git stash pop` | Applies and removes the last stash |
| `git stash apply stash@{n}` | Applies a stash without removing it |
| `git stash drop stash@{n}` | Deletes a specific stash |
| `git stash clear` | Deletes all stashes |
<br>

## 🏷️ Tags
| Command | Description |
|--------|-------------|
| `git tag v1.0.0` | Creates a lightweight tag |
| `git tag -a v1.0.0 -m "message"` | Creates an annotated tag |
| `git tag --list` | Lists tags |
| `git show v1.0.0` | Shows a tag’s details |
| `git push origin v1.0.0` | Pushes a single tag |
| `git push --tags` | Pushes all tags |
| `git tag -d v1.0.0` | Deletes a local tag |
| `git push origin :refs/tags/v1.0.0` | Deletes a remote tag |
<br>

## 🧹 .gitignore and cleaning
| Command | Description |
|--------|-------------|
| Create `.gitignore` | Define files and folders to ignore |
| `git config --global core.excludesfile ~/.gitignore_global` | Global ignore patterns |
| `git clean -n` | Preview removal of untracked files |
| `git clean -fd` | Remove untracked files and directories |

Example `.gitignore`:
````
node_modules/
dist/
.env
.DS_Store
````
<br>

## 🔐 GitHub over SSH
| Command | Description |
|--------|-------------|
| `ssh-keygen -t ed25519 -C "your@email"` | Generates a modern SSH key |
| `eval "$(ssh-agent -s)"` | Starts the SSH agent |
| `ssh-add ~/.ssh/id_ed25519` | Adds your key to the agent |
| Copy public key | `cat ~/.ssh/id_ed25519.pub` and paste into GitHub → Settings → SSH and GPG keys |
| `ssh -T git@github.com` | Tests the SSH connection |
<br>

## 🧭 Quick recipes
Initialize a repo and first push:
```bash
git init
git add .
git commit -m "init"
git branch -M main
git remote add origin git@github.com:username/repo.git
git push -u origin main
```

Update a fork from upstream:
```bash
git remote add upstream git@github.com:ORIGINAL/REPO.git
git fetch upstream
git switch main
git merge upstream/main   # or: git rebase upstream/main
git push
```

Squash before a PR:
```bash
git switch feature
git rebase -i origin/main   # mark commits as squash/fixup
git push --force-with-lease
```

Revert a merge:
```bash
git log --oneline
git revert -m 1 <merge_hash>   # -m 1 picks the main parent
git push
```
<br>

## 💡 Help
| Command | Description |
|--------|-------------|
| `git help <command>` | Official manual in your terminal |
| `<command> --help` | Detailed help for a command |
| Read `git status` | Often suggests the next step |
<br>

## 📚 Glossary
- **Branch**: independent line of work inside the repo. Develop without affecting main.
- **Checkout / Switch**: move to another branch or a specific version of files. Prefer `git switch`.
- **Cherry-pick**: apply a specific commit from another branch onto the current one.
- **Clone**: download a remote repository with its history to your machine.
- **Commit**: a snapshot of changes with a descriptive message.
- **Conflict**: Git cannot merge automatically and asks you to choose what stays.
- **Diff**: differences between versions or commits.
- **Tag**: a mark on an important commit, usually a version, for quick reference.
- **Fast-forward**: merge without a merge commit because branches are aligned.
- **Fetch**: get remote changes without merging into your branch yet.
- **Fork**: your own copy of a repo on your account to work independently.
- **HEAD**: pointer to your current position, usually the latest commit of your branch.
- **Log**: the list of commits made in the repo.
- **Hooks**: scripts auto-run on Git events, e.g., before a commit.
- **Merge**: combine work from one branch into another. May create a merge commit.
- **Origin**: default name for the main remote of your repo.
- **Pull**: fetch + merge or fetch + rebase. Brings and integrates remote changes.
- **Pull request (PR)**: change proposal for review and merge on platforms like GitHub.
- **Push**: send your local commits to the remote repository.
- **Rebase**: reapply your commits "on top of" another branch for a linear history.
- **Interactive rebase**: edit the commit list to reorder, rename, or squash.
- **Release**: a published version, often tied to a tag and changelog.
- **Remote**: a repo hosted on a server or platform (GitHub, GitLab, etc.).
- **Repository**: your project folder plus Git's internal history database.
- **Restore**: get files back from the last commit or remove files from staging.
- **Revert**: create a commit that undoes another without rewriting history.
- **Reset**: move a branch reference to another commit. With `--hard`, also changes files and staging.
- **Reflog**: local log of "where HEAD pointed recently". Great for recovery.
- **SHA (hash)**: unique identifier for a commit, like a license plate.
- **Squash**: combine several commits into one for a cleaner history.
- **Stash**: temporarily store uncommitted changes to get a clean working tree.
- **Staging (index)**: middle area where you prepare what goes into the next commit.
- **Submodule**: Link another repo inside your repo as a versioned dependency.
- **Tracking branch**: local branch connected to a remote branch for easy pull/push.
- **Upstream**: the source remote you derived from, e.g., the original repo of a fork.
- **Working directory**: the files on disk as you're editing them.
- **.gitignore**: list of files and folders Git should ignore.
- **Git LFS**: large file storage for handling big assets without bloating the repo.
