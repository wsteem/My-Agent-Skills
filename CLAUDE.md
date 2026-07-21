# Git workflow

- Never edit files directly on `main`. Before making any change, create a feature branch (`feature/<short-description>` for additions, `fix/<short-description>` for bug fixes).
- This is a habit I should follow by judgment — it is not mechanically enforced. The push step *is* mechanically enforced (see `.claude/settings.json` hook): a direct push to `main` is blocked regardless of instructions.
