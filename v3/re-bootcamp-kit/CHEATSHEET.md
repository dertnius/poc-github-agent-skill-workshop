# Copilot cheat sheet for requirements engineers

## Open things
- Chat view: `Ctrl+Alt+I`, or the Chat icon in the title bar.
- New chat: the `+` icon in the Chat view.
- Command Palette: `Ctrl+Shift+P`.
- Customizations editor: gear icon in the Chat view. Or Command Palette > `Chat: Open Customizations`.

## Give Copilot context
- Context = the files Copilot can see.
- Type `#` and pick a file. Or drag the file into the chat box.
- Start a new chat for a new topic.

## Three ways to teach Copilot
| You need | Use | File |
|---|---|---|
| A rule that is always true | House rules | `.github/copilot-instructions.md` |
| A repeatable task with steps or a template | Skill | `.github/skills/<name>/SKILL.md` |
| A role with its own toolbox | Custom agent | `.github/agents/<name>.agent.md` |

## Skill rules
- Folder name = `name` in `SKILL.md`. Lowercase letters, numbers, hyphens only.
- `description` says WHAT the skill does and WHEN to use it. This line decides when Copilot loads the skill.
- Run a skill by hand: type `/name` in the chat.
- See all skills: type `/skills`.
- Let Copilot draft a skill: type `/create-skill` and describe it.

## Agent rules
- Pick the agent in the dropdown of the Chat view.
- `tools` = what the agent may do. No `edit` tool = the agent cannot change files.
- See all agents: type `/agents`.
- Let Copilot draft an agent: type `/create-agent` and describe the role.

## When something does not work
1. Save the file (`Ctrl+S`).
2. Start a new chat.
3. Right-click in the Chat view > `Diagnostics`. Read the error.
4. Still broken: `Ctrl+Shift+P` > `Developer: Reload Window`.
5. Still broken: ask a helper. Show the Diagnostics screen.
