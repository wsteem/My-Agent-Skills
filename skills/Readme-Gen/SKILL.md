---
name: readme-gen
version: 1.1.0
description: Generates a README when a project has none, or reviews recent repo changes and updates the existing README.md to match — only touching sections that actually need it.
lastUpdated: 2026-07-18
---

## Instructions

### Step 1: Check whether a README already exists

**No README (new project/repo):** Generate a complete one from scratch — go to Step 2 (Full Generation).

**README already exists:** Don't regenerate it wholesale. Instead review what's changed and update only the parts that are now out of date — go to Step 3 (Incremental Update).

### Step 2: Full generation (new project/repo only)

Read the following to build context (use what's available, skip what's not):
- `package.json`, `pyproject.toml`, `*.csproj`, or equivalent — for project name, description, dependencies, scripts
- Entry point files (e.g., `main.py`, `index.js`, `Program.cs`, `App.tsx`)
- `.env.example` — for environment variable documentation
- Top-level folder structure — to infer architecture

Write a README with these sections (skip any that don't apply to the project):

```markdown
# Project Name

One-sentence description of what this project does.

## Features
- Key feature 1
- Key feature 2

## Getting Started

### Prerequisites
- What needs to be installed first

### Installation
Step-by-step setup commands

### Usage
How to run or use the project

## Environment Variables
| Variable | Description | Required |
|---|---|---|

## Project Structure
Brief explanation of top-level folders

## License
```

Then go to Step 4.

### Step 3: Incremental update (existing README)

- Look at what's actually changed in the repo: `git log`/`git diff` since the README's last update (or recent commits/uncommitted changes if that's not determinable), plus the current state of the codebase.
- Compare those changes against what the README currently says. Look specifically for things like: new features or commands worth listing, changed installation/usage steps, new or removed environment variables, new top-level folders, a changed dependency/prerequisite, or a skill/feature list (like the table in this repo's own README) that's now stale.
- **Not every change belongs in the README.** Internal refactors, formatting-only diffs, test changes, and other things a user of the README wouldn't care about should be left alone.
- Only edit the sections that need it — leave the rest of the README untouched, including any custom sections the user has written that aren't part of the standard template.

### Step 4: Confirm and apply

Show the user a concise summary of what changed (or, for a new README, that one was generated) — a short bullet list, not the full file dump unless they ask for it. Ask if they'd like the updates applied.

If they accept: write the file immediately, no further confirmation needed. If they want changes, adjust and re-confirm.

Keep the tone professional but approachable. Avoid filler phrases like "This project aims to..." — just state what it does directly.
