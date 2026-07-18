---
name: Check-skill-versions
version: 1.1.0
description: Compares the versions of your globally installed skills against the latest versions in your GitHub skills repo (defaults to wsteem/My-Agent-Skills), then provides an update report.
lastUpdated: 2026-07-18
---

## Instructions

This skill always checks skill versions against the user's own GitHub repo, **wsteem/My-Agent-Skills**, unless the user explicitly names a different repo in their invocation (e.g. "check versions against acme/other-skills"). Do not ask which repo to use — assume `wsteem/My-Agent-Skills` by default.

When this skill is invoked, do the following:

### Step 1: Find the locally installed skills
Look for all skill folders (each containing a `SKILL.md`) in:
- The current project's `.claude/skills/` directory, and
- The global skills directory (e.g. `~/.claude/skills/`)

For each one found, read its `SKILL.md` frontmatter and extract:
- The skill name (`name`)
- The version (`version`)
- The last updated date (`lastUpdated` / `last Updated`)

### Step 2: Fetch the source-of-truth versions
Fetch the current `skills/` folder contents from the target repo (default `wsteem/My-Agent-Skills`, branch `main`) — use `gh api` or `WebFetch` against the raw GitHub content for each `skills/*/SKILL.md`. Extract the same `name`, `version`, and `lastUpdated` fields from each.

If the user named a different repo, use that repo's owner/name instead, but still assume the `main` branch and a top-level `skills/` folder unless told otherwise.

### Step 3: Compare and report
For every locally installed skill that also exists in the repo, compare versions using semantic versioning (https://semver.org/):
- **Up to date** — local version matches repo version.
- **Outdated** — local version is behind the repo version (show both, and what changed if a changelog/description differs).
- **Ahead / local-only** — local version is newer than the repo, or the skill doesn't exist in the repo at all (likely a local-only or in-progress skill).

Display a clean table: `Skill | Local Version | Repo Version | Status`.

### Step 4: Summarize
After the table, summarize:
- Total number of skills checked
- How many are outdated and need updating
- A one-line recommendation (e.g. "Run `/find-skills` or pull the latest `SKILL.md` for X and Y to update.")

Keep the output concise and scannable. If no local skills folder is found, say so and suggest the correct directory structure (`.claude/skills/<skill-name>/SKILL.md`).
