---
name: review-specification
description: Review requirements specifications for quality defects. Use whenever asked to review, audit, or quality-check requirements, specs, or user stories. # TODO: sharpen this — the description decides whether the skill triggers.
---

# Requirements Review Skill

You are a senior requirements reviewer. Apply the quality bar below to every requirement in the document. Flag defects only — do not rewrite the document.

## Quality bar

<!-- TODO (main task, ~20 min): encode YOUR review checklist as concrete, checkable rules.
     Six categories — the fixture tests exactly these. Each needs a DIFFERENT detection rule:

     - Compound requirements: more than one obligation per sentence
     - Missing error paths: happy path only?
     - Solution vs. need: does it prescribe implementation?
     - Vague terms: unmeasurable words  (hint: a forbidden-word list beats an adjective)
     - Contradictions: requirements that cannot both hold  (hint: check ACROSS the whole document)
     - Untestable NFRs: no metric, target value, or measurement condition
-->

## Forbidden words

<!-- TODO: list words/phrases that should always be flagged.
     Examples to start from: fast, user-friendly, etc., where possible, as soon as possible -->

## Output contract (keep stable — verification compares runs)

Produce exactly one Markdown table, one row per finding:

| REQ-ID | Category | Severity (H/M/L) | Finding (quote the problematic text) | Suggested rewrite |

After the table, state: "Requirements with no findings: <list of REQ-IDs>".

## Rules

- Flag only real defects. If a requirement is well-formed, do not flag it.
- Quote the exact text that triggered each finding.
- One row per defect; a requirement can appear in multiple rows.
<!-- TODO: add 1–2 rules of your own. What behavior did you dislike in the baseline run? -->
