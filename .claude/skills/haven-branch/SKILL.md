---
name: haven-branch
description: Create a correctly-named branch for this repo (Haven-Estates-Testing), following the feature/fix/docs/chore convention in CONTRIBUTING.md. Use when the user wants to "start work on X",[...]
---

# Haven Branch

**Trigger phrases:** "start work on X", "create a branch for X", "I need a
branch for X", "let's begin the X feature/fix". You don't need to say
"haven-branch" or use exact wording — an assistant that supports skills
matches on intent.

Create a new branch off `main` that follows the naming convention in
[`CONTRIBUTING.md`](../../../CONTRIBUTING.md): `feature/<short-name>`,
`fix/<short-name>`, `docs/<short-name>`, or `chore/<short-name>`.

## 1. Work out the branch name

From what the user describes, pick:

- **Type**: `feature` (new capability), `fix` (bug fix), `docs` (documentation
  only), or `chore` (deps, tooling, repo hygiene, no behavior change). Ask if
  it's genuinely ambiguous — don't guess between `feature` and `fix`.
- **Short name**: 2-4 words, kebab-case, describing the work
  (e.g. `stripe-checkout`, `turf-area-bug`, `roadmap-update`).

Confirm the resulting name with the user before creating it if it's not
obvious from context, e.g. `feature/stripe-checkout`.

## 2. Make sure the working tree is clean

```bash
git status
```

If there are uncommitted changes, stop and ask the user what to do with them
(commit, stash, or carry them onto the new branch intentionally) — don't
discard anything silently.

## 3. Branch off an up-to-date main

```bash
git fetch origin
git checkout main
git pull origin main
git checkout -b <type>/<short-name>
```

If `main` doesn't exist locally yet or the repo only has one branch so far,
just branch off the current `HEAD` instead of fetching/pulling.

## 4. Confirm

Report the new branch name and that it's based on the latest `main`. Don't
push it yet — that happens naturally when there's something to commit, or via
the `haven-pr` skill later.
