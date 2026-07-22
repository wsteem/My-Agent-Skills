---
name: haven-pr
description: Open a pull request for this repo (Haven-Estates-Testing) following the conventions in CONTRIBUTING.md — branch naming, Conventional Commits, small focused PRs, and a security checklist.
---

# Haven PR

**Trigger phrases:** "open a PR", "create a pull request", "push this for
review", "let's get this reviewed", "ready to merge this". You don't need to
say "haven-pr" or use exact wording — an assistant that supports skills
matches on intent.

Prepare and open a pull request for this repo that matches the conventions in
[`CONTRIBUTING.md`](../../../CONTRIBUTING.md). Don't skip steps — the checks
below are what keep PRs small, reviewable, and safe to merge.

## 1. Check branch naming

Current branch must be one of: `feature/<short-name>`, `fix/<short-name>`,
`docs/<short-name>`, `chore/<short-name>`.

```bash
git branch --show-current
```

- If it's `main`, stop and ask the user to create a properly named branch first
  — never open a PR from `main` into itself.
- If it doesn't match one of the four prefixes, tell the user and suggest a
  rename (`git branch -m <new-name>`) before continuing.

## 2. Look at what's actually changing

```bash
git status
git log main..HEAD --oneline
git diff main...HEAD --stat
```

- If this touches more than one clearly unrelated concern, flag it to the user
  — CONTRIBUTING.md asks for small, focused PRs. Suggest splitting rather than
  bundling unless the user wants to proceed anyway.
- If commit messages don't already follow Conventional Commits
  (`feat: ...`, `fix: ...`, `docs: ...`, `chore: ...`), that's fine for the PR
  title/body (below) but mention it so the habit improves going forward.

## 3. Run the security/quality checklist

Before drafting the PR, check for the things CONTRIBUTING.md calls out:

- **Secrets**: `git diff main...HEAD` — confirm no API keys, tokens, or
  credentials are being added outside `.env.local` (which is gitignored).
- **RLS**: if any Supabase table/schema changes are included, confirm
  Row-Level Security policies are part of the same PR, not a follow-up.
- **PCI scope**: if payment flows changed, confirm no card data touches
  Haven's own database — Stripe should own that data.
- **Docs**: if behavior changed, confirm the relevant file under `docs/` was
  updated in this branch. If not, ask the user whether it should be, or note
  it as a known gap in the PR body.
- **README**: run the `haven-readme` skill's classification against
  `git diff main...HEAD` if it wasn't already done at commit time — if the
  branch adds/removes a top-level file, skill, or doc, changes the tech
  stack, or changes user-facing scope, confirm `README.md` was updated too.

Don't block on these — surface what's missing and let the user decide.

## 4. Push the branch

```bash
git push -u origin <branch-name>
```

Confirm with the user before pushing if the branch hasn't been pushed before,
per standard practice for actions visible to others.

## 5. Draft the PR

Title: Conventional Commits style, matching the branch prefix
(`feature/` → `feat:`, `fix/` → `fix:`, `docs/` → `docs:`, `chore/` → `chore:`),
under 70 characters.

Body template:

```markdown
## Summary
- <1-3 bullets: what changed and why, not a restatement of the diff>

## Test plan
- [ ] <how this was verified — manual check, test run, etc.>

## Docs
- [ ] Relevant docs/ files updated, or N/A

## Security checklist
- [ ] No secrets committed
- [ ] RLS policies included for any new client-scoped tables, or N/A
- [ ] No card data touches Haven's database, or N/A
```

Open it with:

```bash
gh pr create --title "<title>" --body "$(cat <<'EOF'
<body>
EOF
)"
```

## 6. Reviewer reminder

CONTRIBUTING.md requires at least one other collaborator to review before
merge. Mention this to the user after the PR is created — don't merge it
yourself even if asked, unless the user is explicitly acting as their own
reviewer and says so.
