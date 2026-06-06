# Tidy Engineering Lab Commands

Use `/help` whenever you forget what commands exist or are unsure what to run next.

## Command Reference

| Command | Purpose | When to use |
| --- | --- | --- |
| `/help` | Show this command list, explain command differences, and recommend the best next command. | Use when confused, when you forget a command name, or when you want to know what options exist. |
| `/start-study [target]` | Start or resume a guided study session for a chapter, file, behavior, concept, or restudy target. | Use at the beginning of a study block. |
| `/study-target [target]` | Change the current learning target without closing the session. | Use when the current target is wrong or too broad. |
| `/sessions` | List previous study sessions from `SESSION_INDEX.md`. | Use when you want to review what has already been studied. |
| `/session [session-id]` | Open and summarize one previous session. | Use when you want a recap before deciding whether to restudy it. |
| `/restudy-session [session-id]` | Set a previous session as the current study target and refresh it against current product truth. | Use when an old lesson is important, stale, or worth repeating. |
| `/compare-session [session-id]` | Compare a previous session against current product truth and identify what changed. | Use when product versions moved forward after the session. |
| `/explain-file [path]` | Explain one file deeply: role, imports, exports, flow, risks, and tests. | Use when a specific file is confusing. |
| `/trace-flow [behavior]` | Trace one behavior across UI, hooks, cache, API, database, and tests where applicable. | Use when you want to understand how a feature works end to end. |
| `/slop-audit` | Review the studied area for bloat, drift, fragile design, weak tests, or unclear ownership. | Use after studying a file, flow, or doc surface. |
| `/self-check` | Quiz Prince on the current material and identify weak understanding. | Use before closing a study session or moving to a harder topic. |
| `/sync-product-version` | Refresh lab tracking files from the current product repo state. | Use when product `STATE.json` moved ahead of the lab. |
| `/check-lab-drift` | Compare lab learning state against product truth and report stale handoffs, chapters, version tracking, or product-doc drift. | Use after sync, before closeout, or when docs feel inconsistent. |
| `/close-study` | Save the session summary, latest handoff, state updates, chapter progress, session index row, and ledgers when needed. | Use when the current learning session is done. |
| `/implementation-mode` | Switch out of default study mode into implementation planning. | Only use when Prince explicitly wants implementation planning. Product code still must not be edited unless implementation mode is explicit. |

## Session Discovery Commands

`/sessions`, `/session [session-id]`, `/restudy-session [session-id]`, and `/compare-session [session-id]` use `SESSION_INDEX.md` as their starting point.

- `/sessions` shows the available past sessions.
- `/session [session-id]` summarizes one past session as recorded.
- `/restudy-session [session-id]` turns that past session into the active study target and checks it against current product truth.
- `/compare-session [session-id]` focuses only on what changed between that old session and current product truth.

## Response Footer Contract

At the end of every study response, include a compact footer with:

1. **Recommended next step** - the single best next action.
2. **Useful commands** - 1 to 3 commands that fit the current state.
3. **Questions you can ask** - 1 to 3 plain-English questions Prince can ask next.
4. **Help reminder** - mention `/help` when command discovery would help.

Keep the footer short. Do not bury the actual answer under command suggestions.

## Unknown Command Handling

If Prince uses a command that is not listed here:

1. Do not invent behavior silently.
2. Infer the likely intent if obvious.
3. State that the command is not currently documented.
4. Recommend the closest known command.
5. Suggest `/help` for the full list.

## Default Study Boundary

The lab is reading/navigation/study by default. Writes are allowed in `princeoncada/tidy-engineering-lab` for learning state, handoffs, chapters, ledgers, command docs, session index, and summaries. Do not write to `princeoncada/tidy` unless Prince explicitly enters implementation mode and the task permits it.
