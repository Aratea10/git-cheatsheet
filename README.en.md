# 📝 Git Cheatsheet

A quick and clear reference guide to the most common Git commands with explanations.

---

## 🔧 Initial Setup
| Command | Description |
|--------|-------------|
| `git config --global user.name "[name]"` | Sets the global username for commits. |
| `git config --global user.email "[email]"` | Sets the global email for commits. |

## 🗂️ Initialize and Clone Repositories
| Command | Description |
|--------|-------------|
| `git init` | Initializes a new Git repository in the current directory. |
| `git clone [url]` | Clones (copies) a remote repository to your local machine. |

## 📤 Staging and Commits
| Command | Description |
|--------|-------------|
| `git add [file]` | Adds a specific file to the staging area (prepares it for commit). |
| `git add .` | Adds all modified and new files to the staging area. |
| `git status` | Shows the current state of the repository: modified files, staged files, untracked files, etc. |
| `git commit -m "message"` | Creates a new commit with the staged changes and a descriptive message. |

## 🔍 View History and Differences
| Command | Description |
|--------|-------------|
| `git log` | Displays the commit history of the repository. |
| `git diff` | Shows differences between the working directory and the staging area. |
| `git diff --staged` | Shows differences between the staging area and the last commit. |

## 🌿 Branches
| Command | Description |
|--------|-------------|
| `git branch` | Lists all local branches. |
| `git branch [name]` | Creates a new branch with the specified name. |
| `git branch -d [name]` | Deletes the specified branch (only if already merged). |
| `git checkout [branch]` | Switches to the specified branch. |
| `git checkout [commit]` | Switches the repository state to a specific commit ("detached HEAD" mode). |
| `git checkout -- [file]` | Discards local changes in a specific file (restores from the last commit). |
| `git merge [branch]` | Merges the specified branch into the current branch. |

## ☁️ Working with Remote Repositories
| Command | Description |
|--------|-------------|
| `git remote -v` | Shows the URLs of configured remote repositories. |
| `git pull` | Fetches changes from the remote repository and merges them into the current local branch. |
| `git push` | Pushes local commits to the remote repository. |
| `git push origin [branch]` | Pushes the specified local branch to the remote repository (`origin`). |

## 🔄 Undo Changes and Temporary Storage
| Command | Description |
|--------|-------------|
| `git reset [file]` | Removes a file from the staging area but keeps changes in the working directory. |
| `git reset --hard` | Discards all changes in the working directory and staging area, reverting to the last commit. |
| `git stash` | Temporarily saves uncommitted changes so you can switch branches or perform other operations. |
| `git stash pop` | Restores and applies the most recent stashed changes. |

## 🏷️ Tags
| Command | Description |
|--------|-------------|
| `git tag [name]` | Creates a tag at the current commit, useful for marking releases. |

---

> 💡 **Tip**: Use `git help [command]` or `git [command] --help` to get detailed help for any command.