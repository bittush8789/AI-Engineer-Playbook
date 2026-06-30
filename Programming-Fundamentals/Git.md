# Git & GitHub

## Overview

Git is a distributed version control system used to track changes in source code.

GitHub is a cloud platform that hosts Git repositories and enables collaboration among developers.

---

## Why Git?

Before Git:

```text
project_final.py
project_final_v2.py
project_final_latest.py
project_final_latest_new.py
```

Managing versions becomes difficult.

---

With Git:

```text
Version History
Change Tracking
Collaboration
Rollback
```

---

# Git vs GitHub

| Git | GitHub |
|------|---------|
| Version Control Tool | Repository Hosting Platform |
| Installed Locally | Cloud Platform |
| Tracks Changes | Stores Repositories |
| Works Offline | Requires Internet |

---

# Version Control System (VCS)

## What is VCS?

A Version Control System tracks code changes over time.

---

## Benefits

```text
Track Changes
Restore Previous Versions
Team Collaboration
Branching
Code Review
```

---

# Git Architecture

```text
Working Directory
        │
        ▼
Staging Area
        │
        ▼
Local Repository
        │
        ▼
Remote Repository (GitHub)
```

---

# Installing Git

Official website:

:contentReference[oaicite:0]{index=0}

---

## Verify Installation

```bash
git --version
```

---

## Output

```text
git version 2.x.x
```

---

# Configure Git

## Set Username

```bash
git config --global user.name "Bittu"
```

---

## Set Email

```bash
git config --global user.email "bittu@example.com"
```

---

## Verify

```bash
git config --list
```

---

# Creating a Repository

## Initialize Git

```bash
git init
```

---

## Output

```text
Initialized empty Git repository
```

---

# Git Workflow

```text
Code Changes
      │
      ▼
git add
      │
      ▼
git commit
      │
      ▼
git push
```

---

# Git Status

## Theory

Shows repository status.

---

## Command

```bash
git status
```

---

## Example Output

```text
modified: app.py
```

---

# Git Add

## Theory

Moves files to staging area.

---

## Add Single File

```bash
git add app.py
```

---

## Add All Files

```bash
git add .
```

---

# Git Commit

## Theory

A commit saves changes permanently.

---

## Command

```bash
git commit -m "Added login feature"
```

---

## Example

```bash
git commit -m "Created FastAPI API"
```

---

# Git Log

## Theory

Shows commit history.

---

## Command

```bash
git log
```

---

## Output

```text
Commit ID
Author
Date
Message
```

---

# Git Diff

## Theory

Shows code changes.

---

## Command

```bash
git diff
```

---

# Git Restore

## Undo Changes

```bash
git restore app.py
```

---

# Git Reset

## Unstage Files

```bash
git reset app.py
```

---

# Git Branching

## What is a Branch?

A branch is an independent line of development.

---

## Main Branch

```text
main
```

---

## Feature Branch

```text
feature-login
```

---

# View Branches

```bash
git branch
```

---

# Create Branch

```bash
git branch feature-auth
```

---

# Switch Branch

```bash
git checkout feature-auth
```

---

## Modern Command

```bash
git switch feature-auth
```

---

# Create and Switch

```bash
git checkout -b feature-auth
```

---

# Merge Branch

## Theory

Combine branch changes.

---

## Command

```bash
git merge feature-auth
```

---

# Branch Workflow

```text
main
 │
 ├── feature-auth
 │
 ├── feature-payment
 │
 └── feature-chat
```

---

# GitHub

## What is GitHub?

GitHub is a platform for:

- Code Hosting
- Collaboration
- CI/CD
- Open Source Projects

Official website:

:contentReference[oaicite:1]{index=1}

---

# Create Repository on GitHub

Example:

```text
AI-Claims-Copilot
```

---

# Connect Local Repo to GitHub

```bash
git remote add origin https://github.com/user/repo.git
```

---

# Verify Remote

```bash
git remote -v
```

---

# Push Code

## First Push

```bash
git push -u origin main
```

---

## Regular Push

```bash
git push
```

---

# Pull Code

## Theory

Download latest changes.

---

## Command

```bash
git pull origin main
```

---

# Clone Repository

## Theory

Download repository locally.

---

## Command

```bash
git clone https://github.com/user/repo.git
```

---

# Fork Repository

## Theory

Create your own copy of another repository.

---

## Workflow

```text
Fork
  │
  ▼
Modify
  │
  ▼
Pull Request
```

---

# Pull Requests (PR)

## What is PR?

A Pull Request proposes code changes for review.

---

## Workflow

```text
Feature Branch
       │
       ▼
Pull Request
       │
       ▼
Code Review
       │
       ▼
Merge
```

---

# Merge Conflicts

## Theory

Occurs when two people modify the same code.

---

## Example

Developer A:

```python
print("Hello")
```

Developer B:

```python
print("Welcome")
```

Git cannot automatically decide.

---

## Resolve Conflict

1. Open file
2. Edit code
3. Save
4. Commit
5. Push

---

# Git Ignore

## What is .gitignore?

Prevents files from being tracked.

---

## Example

```text
__pycache__/
.env
venv/
*.log
```

---

# Tags

## Theory

Tags mark important versions.

---

## Example

```bash
git tag v1.0
```

---

# Push Tag

```bash
git push origin v1.0
```

---

# Git Stash

## Theory

Temporarily save changes.

---

## Save

```bash
git stash
```

---

## Restore

```bash
git stash pop
```

---

# Git Revert

## Undo Commit Safely

```bash
git revert COMMIT_ID
```

---

# Git Reset

## Move Repository Back

```bash
git reset --hard HEAD~1
```

---

# GitHub Actions

## What is GitHub Actions?

CI/CD platform built into GitHub.

---

## Workflow

```text
Code Push
    │
    ▼
Build
    │
    ▼
Test
    │
    ▼
Deploy
```

---

## Example

.github/workflows/deploy.yml

```yaml
name: Deploy

on:
  push:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v4
```

---

# GitHub for AI Engineers

## Store

```text
ML Models
Source Code
Notebooks
Pipelines
Prompts
```

---

## Collaborate

```text
Teams
Open Source
Code Reviews
```

---

## CI/CD

```text
Testing
Deployment
Automation
```

---

# Real AI Project Workflow

```text
GitHub
   │
   ▼
GitHub Actions
   │
   ▼
Docker Build
   │
   ▼
Push Image
   │
   ▼
Deploy to Kubernetes
```

---

# Real Insurance Project Example

```text
FNOL Application
      │
      ▼
GitHub Repository
      │
      ▼
Pull Request
      │
      ▼
GitHub Actions
      │
      ▼
Deploy to EKS
```

---

# Most Important Git Commands

```bash
git init

git status

git add .

git commit -m "message"

git push

git pull

git clone

git branch

git checkout

git merge

git log

git diff

git stash
```

---

# Interview Questions

### Q1. What is Git?

```text
A distributed version control system.
```

---

### Q2. What is GitHub?

```text
A cloud-based repository hosting platform.
```

---

### Q3. Difference between git pull and git fetch?

```text
fetch:
Downloads changes.

pull:
Downloads and merges changes.
```

---

### Q4. What is a Branch?

```text
An independent line of development.
```

---

### Q5. What is a Pull Request?

```text
A request to merge code changes into another branch.
```

---

# Learning Path

```text
Git Basics
     ↓
Repositories
     ↓
Commits
     ↓
Branches
     ↓
Merging
     ↓
GitHub
     ↓
Pull Requests
     ↓
Merge Conflicts
     ↓
GitHub Actions
     ↓
CI/CD
```

# Git & GitHub for AI Engineers

Must Learn:

```text
git add
git commit
git push
git pull
git clone
git branch
git merge
.gitignore
Pull Requests
GitHub Actions
```

These concepts are essential for:

```text
AI Engineering
MLOps
LLMOps
DevOps
AI Infrastructure
AI Platform Engineering
Forward Deployed Engineering (FDE)
```

Every production AI project—from RAG systems and AI agents to Kubernetes deployments and MLOps pipelines—uses Git and GitHub as the foundation for collaboration and automation.