# My Agent Skills

A personal collection of Claude Code skills for everyday development tasks.

## What are skills?

Skills are markdown files that give Claude Code a specific set of instructions when you invoke them with `/skill-name`. Think of them as reusable commands you can drop into any project.

## Skills in this repo

| Skill | Version | Description |
|---|---|---|
| `check-skill-versions` | 1.1.0 | Compares your installed skills against this repo's versions and reports what's outdated |
| `bump-version` | 1.0.0 | Automatically bumps a skill's version and lastUpdated metadata (semver) after you edit it |
| `project-health` | 1.0.1 | Quick snapshot of the current project: git status, recent commits, issues |
| `daily-standup` | 1.0.1 | Formats what you worked on as a standup-style summary |
| `readme-gen` | 1.1.0 | Creates a README for new projects, or incrementally updates an existing one to match repo changes |
| `code-explain` | 1.0.1 | Explains a file or code snippet in plain language |

## Version format

Each skill uses semantic versioning: `X.X.X`
- **X** — Major: big changes to how the skill works
- **X** — Minor: small improvements or additions
- **X** — Patch: typo fixes, small tweaks

## How to install a skill

Copy any skill's folder from `skills/` into your project's `.claude/skills/` directory (each skill is a folder containing a `SKILL.md`, plus any supporting files). Then invoke it in Claude Code with `/skill-name`.

```
your-project/
  .claude/
    skills/
      project-health/
        SKILL.md
      readme-gen/
        SKILL.md
```
