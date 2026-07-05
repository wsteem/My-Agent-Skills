# Skill: Daily Standup
**Version:** 1.0.0
**Description:** Helps you quickly format your daily standup — what you did, what's next, and any blockers.
**Last Updated:** 2026-07-05

## Instructions

When this skill is invoked, help the user build a standup update using this process:

### Step 1: Gather context automatically
- Run `git log --since="yesterday" --author="$(git config user.name)" --oneline` to see recent commits.
- Note the current branch name and project name.
- Use this as a starting point — don't ask the user to repeat what git already knows.

### Step 2: Ask the user three quick questions
Ask these one at a time (or all at once if the user prefers):
1. "Anything you worked on yesterday that's not in the commits above?"
2. "What are you working on today?"
3. "Any blockers or things you're waiting on?"

### Step 3: Format the standup
Output a clean standup in this format:

```
**Yesterday**
- [items from commits + anything extra they mentioned]

**Today**
- [what they said they're working on]

**Blockers**
- [blockers, or "None" if they have none]
```

Keep bullet points short (one line each). Write in first person ("Fixed the login bug" not "The user fixed..."). The whole standup should be copy-pasteable into Slack or a standup tool.

If the user invokes this skill with extra context (e.g., `/daily-standup for the auth project`), focus the git log and questions around that area.
