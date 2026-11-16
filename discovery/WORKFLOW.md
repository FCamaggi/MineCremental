# MineCremental: Discovery Workflow

## Canonical references (all versioned in this repository)

- [Discovery Brief](DISCOVERY_BRIEF.md): shared context and decision authority.
- [Historical Baseline](HISTORICAL_BASELINE.md): inherited assumptions, proposals, source paths and statuses.
- [Discovery Strategy](DISCOVERY_STRATEGY.md): methodology, roles and exit criteria.
- [Workspace Setup](WORKSPACE_SETUP.md): structure, setup and Claude Code integration.
- [Interviewer instructions](agents/interviewer.md): canonical main-session prompt.
- [Researcher instructions](agents/researcher.md): canonical research subagent prompt.
- [Reviewer instructions](agents/reviewer.md): canonical review subagent prompt.

These references are committed with the project. The workflow must not depend on files that exist only in a chat or a local temporary download.

## Stage 0: Initialize

1. Ensure this workspace and Claude Code files exist.
2. Read `DISCOVERY_BRIEF.md`, `HISTORICAL_BASELINE.md`, this file and `DISCOVERY_STRATEGY.md`.
3. Inspect existing interviews, decisions, research, reviews and final artifacts.
4. Do not rewrite `CLAUDE.md` or historical `docs/`.

## Stage 1: Concept interview

1. Start the main Claude Code session at repository root.
2. Invoke `/discovery-interview`.
3. The skill loads `agents/interviewer.md` and keeps the interviewer in the main session.
4. Explore identity, fantasy, desired experience and high-impact unknowns.
5. Create/update `final/GAME_VISION.md` with `status: DRAFT`.
6. Save session summary and update decision records.

## Stage 2: Targeted research

1. Derive a focused research brief from a design question or technical uncertainty.
2. Delegate to `discovery-researcher`.
3. Researcher reads `agents/researcher.md`, the brief, relevant decisions and sources.
4. Researcher writes an evidence report under `research/` only.
5. Main session evaluates findings and their design implications.

## Stage 3: Design alternatives

The main interviewer/designer uses evidence to present materially different options, gameplay consequences, trade-offs and uncertainties. Research recommendations are not decisions.

## Stage 4: Contrast interview

Discuss alternatives directly with the author. Record explicit decisions in `decisions/decision-log.md`. Update `GAME_VISION.md` only to reflect what the author approved. Keep `status: DRAFT` until explicit approval.

## Stage 5: Review

Delegate a read-only audit to `discovery-reviewer`. It returns findings to the main session. The main session saves the report under `reviews/` and resolves findings with the author.

## Stage 6: Consolidation

After the author approves the vision and no critical coherence issue remains, consolidate the GDD and supporting documents. Keep unresolved matters visible in `final/OPEN_QUESTIONS.md`.

## File ownership and write boundaries

| Path | Owner | Rules |
|---|---|---|
| `docs/`, `CLAUDE.md`, `README.md`, `src/` | Existing project | Read-only during Discovery. |
| `discovery/interview/` | Main session/interviewer | One new session file per interview; never overwrite history. |
| `discovery/decisions/` | Main session/interviewer | Add/supersede entries; never silently rewrite decisions. |
| `discovery/research/` | Researcher | Evidence and recommendations only; no product decisions. |
| `discovery/reviews/` | Main session | Save subagent review reports; preserve audit history. |
| `discovery/final/` | Main session after author review | Draft/consolidated design with traceability. |
| `.claude/` | Project configuration | Change only during explicit setup/configuration work. |

## Completion

Discovery is not complete because all headings were filled. It is complete when the author approves the vision and the design has enough coherence, evidence, traceability and scope definition for implementation planning.
