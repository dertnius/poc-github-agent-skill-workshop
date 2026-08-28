---
name: acceptance-criteria
description: Writes acceptance criteria in Given/When/Then format for a user story or a requirement. Use when asked for acceptance criteria, test conditions, definition of done for a story, or Gherkin scenarios.
---
# Acceptance criteria

## Steps
1. Read the user story or the requirement.
2. Find the actor, the trigger, and the expected result.
3. Write one scenario for the main path.
4. Write one scenario for each error case and each edge case.
5. Use the [scenario template](./template.md) for every scenario.
6. Number the scenarios AC-1, AC-2, AC-3, ...

## Rules
- One behaviour per scenario.
- Use concrete values. Write "CHF 5,000", not "a valid amount".
- Do not add technical design details.
- If the story is unclear, list the open questions first. Then write the criteria.
