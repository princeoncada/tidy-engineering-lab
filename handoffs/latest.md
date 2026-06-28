# Latest Study Handoff

## Status

Study repo synced to the latest pushed product source-of-truth state on 2026-06-28 and the study session was closed.

This is a study-repo-only sync/closeout handoff. No product code was changed by the assistant.

## Product repo

`princeoncada/tidy`

## Product state read during sync

* Version: 3.6.3
* State: stable
* Phase: 3.6.3
* Phase title: Agent Workflow Realignment
* Next phase in product source of truth: 3.6.4 - Workspace OS Rebase RFC
* Last updated: 2026-06-28

## Latest implementation checked

Product source-of-truth now records 3.6.3 as stable. The roadmap shows the first Planned item as 3.6.4 - Workspace OS Rebase RFC.

Important implementation / workflow surfaces visible in the latest product handoff/source:

* The dashboard remains Replicache-only for render/write behavior; legacy dashboard tRPC render, pending outbox overlay, local outbox write-capture/replay worker, `/api/sync`, and local-outbox sync badge paths remain retired from the 2.0.9 arc.
* Current user actions include list/item/tag/view CRUD, item note editing, status and assignee changes, board interactions, sharing/workspace management, read-only history, replay-based revert, and theme switching.
* Current key product surfaces include `components/ReplicacheProvider.tsx`, `hooks/useReplicacheDashboard.ts`, `hooks/useDashboardMutations.ts`, `lib/sync/replicache/*`, `lib/sync/server-apply.ts`, `lib/dashboard/server-read.ts`, `lib/collab/*`, `components/item/ItemDetailPanel.tsx`, `components/item/ItemNotesField.tsx`, `components/board/*`, `lib/realtime/*`, `components/history/HistoryPanel.tsx`, `lib/history/*`, `trpc/routers/revertRouter.ts`, `components/sharing/*`, and `lib/sync/permissions.ts`.
* 3.5.2 added replay-based, flag-gated revert through `revertToLedgerEntry`, reconstructing prior state from the user-scoped ledger and writing corrective operations through server-apply with the existing poke path.
* 3.6.0-3.6.3 added Tidy stewardship docs/audits/cleanup and realigned the AI workflow. `docs/tidy/*` supports source-of-truth mapping, staleness audit, cleanup backlog, and agent support checklists; it is not a second roadmap or handoff owner.
* 3.6.3 role model: ChatGPT is second-opinion/docs-workflow auditor with scoped support writes; Claude Code is future-plan architect and Codex-ready implementation explainer; Codex implements and reports automated validation evidence; user/controller owns manual product validation and closeout.
* Next product direction is 3.6.4 - Workspace OS Rebase RFC, then 4.0.0 - Workspace OS Product Model Rebase. The app is being prepared to move beyond todo-list productivity into a lightweight workspace OS while preserving Replicache, Yjs, shadcn/Radix, semantic tokens, local-first behavior, and small vertical phases.

## Study repo sync changes

* `PRODUCT_SYNC_STATE.json` now points to product 3.6.3 stable.
* `STUDY_STATE.json` now records the latest product read as 3.6.3 stable and points to the 2026-06-28 closeout summary.
* `STUDY_INDEX.md` now marks the lab as synced through 3.6.3 and adds a planned study track for 3.5.2-3.6.3 revert / stewardship / workflow realignment.
* `PRODUCT_VERSION_MATRIX.md` now tracks product releases through 3.6.3.
* `chapters/01-pre-versioning-product-baseline.md` now carries a 3.6.3 sync overlay, updated mental model, study questions, and risks.
* `chapters/3.5.2-3.6.3-revert-stewardship-workflow-series.md` was added as a placeholder study chapter for the newly synced arc.
* `sessions/2026/06/2026-06-28-3.6.3-workflow-realignment-sync-closeout.md` was added as the closeout summary.

## Recommended next study action

Recommended study target:

`2.0.4-2.0.9-replicache-hardening-legacy-retirement-review`

Reason: the lab still has not deeply reviewed the transition from early Replicache/sharing into a fully Replicache-only dashboard with Yjs notes, realtime poke authorization, dead config removal, and legacy path retirement. That boundary should be understood before studying the later shell/collaboration, item panel, board/presence, history/revert, stewardship/workflow, or Workspace OS RFC arcs.

## Carry forward

* `princeoncada/tidy` owns product truth.
* `princeoncada/tidy-engineering-lab` owns learning/sync truth.
* Read product source-of-truth fresh before making product claims.
* Do not write to `princeoncada/tidy` in normal study/review mode.
* Do not enter implementation unless Prince explicitly says `implementation mode`.
* 3.6.4 is now the next pushed product phase, but study should still begin with the 2.0.4-2.0.9 catch-up unless Prince explicitly changes the study order.
