# My Agent Skills

A personal collection of Claude Code skills for everyday development tasks.

## What are skills?

Skills are markdown files that give Claude Code a specific set of instructions when you invoke them with `/skill-name`. Think of them as reusable commands you can drop into any project.

## Skills in this repo

| Skill | Version | Description |
|---|---|---|
| `check-skill-versions` | 1.0.0 | Scans all skills in this repo and reports their versions |
| `project-health` | 1.0.0 | Quick snapshot of the current project: git status, recent commits, issues |
| `daily-standup` | 1.0.0 | Formats what you worked on as a standup-style summary |
| `readme-gen` | 1.0.0 | Generates or refreshes a README for the current project |
| `code-explain` | 1.0.0 | Explains a file or code snippet in plain language |

## Version format

Each skill uses semantic versioning: `X.X.X`
- **X** — Major: big changes to how the skill works
- **X** — Minor: small improvements or additions
- **X** — Patch: typo fixes, small tweaks

## How to install a skill

Copy any `.md` file from the `skills/` folder into your project's `.claude/skills/` directory. Then invoke it in Claude Code with `/skill-name` (the filename without `.md`).

```
your-project/
  .claude/
    skills/
      project-health.md
      readme-gen.md
```
