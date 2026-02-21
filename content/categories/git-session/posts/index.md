---
title: "Git Commands: From Absolute Beginner to Pro Advanced"
date: 2026-02-21
draft: false
tags: ["Git", "Version Control", "Beginner", "Advanced", "Cheatsheet"]
description: "A comprehensive guide to Git commands, covering everything from the absolute basics to advanced pro techniques."
authors: ["ckdash"]
categories: ["git-session"]
---

Git is the backbone of modern software development. Whether you're working solo on a weekend project or collaborating with hundreds of engineers in a corporate environment, mastering Git is a superpower. 

This guide covers everything you need to know, starting from your very first commit to rescuing a broken repository like a pro.

---

## 1. Setup & Configuration

Before you start tracking code, Git needs to know who you are. These commands configure your Git environment.

### Set your identity
```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

### View your configuration
```bash
git config --list
```

---

## 2. The Absolute Basics: Getting Started

These are the commands you'll use to initialize projects and get code onto your machine.

### Start a new repository
Turns an existing directory into a Git repository.
```bash
git init
```

### Copy an existing repository
Downloads a project and its entire version history from a remote server (like GitHub or GitLab).
```bash
git clone <url>
```

---

## 3. The Daily Workflow

This is your bread and butter. You will type these commands dozens of times a day.

### Check repository status
Shows which files are modified, staged, or untracked.
```bash
git status
```

### Stage changes
Prepares files to be committed.
```bash
# Stage a specific file
git add filename.ext

# Stage all modified and new files
git add .
```

### Commit changes
Saves your staged changes to the local repository with a descriptive message.
```bash
git commit -m "Add a descriptive commit message here"
```

### View history
See the history of commits in the repository.
```bash
# Standard comprehensive log
git log

# A cleaner, one-line summary of commits
git log --oneline
```

---

## 4. Branching & Merging

Branches allow you to work on features or fixes in isolation without affecting the main codebase.

### List branches
Look at all your local branches. Add `-a` to see remote branches as well.
```bash
git branch
```

### Create a new branch
```bash
git branch <branch-name>
```

### Switch branches
Move to a different branch. (`switch` is newer and preferred, but `checkout` is also widely used).
```bash
# The modern way
git switch <branch-name>

# The older/traditional way
git checkout <branch-name>
```

> [!TIP]
> You can create and switch to a new branch in one command using `git switch -c <branch-name>` or `git checkout -b <branch-name>`.

### Merge a branch
Brings the history of the specified branch into your *current* branch.
```bash
git merge <branch-name>
```

---

## 5. Working with Remotes

To collaborate, you must synchronize your local repository with a remote server.

### List remotes
Show the remote repositories currently connected to your local repo.
```bash
git remote -v
```

### Fetch updates
Downloads new data from the remote repository, but *does not* integrate it into your working files.
```bash
git fetch origin
```

### Pull updates
Fetches changes from the remote and immediately merges them into your current branch.
```bash
git pull origin <branch-name>
```

### Push changes
Uploads your local commits to the remote repository.
```bash
git push origin <branch-name>
```

---

## 6. Pro / Advanced Commands

When things get complicated—or when you inevitably make a mistake—these are the commands that will save the day.

### Stashing
Temporarily shelves your uncommitted changes so you can work on something else (like switching branches quickly) without having to commit half-done work.
```bash
# Save uncommitted work
git stash

# Restore the most recently stashed work
git stash pop

# View all stashes
git stash list
```

### Rebase
Takes your current branch and reapplies its commits on top of another branch. It creates a much cleaner, linear history compared to standard merging.
```bash
git rebase main
```
> [!WARNING]
> Never rebase commits that have already been pushed to a shared remote branch. It rewrites history and will cause headaches for your collaborators.

### Cherry-Pick
Grab a specific commit from another branch and apply it to your current branch.
```bash
git cherry-pick <commit-hash>
```

### Reset
Moves the repository state backward in time.
```bash
# Keeps your file changes, but removes the commit from history (Soft reset)
git reset --soft HEAD~1

# Destructive: completely wipes out the last commit and all changes in it (Hard reset)
git reset --hard HEAD~1
```

### Revert
Creates a *new* commit that perfectly undoes the changes of a previous commit. This is the safe way to undo mistakes in a public repository because it doesn't rewrite history.
```bash
git revert <commit-hash>
```

### Reflog
The ultimate safety net. It records every time your branch tip changes (even after hard resets). If you deleted a branch or lost a commit, you can usually find the hash here and recover it.
```bash
git reflog
```

### Bisect
A powerful debugging tool that uses binary search to find exactly which commit introduced a bug.
```bash
git bisect start
git bisect bad                 # The current commit has the bug
git bisect good <commit-hash>  # A past commit that you know was working fine
# Git will checkout a commit in the middle. You test your app, and tell Git:
git bisect good # OR git bisect bad
# Repeat until Git pinpoints the culprit!
```

---

## Conclusion

Git is incredibly deep, but you don't need to memorize everything at once. Start by mastering the daily workflow (`add`, `commit`, `push`, `pull`), practice branching, and slowly introduce advanced commands like `stash` and `rebase` as you encounter more complex scenarios. 

Happy committing!
