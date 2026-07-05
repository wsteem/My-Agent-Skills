---
Name: Check-skill-versions
Version: 1.0.1
Description: Scans all globally cloned skills and compares their verison against the latest GitHub repo version, then provides an update report. 
Last Updated: 2026-07-05
---

## Instructions

When this skill is invoked, do the following:

1. Look for all `.md` files in the `skills/` directory of the current repo (or a path the user specifies).
2. For each skill file, read the top of the file and extract:
   - The skill name (from the `# Skill:` heading)
   - The version number (from the `**Version:**` line)
   - The last updated date (from the `**Last Updated:**` line)
3. Display a clean table showing: Skill Name | Version | Last Updated
4. Check git log for each file and compare the `Last Updated` date against the most recent commit date for that file. If a file was committed more recently than its `Last Updated` date, flag it with a warning.
5. After the table, summarize:
   - Total number of skills found
   - Any skills that appear stale or have mismatched dates
   - A recommendation if any skills look like they need attention

Keep the output concise and easy to scan. If no skills folder is found, let the user know and suggest the correct directory structure.
