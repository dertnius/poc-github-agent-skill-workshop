# Skills & Agents for Requirements Engineers & POs — 90 min, GitHub Copilot

Audience: RE/PO, zero local setup (devcontainer → one-click Codespaces with Copilot + gh).
Outcome: every participant writes a skill, verifies it against a fixture in max 3 iterations, and runs an agent that composes their skill with a provided publish skill — all results converging in one place.

Start with `facilitator-guide.md`.

```
re-skills-training/
├── facilitator-guide.md                      # objectives, credit rules, timeline, contingencies
├── facilitator-only/reference-skill/SKILL.md # production version, revealed in the top-3 discussion
└── participant-repo/                         # → publish as the repo participants open in Codespaces
    ├── .devcontainer/devcontainer.json            # Copilot + GitHub CLI preinstalled
    ├── .github/skills/review-specification/SKILL.md   # THEY write this (template, 6 TODOs)
    ├── .github/skills/publish-review/SKILL.md         # PROVIDED — reuse, not rewrite
    ├── .github/agents/reviewer.md                     # composes both skills end to end
    ├── spec/client-portal-spec.md                     # fixture: 6 seeded defects + 5 clean REQs
    ├── verification/expected-findings.md              # the matrix + run log (max 3 iterations)
    └── docs/  concepts.md · how-to-write-a-skill.md
```

Flow: baseline run → build `review-specification` vs. the matrix (≤3 iterations) → `reviewer` agent runs their skill + `publish-review` end to end → every group's report lands in the repo's issue list (fallback `reviews/`) → 3 groups present incl. where HITL was needed → top-3 skills discussed, each group names what they'd take. Everyone builds, everything ends in the same place — reuse.
