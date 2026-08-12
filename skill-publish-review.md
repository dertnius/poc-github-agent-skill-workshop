---
name: publish-review
description: Take a findings table produced by the review-specification skill and publish it as a review report to the shared destination. Always use this after a specification review is complete and the findings need to be delivered, filed, or shared.
---

# Publish Review Skill

This skill is **provided ready-made** — you reuse it, you don't write it. It takes review findings and delivers them to the shared destination where all groups' results converge.

## Input

The complete output of the `review-specification` skill: the findings table plus the "Requirements with no findings" line.

## Report format

Assemble a Markdown report:

```
# Specification Review — <spec filename>
**Group:** <group id, e.g. G7> · **Date:** <today> · **Skill iteration:** <run number>

<the full findings table, unchanged>

<the "Requirements with no findings" line, unchanged>

## Summary
<one sentence: N defects found, M high severity>
```

Do not alter, reorder, or re-judge the findings — this skill publishes, it does not review.

## Destination

1. **Primary:** create a GitHub issue in this repository using the terminal:
   `gh issue create --title "Review <group id> — <spec filename>" --body-file <report file>`
   (write the report to a temp file first, then run the command; output the issue URL).
2. **Fallback** (if issue creation fails for any reason): write the report to `reviews/review-<group id>.md` in the repository and output that path.

Always end by stating exactly where the report landed: the issue URL or the file path.
