---
name: estate-agent-orchestrator
description: Orchestrate the complete workflow for creating features using haven-branch and haven-pr skills. Follows a step-by-step process: create branch → create code → create PR with agent marker.
---

# Estate Agent Orchestrator

**Trigger phrases:** "use the estate agent", "run the estate agent workflow", "complete estate agent task", "start estate agent process". 

This skill orchestrates a complete end-to-end workflow for creating and submitting features:

1. **Create Feature Branch** - Uses the haven-branch skill to create a properly-named branch
2. **Create Code** - Generates the necessary code changes
3. **Create Pull Request** - Uses the haven-pr skill to open a PR with an agent marker

## Workflow Steps

### Step 1: Create Feature Branch

Use the haven-branch skill to create a new feature branch:
- Determine the branch type (feature/fix/docs/chore)
- Create the branch off main
- Confirm the branch name with the user

### Step 2: Create Code

Once the branch is created:
- Ask the user for the specific requirements
- Generate the necessary code changes
- Commit changes following Conventional Commits format
- Verify changes align with project conventions

### Step 3: Create Pull Request

Use the haven-pr skill to open the PR:
- Verify branch naming conventions
- Run security/quality checklist
- Push the branch to remote
- Draft and open the PR with the following addition to the PR body:

```markdown
---
*This pull request was created by the Estate Agent.*
```

## Important Notes

- Follow each step in sequence — do not skip steps
- Confirm with the user before proceeding to each new step
- Use the skills as documented in haven-branch and haven-pr
- Always add the agent marker to the PR description footer
- Ensure the user has reviewed and approved the work before creating the PR
