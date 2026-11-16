---
name: discovery-interview
description: Start or resume the interactive MineCremental game-design discovery interview in the main conversation.
disable-model-invocation: true
---

# Start MineCremental Discovery Interview

This skill must execute in the **current main conversation**. Do not run the interviewer as a subagent and do not fork the interview into another context.

## Required reads

Use the Read tool to load the full content of:

1. `discovery/agents/interviewer.md`
2. `discovery/DISCOVERY_BRIEF.md`
3. `discovery/HISTORICAL_BASELINE.md`
4. `discovery/WORKFLOW.md`
5. `discovery/decisions/decision-log.md`
6. `discovery/interview/README.md`
7. Latest relevant interview summary.
8. `discovery/final/GAME_VISION.md`, if present.

Follow `discovery/agents/interviewer.md` as the canonical role prompt. Do not paraphrase it into a shorter or weaker set of rules.

If a required canonical file is missing, stop and report the exact path. Do not invent replacement instructions.

## Execution

- Resume the latest unfinished Discovery thread when one exists.
- Do not ask the author to repeat decisions or preferences already documented.
- Treat `HISTORICAL_BASELINE.md` as a bias register, not a requirements document.
- Conduct a direct adaptive conversation with the author in the current main session.
- Ask one high-value question at a time by default.
- Do not display a complete questionnaire.
- Do not begin with mod selection, version, loader, Create, dimensions, prestige or implementation details.
- Keep the interviewer in the main session. You may delegate focused research to `discovery-researcher` and read-only audits to `discovery-reviewer`, but these agents do not conduct the interview.
- Respect file boundaries and author decision authority from the canonical prompt.

## Session close

When the author pauses or closes the session, follow the canonical prompt to:
- Summarize what was explored.
- Create the next `discovery/interview/session-NNN.md` without overwriting history.
- Update `discovery/decisions/decision-log.md` only with explicit author-confirmed changes.
- Update `discovery/final/GAME_VISION.md` as a single living artifact, keeping `status: DRAFT` until the author explicitly approves it.

Do not create `GAME_VISION_DRAFT.md`.
