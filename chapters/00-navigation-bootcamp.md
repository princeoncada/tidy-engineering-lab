# Navigation Bootcamp

## Status

Completed on 2026-06-06.

## Purpose

Learn repo navigation, source-of-truth docs, safe read sets, and the default reading workflow.

## Related Product Versions

* 1.9.5 - Dashboard Mutation to Outbox Wiring
* Next product phase during study: 1.9.6 - Durable Pending-Write Integration

## Files Read

### Study repo

* `STUDY_STATE.json`
* `PRODUCT_SYNC_STATE.json`
* `STUDY_INDEX.md`
* `LEARNING_WORKFLOW.md`
* `COMMANDS.md`
* `CHATHEAD_OPENER.md`
* `SESSION_INDEX.md`
* `handoffs/latest.md`
* `ledgers/open-questions.md`
* `ledgers/slop-log.md`

### Product repo

* `STATE.json`
* `codebase-graph.json`
* `docs/CONTEXT_INDEX.md`
* `docs/AI_HANDOFF.md`
* `docs/VERSIONING.md`
* `docs/FUTURE_PLANS.md`
* `docs/WORKFLOW.md`
* `docs/CODEX_RULES.md`
* `docs/COMPACT_STRATEGY.md`
* `docs/DECISIONS.md`
* `.claude/skills/tidy-session-clone/SKILL.md`
* `ai-harness/README.md`

## Mental Model

Tidy's docs act as an AI control system.

* `STATE.json` owns current product truth: version, state, phase, phase title, and next phase.
* `docs/FUTURE_PLANS.md` owns roadmap truth.
* `docs/CONTEXT_INDEX.md` owns read routing and smallest-correct-context selection.
* `docs/VERSIONING.md` owns versioning rules and history.
* `docs/AI_HANDOFF.md` owns current architecture/risk handoff, but can drift if lower narrative sections are not updated.
* `docs/CODEX_RULES.md` owns implementation boundaries.
* `docs/WORKFLOW.md` owns the phase/process constitution.
* `.claude/skills/*` owns repeated operational execution procedures.
* The study repo owns learning truth only, not product truth.

## Runtime Flows

Not applicable. This chapter focused on documentation navigation and workflow orientation, not product runtime behavior.

## Tests

Not applicable. This chapter did not inspect product tests deeply.

## Slop/Risk Review

Findings discovered during study:

1. Product `AI_HANDOFF.md` top state is current, but lower guidance still references older 1.5.x and 1.6.x continuation work.
2. Product `VERSIONING.md` has stable version rows with `(in progress)` notes.
3. Product role docs still describe ChatGPT as architect/scoper, while Prince's actual workflow now uses Claude Code as architect/scoper/planner/validator/prompt builder, Codex as boosted implementer, and ChatGPT as reviewer.
4. `FUTURE_PLANS.md` and `VERSIONING.md` both carry historical version information, creating possible history duplication.
5. Retired/pointer workflow surfaces may be removable or compressible after validation.

## Senior Lessons

* Always identify the owner of a fact before trusting it.
* Treat `STATE.json` as the product state oracle, but compare `STATE.json.nextPhase` with the first Planned item in `FUTURE_PLANS.md`.
* Do not read historical logs by default.
* Do not delete old docs blindly. Classify them as active, routing-only, historical, deprecated, or removable.
* Drift usually appears when one fact is duplicated across multiple docs.
* Study repo sync and product repo truth are separate. The lab can be current or stale independently of the product.

## Self-Check Questions

1. Which file owns the current product version and phase?
2. Which file owns the roadmap backlog?
3. What should happen if `STATE.json.nextPhase` disagrees with the first Planned item in `FUTURE_PLANS.md`?
4. Why is `codebase-graph.json` not a source of truth?
5. What is the difference between `handoffs/latest.md` and `SESSION_INDEX.md`?
6. Why should `PHASE_LOG.md` and session logs not guide active implementation by default?
7. What product-doc drift was found during this session?

## Session Links

* `sessions/2026/06/2026-06-06-navigation-bootcamp.md`
* Restudy command: `/restudy-session 2026-06-06-navigation-bootcamp`

## Next Study Target

`01-pre-versioning-product-baseline`
