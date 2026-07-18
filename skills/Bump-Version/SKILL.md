---
name: bump-version
version: 1.0.0
description: Automatically bumps the version and lastUpdated metadata in a skill's SKILL.md based on the changes made to that skill's folder, following semantic versioning.
lastUpdated: 2026-07-18
---

## Instructions

Trigger phrases: "bump version", "update version", "bump the version", "update the version", or equivalent. When triggered, act immediately — do not ask for confirmation before editing the frontmatter, and do not ask which skill to bump if it can be determined automatically.

### Step 1: Identify which skill(s) changed
- Run `git status` and `git diff` (staged + unstaged) to find every file that was added, modified, or deleted under `skills/`.
- Group changed files by their top-level skill folder (e.g. `skills/Readme-Gen/`). A "skill folder" includes `SKILL.md` plus everything nested under it — `assets/`, `scripts/`, `references/`, examples, etc. Any changed or new file anywhere in that folder counts as a change to that skill.
- If changes span multiple skill folders, process each one independently — each gets its own version bump based only on its own changes.
- If a folder is brand new (didn't exist in the last commit), treat it as a new skill: set `version: 1.0.0` and `lastUpdated` to today's date, regardless of the diff content.

### Step 2: Review what changed in each skill folder
For each affected existing skill, read the full diff of every changed file in that folder (not just `SKILL.md`) to understand the nature of the change. Consider:
- What instructions, steps, or behavior were added, removed, or altered
- Whether any asset/script/reference file was added, removed, or rewritten
- Whether the change affects how the skill behaves for a user invoking it, or is purely cosmetic (typos, formatting, comment wording)

### Step 3: Determine the semver bump
Apply semantic versioning (https://semver.org/) rules to decide the bump for each skill:
- **MAJOR** (`X.0.0`) — a breaking or incompatible change: instructions that change what the skill does in a way existing users would need to know about, removed steps/files that were previously relied on, or a fundamentally different trigger/behavior.
- **MINOR** (`x.Y.0`) — backward-compatible additions: new steps, new supporting files (assets/scripts/references), new capabilities added to the skill without removing or breaking existing behavior.
- **PATCH** (`x.y.Z`) — backward-compatible fixes or tweaks: typo fixes, wording/clarity edits, formatting, small corrections that don't change what the skill does.

When a skill folder has multiple kinds of changes, use the highest-impact category (MAJOR beats MINOR beats PATCH).

### Step 4: Apply the update
For each affected skill's `SKILL.md`:
- Update the `version` field per Step 3 (reset lower segments to 0, e.g. a MINOR bump on `1.4.2` becomes `1.5.0`).
- Update the `lastUpdated` field to today's date (`YYYY-MM-DD`).
- Make the edit directly — no confirmation needed.

### Step 5: Report
After applying all bumps, output a short summary table: `Skill | Old Version -> New Version | Bump Type | Reason`. Keep the reason to one short phrase (e.g. "added retry logic", "typo fix in Step 2", "new skill created").
