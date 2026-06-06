# Learning Workflow

## Purpose

This workflow keeps Tidy codebase study consistent across chatheads.

The goal is maintainer-level understanding.

## Default Mode

Reading and navigation only.

Implementation requires Prince to explicitly say `implementation mode`.

## Session Startup

1. Read lab state: `STUDY_STATE.json`, `PRODUCT_SYNC_STATE.json`, `STUDY_INDEX.md`, and `handoffs/latest.md`.
2. Read the current chapter file.
3. Read product repo source documents fresh: `STATE.json`, `codebase-graph.json`, `docs/CONTEXT_INDEX.md`, `docs/AI_HANDOFF.md`, and `docs/VERSIONING.md`.
4. Report lab state and product state.
5. Confirm the current study target.

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

## Commands

| Command | Purpose |
| --- | --- |
| `/start-study [target]` | Start a study session. |
| `/study-target [target]` | Set or change the current target. |
| `/explain-file [path]` | Walk through one file deeply. |
| `/trace-flow [behavior]` | Trace a behavior across UI, hooks, cache, API, database, and tests where applicable. |
| `/slop-audit` | Review the studied area for risk and code quality. |
| `/self-check` | Quiz Prince on the current material. |
| `/close-study` | Save session summary, handoff, state updates, and ledger changes. |
| `/implementation-mode` | Switch to implementation planning. Not allowed by default. |

## Session Close Requirements

At close, update the session summary, latest handoff, relevant chapter, study state, and any affected ledgers.
