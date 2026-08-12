# Facilitator Guide — Skills & Agents for RE/PO (90 min, remote)

## Learning objectives — every participant leaves able to:

1. **Write a Copilot skill** (`review-specification`): trigger description, executable rules, output contract — verified against a test fixture in max 3 iterations.
2. **Compose skills in an agent**: the `reviewer` agent runs their skill + the provided `publish-review` skill end to end, and every group's result lands in the same place.
3. **Iterate like code and reuse**: run → diff against the matrix → change one rule → rerun; reuse a platform skill instead of rewriting it.

Triads in breakout rooms; driver rotates each block; no git knowledge needed live. Everything is open in the repo except the reference skill.

## Prep (day before)

- [ ] Publish the participant repo from `participant-repo/`. Verify **Issues are enabled** and participants can create them — that's the publish destination (fallback: `reviews/` folder, already handled by the skill).
- [ ] Pilot the full path with a **non-developer**: open Codespace (devcontainer installs Copilot + `gh`) → Copilot Chat responds → `review-specification` skill, `publish-review` skill and `reviewer` agent discoverable → `gh issue create` works from the Codespace terminal.
- [ ] Check the model picker for the current 0× included models; note 1–2 names.
- [ ] Breakout rooms: one per triad + main room. Keep `facilitator-only/reference-skill/SKILL.md` on your machine.

## Credit rules (announce at 0:00 — participants have 300 premium requests/month)

Only user-sent prompts consume credits; agent-internal steps are free; 0× included models consume nothing. Rules: **0× model for every run**, **one message = one complete run**, **driver rotates per block**. Whole session ≈ 10 prompts per group → 0 credits on the included model.

## Timeline

| Time | Block | What happens |
|------|-------|--------------|
| 0:00–0:10 | **Setup + concepts** | Groups post roles in main chat, open Codespaces (green Code button). You screen-share `docs/concepts.md`: description = trigger; agent = process, skills = judgment + delivery; verification via fixture + matrix. Frame the scenario: "this spec is the change set proposed for the client portal — your job is to review it." |
| 0:10–0:15 | **Baseline (run 0)** | Plain "review `spec/client-portal-spec.md`" — no skill. Log in the run table. Expect 2–3 of 6, contradiction missed. |
| 0:15–0:40 | **Build `review-specification`** | Fill the six-category TODOs in the skill template. **Max 3 iterations**: run → compare with `verification/expected-findings.md` (the matrix) → change one rule → rerun. Pass = 6/6, zero clean REQs flagged. Not passing after run 3 is fine — the gap becomes discussion material. You hop rooms: "what rule changed between run 1 and 2?" |
| 0:40–0:45 | **Checkpoint** | Main room. Each group posts one line: `G7 \| 5/6 after run 3 \| best rule: "…"`. Paste into a visible table. |
| 0:45–1:05 | **`reviewer` agent — end to end** | Walk `reviewer.md` (2 min): step 2 runs *their* skill, step 3 runs the provided `publish-review` skill — composition + reuse. Groups set their GROUP_ID, fill the two small TODOs, then one message: "Review spec/client-portal-spec.md end to end." Result: a GitHub issue (or `reviews/` file) per group — **all in the same place**. You keep the repo's issue list on screen as they arrive. |
| 1:05–1:20 | **Presentations + top-3 discussion** | Max **3 groups** that completed end to end, 2 min each: their result, their critique, and **where the human had to step in (HITL)** to finish. Then open the top 3 skills side by side (+ reference skill as the production extension): each group names one thing they would take into their own skill. Message: everyone built differently, everything converged in one place — that's reuse. |
| 1:20–1:30 | **Wrap** | `docs/how-to-write-a-skill.md` is the takeaway. Closing round: each participant names the first real skill they'll write next week (`story-review`, `ac-check`, `dor-check` are natural candidates). |

## What you actively do

- Call time boxes; recall to main room at 0:40, 1:05, 1:20.
- Block 1 room-hopping question: "show me the run log — what changed between run 1 and 2?"
- Block 2 room-hopping question: "show me both skills firing in one run" — findings table AND publish confirmation from a single message.
- Keep the issues list visible from 0:50 — arriving issues build momentum across rooms.

## Contingencies

- **Issue creation blocked by org policy:** the publish skill falls back to `reviews/review-G<X>.md` automatically; screen-share the folder instead of the issue list.
- **Codespaces blocked:** local VS Code for whoever has it; else shared screen with remote-control handover per block.
- **Copilot down for one seat:** driver rotates to a working seat.
- **Group passes Block 1 before run 3:** they add one new defect to the fixture (escape clause "where possible", passive voice) + a matrix row, and extend the skill to catch it.
- **Group below 4/6 after run 2:** hand them the missing rule verbally — completing the end-to-end matters more than unaided discovery.
- **Agent skips a skill in Block 2:** usual cause is a vague workflow step — have them cite the skill path literally. Teachable: explicit invocation exists because auto-triggering is unreliable.
