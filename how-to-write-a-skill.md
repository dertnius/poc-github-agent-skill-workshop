# How to Write a Skill — Takeaway Checklist

The eight rules from today, in the order you apply them.

1. **One skill = one job.** Name it after the job (`review-specification`, not `helper`). If you're writing "and also…", that's a second skill.

2. **The description is the trigger — write it last, write it pushy.** State what the skill does *and* every situation where Copilot should reach for it: "Review requirements for ambiguity, testability, contradictions… Always use when asked to review, audit, check, or comment on requirements, specs, user stories or acceptance criteria — even if the word 'review' is not used." A skill with a timid description silently never fires.

3. **Rules a stranger could apply.** Every rule needs a detection cue, not an adjective. "Flag vague terms" is useless; a forbidden-word list (fast, most, user-friendly, where possible, etc.) is executable. If you can't say how to detect it, you haven't finished thinking it through.

4. **Fix the output contract.** Exact format, exact columns, exact closing line. Stable output is what makes a skill verifiable by you and consumable by an agent or a CI step. Change the rules freely; keep the contract frozen.

5. **Write the anti-false-positive rule.** Models invent findings to appear thorough. Every review-type skill needs: "If it is well-formed, do not flag it" and "unknown value → write `<TBD: stakeholder>`, never invent a plausible number."

6. **Verify against a fixture before you trust it.** A test document with known-good and known-bad content, plus an expected-findings file, lives next to the skill. Pass = all seeded defects found, zero clean items flagged. No fixture, no confidence.

7. **Iterate like code.** Run → diff against expected → change **one** rule → rerun. Log the runs. When it passes: commit, MR review like any source file, note the version.

8. **Compose deliberately.** An agent that must apply your skill should invoke it explicitly in its workflow ("apply the review-specification skill to the spec, then the publish-review skill to the findings") — deterministic. Description-based auto-triggering is the fallback for ad-hoc use. Design for the explicit path; tune the description for the rest.

First real skill to write next week: pick a review you personally perform repeatedly (spec review, story refinement, AC check, test-case review). You already know the rules — today you learned how to package them.
