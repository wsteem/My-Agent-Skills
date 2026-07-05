---
Name: project-health
Version: 1.0.1
Description: Gives a quick health snapshot of the current project — git status, recent commits, and any obvious issues.
Last Updated: 2026-07-05
---

## Instructions

When this skill is invoked, run through the following checks and report the results in a clean, scannable summary:

### 1. Git Status
- Are there uncommitted changes? List modified, added, or deleted files.
- Is the branch ahead or behind its remote? By how many commits?
- What branch are we on?

### 2. Recent Activity
- Show the last 5 commits (short hash, date, message).

### 3. Project Type Detection
- Detect what kind of project this is based on files present (package.json = Node/JS, requirements.txt = Python, *.csproj = C#, etc.)
- If `package.json` exists: check if `node_modules` is present (warn if missing), and note the main scripts available.
- If `requirements.txt` or `pyproject.toml` exists: note the Python environment situation.

### 4. Quick Issues Check
- Are there any obvious config files that look incomplete (empty .env.example, missing README)?
- Are there large files that probably shouldn't be committed (>1MB that aren't in .gitignore)?

### Output format
Present findings under clear headings: **Git**, **Recent Commits**, **Project Type**, **Issues**. Use checkmarks for things that look good and warning symbols for things that need attention. Keep it brief — this is a quick glance, not a deep audit.
