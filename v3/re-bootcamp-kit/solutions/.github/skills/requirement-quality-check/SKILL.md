---
name: requirement-quality-check
description: Reviews requirements and user stories for weak words, ambiguity, missing actors, and testability. Use when asked to review, check, audit, or improve the quality of requirements or user stories.
---
# Requirement quality check

## Steps
1. Read all requirements in the input.
2. Check each requirement against the [checklist](./checklist.md).
3. Report the findings in one table with these columns: ID | Problem | Why it matters | Suggested rewrite
4. Give each finding a severity:
   - HIGH = cannot be tested as written
   - MEDIUM = two readings are possible
   - LOW = style only
5. Sort the table: HIGH first.
6. End with a list of open questions for the stakeholders.

## Rules
- Do not change the meaning in a rewrite.
- If two readings are possible, do not choose one. Ask.
- Keep the original ID in every row.
