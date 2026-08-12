# Runbook — keep open during the session

## (1) Trainer

Day before: publish repo · Issues enabled · pilot Codespace + Copilot + `gh issue create` with a non-developer · note 0× model names · breakout rooms ready.

1. 0:00 — roles in main chat, Codespaces open, announce credit rules: 0× model / one message = one run / driver rotates.
2. –0:10 — screen-share `docs/concepts.md`; frame: "this spec is the proposed change set — review it."
3. 0:10 — breakouts, run 0.
4. 0:15–0:40 — hop rooms: "what rule changed between run 1 and 2?" Enforce max 3 iterations.
5. 0:40 — recall; collect one-liners into visible table.
6. 0:45 — walk `reviewer.md` (2 min); breakouts; issue list on screen from 0:50.
7. Hop rooms: "show me both skills firing in one run."
8. 1:05 — recall; presentations → top-3 discussion + reference skill.
9. 1:20–1:30 — takeaway doc; closing round.

## (2) One group

1. Codespace open · driver/navigator/verifier (rotate per block) · pin 0× model.
2. Run 0: "review `spec/client-portal-spec.md`" — no skill. Log the row.
3. Open `.github/skills/review-specification/SKILL.md`; read the six TODO categories.
4. Loop ≤3×: one rule changed → identical prompt rerun → diff vs `verification/expected-findings.md` → log row.
5. 0:40 — post `G7 | 5/6 after run 3 | best rule: "…"`; checkpoint.
6. Open `.github/agents/reviewer.md`: set GROUP_ID, zero-findings rule, sharpen description.
7. One message: "Review spec/client-portal-spec.md end to end." Note every manual intervention (HITL).
8. Confirm issue/file landed; prep 2-min presentation: result · critique · HITL moments.

## (3) All-groups discussion

1. 3 end-to-end groups × 2 min: published result, critique, HITL.
2. Top-3 skills side by side (paste in chat) + reference skill as production extension.
3. Round: each group names ONE thing it would take from another skill.
4. Trainer: different skills, one issue list = reuse; the publish skill nobody wrote is reuse already consumed.
5. Wrap: `docs/how-to-write-a-skill.md`; each participant — first real skill next week, one sentence.
