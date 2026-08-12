# Concepts: Skills and Agents in GitHub Copilot

Read time: 5 minutes. This is the mental model for the whole session.

## What a skill is

A skill is **packaged domain expertise as instructions**, stored in the repo, versioned like code:

```
.github/skills/review-specification/
└── SKILL.md
    ├── YAML frontmatter: name + description   ← always visible to Copilot
    └── Body: rules, checklists, output format ← loaded when the skill triggers
```

Three-tier loading (progressive disclosure): Copilot always sees only name + description of every skill. When a task matches a description, it loads the body. Bundled resources (reference files, scripts) load only if the body points to them. This keeps context lean — you can have 50 skills without drowning the model.

**The description is the trigger.** It must say what the skill does *and* when to use it. A weak description means the skill silently never fires.

A skill is *not* a prompt you paste. It's not repo-wide custom instructions either (those are always-on and global). A skill is on-demand, modular, and owned like source code: drafted, tested, MR-reviewed, versioned.

## What an agent is

An agent (`.github/agents/<name>.md`) is a **worker with a mission and a workflow**: persona, ordered steps, hard rules, output contract. It runs multi-turn and decides what to do next — unlike a single chat prompt.

## The relationship — the point of today

```
Agent (worker)  ──loads──▶  Skill (knowledge)  ──applied to──▶  Work item
reviewer                    review-specification + publish-review           spec under review
```

The agent supplies *process* (read notes → draft → review → fix → deliver). The skill supplies *judgment* (what "good requirement" means here). Separating them is what makes both reusable: the same `review-specification` skill serves the agent's self-check, your manual spec reviews, and a CI quality gate — one quality bar, maintained in one file.

Two ways an agent uses a skill:

1. **Explicit invocation** — the agent's workflow says "apply the `review-specification` skill to your draft." Deterministic. Use this for quality gates.
2. **Auto-trigger** — Copilot matches the task to the skill's description. Convenient, less predictable. Good descriptions make this work.

Today you build the judgment half yourself (`review-specification`), reuse a provided delivery skill (`publish-review`), and wire both into the `reviewer` agent — one run, findings plus a published report, every group converging in the same issue list.

## What a run costs

Copilot bills **premium requests per user-sent prompt × the model's multiplier**. Included 0× models cost nothing, and everything an agent does inside one of your turns — reading files, applying a skill, fixing its own findings — is free; only your messages count. Two habits follow: pin the model to an included one for routine runs, and write complete run-to-completion prompts instead of chatting a task along one correction at a time. Today's entire session fits in zero premium requests; your 300/month are for the work where model choice actually matters.

## How you verify a skill

Like code: against a **test fixture with expected results**. Our fixture is `spec/client-portal-spec.md` — 12 requirements with 6 known defects and 5 deliberately clean ones. `verification/expected-findings.md` is the oracle. A skill passes when it reports all 6 defects and flags none of the 5 clean requirements. Run → diff against expected → sharpen one rule → rerun. That loop is the job.
