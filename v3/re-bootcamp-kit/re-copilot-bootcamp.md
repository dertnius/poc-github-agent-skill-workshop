# Copilot Skills and Custom Agents
## 5-hour bootcamp for requirements engineers

Facilitator guide, lab scripts, and reference cards. Verified against the VS Code docs of 2026-08-26. Re-check one week before the day. This area changes monthly.

---

## 1. Goal

At the end of the day, each participant can:

1. Ask Copilot for help with requirements work in VS Code.
2. Write team rules in `copilot-instructions.md`.
3. Build a skill. Test it. Fix it.
4. Build a custom agent. Give it a job and a toolbox. Test it.
5. Choose the right tool: rule, skill, or agent.
6. Share a skill or an agent with the team.

## 2. Audience and assumptions

- Requirements engineers. Little or no coding experience.
- Tool: VS Code with GitHub Copilot (Enterprise). Chat view, Agent mode.
- No terminal. No Git commands. Everything happens in the VS Code window.
- Each person has the `starter/` folder unzipped on the laptop. No clone. No repo.
- Group size: max 12 per facilitator. Pods of 3. One helper per 2 pods if possible.
- Explain every hard word the first time. See the word list in card A.

## 3. Before the day — facilitator checklist

- [ ] Run every lab on a corporate laptop with the corporate VS Code build. Note every difference from this document. Fix the document.
- [ ] Check the Copilot policies: Agent mode on, custom agents allowed, skills allowed, one model available that does not burn premium requests.
- [ ] Check the VS Code version. Skills need 1.108 or later. The Agent Customizations editor is a preview feature. If it is missing, use the manual paths in card C and card D.
- [ ] Check the handoff button (lab 5). If it does not show, change `agent: Requirement Reviewer` to the file name `requirement-reviewer` in `story-writer.agent.md`.
- [ ] Send the starter ZIP and the setup mail 3 days before. Ask each person to: open VS Code, sign in to Copilot, unzip the kit, open the folder, click "Yes, I trust the authors", open Chat, send "hello".
- [ ] Prepare a rescue copy of `solutions/` on a share. Copy `solutions/.github` over `starter/.github` to get a finished workspace.
- [ ] Print `CHEATSHEET.md`. One per person.
- [ ] Room: projector, one power socket per person, whiteboard.

## 4. Schedule (300 min)

| Start | Min | Block |
|---|---|---|
| 00:00 | 15 | Setup check. VS Code in 5 clicks. |
| 00:15 | 30 | M1 Talk to Copilot (lab 1) |
| 00:45 | 20 | M2 House rules (lab 2) |
| 01:05 | 10 | Break |
| 01:15 | 60 | M3 Skills (labs 3a, 3b) |
| 02:15 | 25 | Lunch |
| 02:40 | 60 | M4 Custom agents (labs 4a, 4b) |
| 03:40 | 10 | Break |
| 03:50 | 45 | M5 Put it together. Build your own (lab 5) |
| 04:35 | 20 | M6 Share. Keep it good. Troubleshoot. |
| 04:55 | 5 | Wrap-up |

If you run late: give the solution for lab 3b, demo lab 4b instead of running it, cut lab 5 to 20 min. Never cut M6.

## 5. Modules

Each module has four parts: Teach (say this), Show (demo), Do (lab), Check (how you know they got it).

### Setup check (15 min)

VS Code in 5 clicks. Everyone does this together.

1. File > Open Folder. Select the `starter` folder.
2. Click "Yes, I trust the authors".
3. Click the Explorer icon (left bar, top). You see the files.
4. Open Chat: `Ctrl+Alt+I`, or the Chat icon in the title bar.
5. In the Chat view, choose "Agent" in the dropdown. Send: "List the files in this folder."

Check: everyone sees an answer. Helpers go to anyone who is stuck.

Word list for the whiteboard: folder = workspace. The Chat view = where you talk to Copilot. Agent = Copilot can read and change files for you.

### M1 Talk to Copilot (30 min)

Teach (5 min):
- Copilot is a very fast colleague. It has no memory of your team.
- Give it four things: the role, the task, the input, the output format.
- Context = the files Copilot can see. Add a file with `#` and the file name. Or drag the file into the chat box.
- Copilot can invent facts. Every answer needs a check.

Show (5 min):
1. Send: "Find unclear words in #requirements-raw.md".
2. Send: "Do it again. Give a table: ID | word | problem | better version."
3. Compare the two answers. Same question, different shape. Ask the room which one they can use.

Lab 1 (15 min), in pods:
1. Send: "Review #requirements-raw.md. Find words that are not testable."
2. Send: "Do it again. Give a table: ID | word | problem | better version."
3. Send: "Write REQ-09 as separate requirements."
4. In your pod: find one thing Copilot got wrong or invented. Write it on a sticky note.

Check (5 min): collect 3 sticky notes on the whiteboard. Message: "This is why we give Copilot rules."

### M2 House rules (20 min)

Teach (5 min):
- `.github/copilot-instructions.md` = the house rules. Copilot reads it in every chat in this folder. Always on.
- Keep it short. Less than one page. Only rules that are always true.
- A rule that is only true for one task is not a house rule. That is a skill. Next module.

Show (5 min):
1. Open `.github/copilot-instructions.md`. Read the 6 rules out loud.
2. Start a new chat. Send the lab-1 prompt from step 2. The table now follows the rules.

Lab 2 (10 min):
1. Open `.github/copilot-instructions.md`.
2. Add one rule from your own team. Example: "Write all dates as YYYY-MM-DD."
3. Save: `Ctrl+S`.
4. Start a new chat (`+` icon). Send the lab-1 prompt. Check that Copilot applies your rule.

Check: each pod shows one answer that follows the new rule.

### M3 Skills (60 min)

Teach (10 min):
- A skill is a folder with a recipe card. The card is a file named `SKILL.md`.
- The card has a header and a body. The header is three lines between `---` marks. This format is called "frontmatter". It holds the `name` and the `description`.
- Copilot reads the name and the description of all skills at the start of a chat. It opens the full card only when your request matches the description.
- So: the description decides when the skill runs. Write WHAT the skill does AND WHEN to use it.
- Extra files (a template, a checklist) sit next to the card. Link them from the card. Copilot opens them only when the card points to them.
- Three levels: name + description, then the card, then the linked files. Many skills cost nothing until they are needed.
- Rules: folder name = `name`. Lowercase letters, numbers, hyphens only. One job per skill.
- You can also run a skill by hand. Type `/` and the name.

Show (10 min):
1. In the Chat view, click the gear icon. The Agent Customizations editor opens.
2. Click the Skills tab. Choose New Skill (Workspace). Name: `acceptance-criteria`.
3. VS Code creates `.github/skills/acceptance-criteria/SKILL.md`. Fill in the description. Paste the body from `solutions/`.
4. Save. Start a new chat. Send: "Write acceptance criteria for REQ-01 in #requirements-raw.md". Show that Copilot used the skill (it says so in the response, or the steps match the card).
5. Send: `/acceptance-criteria for US-042 in #user-story-example.md`. Same skill, called by hand.

Manual path if the editor is missing: Explorer > right-click `.github/skills` > New Folder `acceptance-criteria` > right-click the folder > New File `SKILL.md`.

Lab 3a (20 min): build `acceptance-criteria`.
1. Create the skill folder and `SKILL.md` as in the demo.
2. Header: `name: acceptance-criteria`. Description: what it does and when to use it. Say "Given/When/Then" in the description.
3. Body: 5 numbered steps and 3 rules. Use your own words. Keep it under 20 lines.
4. Save. Type `/skills`. Your skill is in the list. If not: see card E.
5. Test with plain language: "Write acceptance criteria for REQ-05 in #requirements-raw.md".
6. Test by hand: `/acceptance-criteria for REQ-06`.
7. Read the result. Change one rule in the card. Test again. See the change.

Lab 3b (15 min): add a resource file and a second skill.
1. In the skill folder, create `template.md`. Put the Given/When/Then block in it.
2. In `SKILL.md`, add a step: "Use the [scenario template](./template.md)."
3. Test again. The output follows the template.
4. Now build `requirement-quality-check` with a `checklist.md`. Fast way: type `/create-skill` and describe it. Then fix what Copilot drafted. Compare with `solutions/`.

Check (5 min):
- `/skills` shows both skills for everyone.
- Right-click in the Chat view > Diagnostics. No errors.
- Ask the room: "What decides when a skill runs?" Answer: the description.

### M4 Custom agents (60 min)

Teach (10 min):
- A custom agent is a specialist colleague. You pick it in the dropdown. Then every message goes to that colleague.
- One file: `.github/agents/<name>.agent.md`. Three parts: who (name, description), toolbox (`tools`), job description (the body).
- Tools are permissions. `search` = it can read files. `edit` = it can change files. No `edit` = it cannot change anything.
- Give an agent only the tools its job needs. This idea is called "least privilege". Smallest toolbox that works.
- Agents can use skills. The agent is the person. The skills are the recipe cards on the shelf.
- Skill or agent? You *call* a skill, or Copilot loads it when needed. You *switch to* an agent, and it stays for the whole chat.
- Type `/agents` to see all agents.

Show (10 min):
1. Gear icon > Agents tab > New Agent (Workspace). Name: `requirement-reviewer`.
2. Fill the header: name, description, `tools: ['search']`. Use the tool picker in the editor if it is there.
3. Paste the body from `solutions/requirement-reviewer.agent.md`.
4. Save. Pick "Requirement Reviewer" in the dropdown. Send: "Review #requirements-raw.md".
5. Send: "Now fix REQ-02 in the file." It cannot. Point at the toolbox. This is the point.

Manual path if the editor is missing: Explorer > right-click `.github/agents` > New File `requirement-reviewer.agent.md`.

Lab 4a (25 min): build Requirement Reviewer.
1. Create `.github/agents/requirement-reviewer.agent.md`.
2. Header: name, description, `tools: ['search']`.
3. Body: who it is, 4 steps, 3 style rules. Tell it to use the `requirement-quality-check` skill. Tell it what to answer when someone asks it to edit.
4. Save. Pick the agent in the dropdown. Send: "Review #requirements-raw.md".
5. Check the output: one table, HIGH first, open questions at the end. If not: fix the body. Test again.
6. Send: "Change REQ-07 in the file." Confirm that it does not edit.

Lab 4b (20 min): build Story Writer.
1. Create `story-writer.agent.md`. Header: `tools: ['search', 'edit']`.
2. Body: read the input, use the `story-from-notes` skill, use the `acceptance-criteria` skill, write to `output/stories-<topic>.md`, change no other file. Fast way: `/create-agent` and describe the role. Then fix the draft.
3. Add the `story-from-notes` skill from `solutions/` to your skills folder.
4. Pick Story Writer. Send: "Write user stories from #meeting-notes.md".
5. Open `output/stories-card-blocking.md`. Read it. Find one story that is wrong or missing. Fix the agent body or the skill. Run again.

Check (5 min):
- Both agents are in the dropdown for everyone.
- Reviewer gives a table and cannot edit.
- Story Writer wrote a file in `output/`.

### M5 Put it together. Build your own (45 min)

Show (10 min): the handoff.
- A handoff is a button that appears after an agent finishes. It switches to another agent with a prepared prompt.
- Open `solutions/story-writer.agent.md`. Show the `handoffs` block: label, target agent, prompt.
- Run Story Writer on the meeting notes. Click "Review these stories". Requirement Reviewer opens with the prompt ready. Send it.
- The workflow: notes -> Story Writer -> Reviewer -> fix -> Reviewer. One person, two colleagues, one chain.

Lab 5 (30 min): build your own.
1. Pick one task from your real work. Use the idea list in section 8. Or your own.
2. Decide: rule, skill, or agent? Use card B.
3. Build it. Test it with a real input that is not confidential.
4. Swap laptops with your neighbour. Test each other's skill or agent. Give one improvement.

Show and tell (5 min): 3 volunteers, 1 minute each. What did you build? What did you fix after the test?

### M6 Share. Keep it good. Troubleshoot (20 min)

Teach (10 min):
- Two homes for a skill or an agent. Workspace: `.github/...` inside the team folder. Everyone who has the folder has it. User profile: `~/.copilot/skills/` and `~/.copilot/agents/`. Only you have it.
- Sharing: put the skill folder into the team folder. One owner reviews it and merges it. (Facilitator: decide the process before the day. Simplest: one shared GitLab repo `re-copilot-kit`; participants send the folder to the owner; the owner merges. Show the repo on the projector.)
- A skill is text. Anyone can read it. Treat it like a team template.
- Rules for a good skill: one job, short, concrete examples, the description says when, a date and an author at the bottom.
- Never put in a skill or an agent: passwords, customer data, personal data, internal secrets.
- A skill is not the truth. It is your recipe. Review the output every time.

Do (10 min): the troubleshooting card.
- Walk through card E. Break one thing on the projector (rename the skill folder). Show the symptom. Show Diagnostics. Fix it.
- Give 3 minutes: each pod breaks one thing on purpose and fixes it.

### Wrap-up (5 min)

- Three takeaways: rules are always on, skills are recipe cards, agents are colleagues with a toolbox.
- Homework: build one skill for a real task within 7 days. Share it in the team channel.
- Feedback form. One question: "What will you build first?"

## 6. Starter kit

    re-bootcamp-kit/
      re-copilot-bootcamp.md          <- this file
      CHEATSHEET.md                   <- print, one per person
      starter/                        <- zip and send to participants
        .github/
          copilot-instructions.md     <- 6 house rules (M2)
          skills/README.md            <- empty, participants build here
          agents/README.md            <- empty, participants build here
        samples/
          requirements-raw.md         <- 10 bad requirements (labs 1-4)
          meeting-notes.md            <- workshop notes (lab 4b, 5)
          glossary.md                 <- terms (checklist, lab 5 ideas)
          user-story-example.md       <- gold standard story
        output/README.md              <- agents write here
      solutions/                      <- facilitator only
        .github/
          copilot-instructions.md
          skills/acceptance-criteria/SKILL.md + template.md
          skills/requirement-quality-check/SKILL.md + checklist.md
          skills/ste-rewrite/SKILL.md
          skills/story-from-notes/SKILL.md
          agents/requirement-reviewer.agent.md
          agents/story-writer.agent.md

## 7. Reference cards

### Card A — words and mental models

| Word | Say it like this |
|---|---|
| Workspace | The folder you opened in VS Code. |
| Context | The files Copilot can see right now. |
| Agent mode | Copilot can read and change files for you. |
| Frontmatter | The header of a card. Three lines between `---` marks. |
| YAML | The format of the header. One `key: value` per line. |
| Tool | One thing an agent may do. Read files. Change files. Search the web. |
| Least privilege | The smallest toolbox that does the job. |
| Handoff | A button that passes the work to the next agent. |
| House rules | `copilot-instructions.md`. Always on. |
| Skill | A recipe card. Loaded when the task matches. |
| Custom agent | A colleague with a job description and a toolbox. |

### Card B — which one do I need?

| You need | Use | Why |
|---|---|---|
| A rule that is true in every chat | House rules | Always on. No trigger needed. |
| A repeatable task with steps, a template, or a checklist | Skill | Loaded only when needed. Portable. |
| A role that stays for the whole chat and has its own toolbox | Custom agent | You switch to it. Tools = permissions. |
| A saved prompt you run by hand | Prompt file | Not in this bootcamp. Mention only. |

A colleague (agent) can use many recipe cards (skills). Build the card first. Then build the colleague.

### Card C — SKILL.md rules

    .github/skills/<name>/SKILL.md      shared with the folder
    ~/.copilot/skills/<name>/SKILL.md   only you

    ---
    name: acceptance-criteria
    description: What it does. When to use it. Include the words people will type.
    ---
    # Title
    ## Steps
    1. ...
    ## Rules
    - ...

- `name` = the folder name. Lowercase letters, numbers, hyphens. Max 64 characters. A wrong name = the skill does not load. No error is shown.
- `description` = max 1024 characters. Both WHAT and WHEN.
- A colon inside the description breaks the header. Put the description in quotes, or remove the colon.
- Link extra files: `[template](./template.md)`. No link = Copilot never opens the file.
- Optional: `user-invocable: false` hides the `/` command. `disable-model-invocation: true` = only by hand.
- Fast draft: `/create-skill`. Then fix it. Copilot writes long cards. Cut them.

### Card D — .agent.md rules

    .github/agents/<name>.agent.md      shared with the folder
    ~/.copilot/agents/<name>.agent.md   only you

    ---
    name: Requirement Reviewer
    description: One line. Shows in the chat box as a hint.
    tools: ['search']
    ---
    You are ... . Your job is ... .
    ## Steps
    1. ...
    ## Style
    - ...

- No `edit` in `tools` = the agent cannot change files. Start there. Add `edit` only if the job needs it.
- Name a skill in the body to make the agent use it: "Use the acceptance-criteria skill."
- `handoffs:` = buttons to the next agent. `label`, `agent`, `prompt`, `send: false`.
- Optional: `model:` to pin a model. Leave it out for the bootcamp.
- Fast draft: `/create-agent` in Agent mode. Then cut the draft to what you need.

### Card E — troubleshooting

| Symptom | Likely cause | Fix |
|---|---|---|
| Skill not in `/skills` | Folder name is not equal to `name`. Capital letter, dot, or space in the name. | Rename. Then Command Palette > `Developer: Reload Window`. |
| Skill exists but never runs by itself | Description is vague. It does not say when. | Rewrite the description with the words people type. Or call it with `/name`. |
| Agent not in the dropdown | File is not in `.github/agents`. Or `user-invocable: false`. | Move the file. Check the header. |
| Agent will not change a file | No `edit` tool. | Add `edit` only if the job needs it. |
| Red marks in the header | Colon in the description. Wrong indent. Tab instead of spaces. | Put the value in quotes. Use spaces. |
| My change does nothing | Old chat is still open. | Save. Start a new chat. |
| Copilot ignores a house rule | File too long. Two rules conflict. | Shorten. One rule per line. Remove the conflict. |
| I do not see the error | | Right-click in the Chat view > Diagnostics. |
| Nothing helps | | `Developer: Reload Window`. Then ask a helper with Diagnostics open. |

## 8. Idea list for lab 5

Skills:
- Glossary keeper. Checks new text against `glossary.md`. Flags terms that are not defined.
- Story splitter. Splits a big story into small ones. Each one must be testable on its own.
- NFR helper. Turns "fast" and "secure" into measurable non-functional requirements with a number and a unit.
- Test-case draft. Turns acceptance criteria into a test-case table: ID, steps, expected result.
- Traceability table. Requirement -> story -> acceptance criterion -> test.
- Change impact. Given one changed requirement, lists the stories to re-check.
- Meeting notes to action list. Owner, action, due date.
- Plain-English rewrite. See `solutions/ste-rewrite`.

Agents:
- Stakeholder summarizer. Read-only. Writes a 5-line summary of a requirements file for managers.
- Compliance reviewer. Read-only. Checks stories against a short rule list you give it.
- Story Writer for your own domain. Copy the bootcamp one. Change the format and the IDs.

## 9. Risks

| Risk | Plan |
|---|---|
| Corporate VS Code is too old for skills or the editor | Test one week before. Use the manual paths. Update the screenshots. |
| Premium-request limits hit at 14:00 | Pin one included model in the setup mail. Watch the counter. |
| Agent mode is off by policy | Ask the admin two weeks before. Without it, agents cannot write files. Lab 4b becomes a demo. |
| YAML errors eat the lab time | Give the header as a copy-paste block on the projector. Helpers check headers first. |
| People finish at different speeds | Fast pods start lab 5 early. Slow pods get the solution folder and test it. |
| Confidential data in a test input | Say it in the setup mail and at the start. Use only the samples or made-up data. |
