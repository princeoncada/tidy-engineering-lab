# Learning Workflow

## Purpose

This workflow keeps Tidy codebase study consistent across chatheads.

The goal is maintainer-level understanding.

## Default Mode

Reading and navigation only.

Implementation requires Prince to explicitly say `implementation mode`.

## Session Startup

1. Read lab state: `STUDY_STATE.json`, `PRODUCT_SYNC_STATE.json`, `STUDY_INDEX.md`, and `handoffs/latest.md`.
2. Read `SESSION_INDEX.md` only when Prince asks for previous sessions, restudy targets, or session history.
3. Read the current chapter file.
4. Read product repo source documents fresh: `STATE.json`, `codebase-graph.json`, `docs/CONTEXT_INDEX.md`, `docs/AI_HANDOFF.md`, and `docs/VERSIONING.md`.
5. Report lab state and product state.
6. Confirm the current study target.

## Study Loop

1. Define scope.
2. Read the smallest correct file set.
3. Build a mental model.
4. Walk through specific code.
5. Trace one runtime flow when applicable.
6. Review relevant tests.
7. Identify slop, risk, and missing coverage.
8. Extract senior-level lessons.
9. Record open questions.
10. Close the session with a concise handoff.

## Session History and Restudy Flow

Previous study sessions are tracked in `SESSION_INDEX.md`.

Use session history when Prince wants to review, resume, restudy, or compare older lessons.

| Command | Source | Output |
| --- | --- | --- |
| `/sessions` | `SESSION_INDEX.md` | Compact list of prior study sessions and recommended session target. |
| `/session [session-id]` | `SESSION_INDEX.md` + linked session summary | Recap of what was learned, what files were read, what questions remain, and possible next steps. |
| `/restudy-session [session-id]` | `SESSION_INDEX.md` + linked session summary + current product source-of-truth docs | Sets that session as the active restudy target and refreshes the lesson against current product truth. |
| `/compare-session [session-id]` | `SESSION_INDEX.md` + linked session summary + current product source-of-truth docs | Reports what changed since the session and whether the old lesson is stale. |

`handoffs/latest.md` is only for continuing the most recent session. `SESSION_INDEX.md` is for choosing any previous session.

## Commands

Full command reference lives in `COMMANDS.md`.

| Command | Purpose |
| --- | --- |
| `/help` | Show available study commands, explain command differences, and recommend the best next command. |
| `/start-study [target]` | Start a study session. |
| `/study-target [target]` | Set or change the current target. |
| `/sessions` | List previous study sessions. |
| `/session [session-id]` | Open and summarize one previous study session. |
| `/restudy-session [session-id]` | Set a previous session as the active restudy target. |
| `/compare-session [session-id]` | Compare a previous session against current product truth. |
| `/explain-file [path]` | Walk through one file deeply. |
| `/trace-flow [behavior]` | Trace a behavior across UI, hooks, cache, API, database, and tests where applicable. |
| `/slop-audit` | Review the studied area for risk and code quality. |
| `/self-check` | Quiz Prince on the current material. |
| `/sync-product-version` | Refresh lab tracking from current product source-of-truth files. |
| `/check-lab-drift` | Compare lab state against product truth and report stale or mismatched learning/doc state. |
| `/close-study` | Save session summary, handoff, state updates, chapter updates, session index row, and ledger changes. |
| `/implementation-mode` | Switch to implementation planning. Not allowed by default. |

## Response Footer

At the end of every study response, include a compact footer with:

- **Recommended next step** - the single best next action.
- **Useful commands** - 1 to 3 commands that fit the current state.
- **Questions you can ask** - 1 to 3 plain-English follow-up questions Prince can ask next.
- **Help reminder** - mention `/help` when command discovery would help.

Keep the footer compact and practical. Do not let the footer replace the actual answer.

## Unknown Commands

If Prince uses an undocumented command, do not silently invent behavior. State that it is not currently documented, infer the likely intent if obvious, recommend the closest known command, and point to `/help`.

## Session Close Requirements

At close, update the session summary, latest handoff, relevant chapter, study state, session index, and any affected ledgers.

### `/close-study` Persistence Contract

Every `/close-study` should persist the session in these places:

| Destination | What gets saved |
| --- | --- |
| `sessions/YYYY/MM/[session-id].md` | Full session summary: target, date, product version, files read, concepts learned, mental model, drift found, open questions, next actions, and restudy notes. |
| `handoffs/latest.md` | Compact continuity handoff for the next chat: current study state, latest product state, what was learned, what to do next, and what not to carry forward. |
| `STUDY_STATE.json` | Machine-readable study position: current chapter, completed chapters, current/next target, open question count, slop finding count, and last updated date. |
| Current chapter file | Chapter progress, session links, mental model updates, senior lessons, self-check items, and completion status when appropriate. |
| `SESSION_INDEX.md` | One searchable row for the session with session ID, date, title, chapter/target, product version, status, summary file, and restudy command. |
| `ledgers/open-questions.md` | Any unresolved questions that should survive the chat. |
| `ledgers/slop-log.md` | Any bloat, drift, unclear ownership, weak test, or risk finding worth tracking. |
| `PRODUCT_VERSION_MATRIX.md` | Only when the session studied or reviewed a product version enough to update its lab status. |

Do not save raw transcript, private scratchpad, or unverified product claims. Save only compact, reusable learning state.
