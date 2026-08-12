# Verification: Expected Findings for `spec/client-portal-spec.md`

This is the **test oracle** for your `review-specification` skill. The fixture contains 6 seeded defects and 5 deliberately clean requirements. Each defect needs a **different rule** to detect — that's by design. Your skill **passes** when a run reports all 6 and flags none of the clean requirements.

## Expected defects

| # | REQ | Category | Problem | The rule that catches it | A correct rewrite looks like |
|---|-----|----------|---------|--------------------------|------------------------------|
| E1 | REQ-002 | Compound requirement | Three obligations in one sentence (verify, create, send) | One obligation per requirement — flag "and"-chained verbs | Split into three requirements with individual acceptance criteria |
| E2 | REQ-003 | Missing error path | No behavior for upload failure, unsupported format, oversized or expired document | Every input/upload/integration requirement must state failure behavior | "If the upload fails, the file exceeds 10 MB, or the document is expired, the system shall display error ERR-DOC-01 and retain the entered application data." |
| E3 | REQ-004 | Solution in requirement | Prescribes implementation (React component, TypeScript, table name) instead of the need | Technology, widgets, and table names belong in design — restate as a need | "The system shall allow the client to select exactly one account currency from the currencies offered by the bank." |
| E4 | REQ-006 | Vague terms | "most" and "quickly" are unmeasurable | Forbidden-word list (most, quickly, fast, some, many, …) | "The system shall execute 99% of authorized domestic payment orders within 10 seconds." |
| E5 | REQ-007 + REQ-009 | Contradiction | Sub-CHF-1,000 execution without authorization vs. 2FA on every payment — both cannot hold | Compare requirements **across the whole document**, not sentence by sentence | Resolve with stakeholder; likely REQ-009 → "…of CHF 1,000 or above…" |
| E6 | REQ-011 | Untestable NFR | "intuitive", "user-friendly" — no metric, target, or measurement condition | Every NFR needs a metric + target value + measurement conditions | "New clients shall complete a standard payment order without help within 3 minutes in usability testing (n≥10, success rate ≥90%)." |

Note on E5: a pass requires the finding to name **both** REQ-007 and REQ-009. This defect is invisible to sentence-level review — if your skill misses it, it lacks a cross-document rule. Baseline runs (no skill) miss it almost every time.

## Clean requirements — must NOT be flagged

REQ-001, REQ-005, REQ-008, REQ-010, REQ-012. These are well-formed (EARS pattern, testable, single obligation). If your skill flags them, it's over-triggering: add an anti-false-positive rule ("if a requirement is well-formed, do not flag it; do not invent findings to appear thorough").

## Run log

Track your iterations — this is the loop you'll use on real skills:

**Maximum 3 improvement iterations.** If run 3 still misses defects, log the gap — you will close it in the group discussion.

| Run | Defects found (of 6) | Clean REQs wrongly flagged | Rule changed before next run |
|-----|---------------------|---------------------------|------------------------------|
| baseline (no skill) | | | — |
| 1 | | | |
| 2 | | | |
| 3 (last) | | | |
