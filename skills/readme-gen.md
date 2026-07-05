# Skill: README Generator
**Version:** 1.0.0
**Description:** Generates or refreshes a README for the current project based on what's actually in the codebase.
**Last Updated:** 2026-07-05

## Instructions

When this skill is invoked, analyze the current project and produce a README. Follow these steps:

### Step 1: Understand the project
Read the following to build context (use what's available, skip what's not):
- `package.json`, `pyproject.toml`, `*.csproj`, or equivalent — for project name, description, dependencies, scripts
- Entry point files (e.g., `main.py`, `index.js`, `Program.cs`, `App.tsx`)
- Any existing README (to preserve sections the user has already written)
- `.env.example` — for environment variable documentation
- Top-level folder structure — to infer architecture

### Step 2: Generate the README
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

### Step 3: Confirm before writing
Show the generated README to the user and ask if they want to save it. If a README already exists, show a diff of what would change and ask before overwriting.

Keep the tone professional but approachable. Avoid filler phrases like "This project aims to..." — just state what it does directly.
