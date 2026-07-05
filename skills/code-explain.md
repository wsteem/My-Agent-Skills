# Skill: Code Explain
**Version:** 1.0.0
**Description:** Explains a file or code snippet in plain language, tailored to someone unfamiliar with that part of the codebase.
**Last Updated:** 2026-07-05

## Instructions

When this skill is invoked, explain the specified code clearly and concisely. Follow these steps:

### Step 1: Identify what to explain
- If the user passes a file path (e.g., `/code-explain src/auth/middleware.js`), read that file.
- If the user pastes a snippet, use that.
- If neither, ask: "What file or code would you like me to explain?"

### Step 2: Read surrounding context
Before explaining, quickly check:
- What directory/module is this file in? What role does it play?
- Are there obvious callers or dependencies (imports, exports)?
- What language/framework is being used?

### Step 3: Explain it
Structure your explanation like this:

**What it does** (1-3 sentences, no jargon)
A plain English summary of the overall purpose.

**How it works** (step-by-step walkthrough)
Walk through the key parts in execution order. Reference specific function names and line numbers. Avoid restating the code — explain the *why* and *what*, not the syntax.

**Key concepts** (only if needed)
If the code uses a pattern or concept that might be unfamiliar (e.g., debouncing, middleware chains, dependency injection), explain it briefly with a simple analogy.

**Things to watch out for** (optional)
Note any side effects, edge cases, or non-obvious behavior worth knowing.

### Tone
Write as if explaining to a smart colleague who hasn't seen this part of the code before. Skip obvious things (don't explain what a for loop is). Focus on what makes *this specific code* worth understanding.

If the user asks follow-up questions about the code, answer them using the same file context.
