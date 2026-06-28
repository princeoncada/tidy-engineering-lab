# Pre-Versioning Product Baseline

## Status

Checkpointed after 2026-06-13 repo-review/support session, updated after 2026-06-14 product-sync catch-up, resynced to product 3.2.9 on 2026-06-22, resynced to product 3.5.1 on 2026-06-26, and resynced to product 3.6.3 on 2026-06-28.

This chapter has not been completed as a full baseline study. It carries practical product-review checkpoints so the next session does not lose context.

## Current Product Sync Overlay

Latest product source-of-truth read during sync:

* Version: 3.6.3
* State: stable
* Phase: 3.6.3
* Phase title: Agent Workflow Realignment
* Next phase: 3.6.4 - Workspace OS Rebase RFC
* Last updated: 2026-06-28

The lab is now metadata-synced through product 3.6.3, but the implementation study backlog is large. The lab still needs to study the 2.0.4-2.0.9 Replicache hardening / Yjs notes / legacy retirement sequence, the 2.1-2.2 deploy and visual readiness sequence, the 3.0-3.2 collaboration shell and sync-hardening sequence, the 3.3-3.5.1 item panel / presence / history sequence, and the 3.5.2-3.6.3 revert / stewardship / workflow sequence before treating the 3.6.4 Workspace OS Rebase RFC as study-ready.

## Purpose

Understand the actual app architecture before versioned workflow history and maintain enough product-direction context to support branch reviews safely.

## Related Product Versions

### Previously synced baseline

* 1.9.29 - Direct-Write Retirement & Default Dexie-First - stable 2026-06-13
* 1.9.30 - Delete Outbox Payload Validation Fix - stable 2026-06-13
* 1.9.31 - E2E Auth-Suite Sync-Timing Assertion Hardening - stable 2026-06-13
* 1.9.32 - Local-First Dashboard Architecture Closeout - stable 2026-06-14
* 1.10.0 - Copy and Metadata Hygiene - stable 2026-06-14
* 1.10.1 - Landing Page Branding Polish - stable 2026-06-14
* 2.0.0 - Replicache Read-Path Inversion (Local Store as Render Source) - stable 2026-06-14
* 2.0.1 - Fractional Indexing for Order - stable 2026-06-14
* 2.0.2 - Supabase Broadcast Realtime Poke - stable 2026-06-14
* 2.0.3 - Sharing & Permissions - stable 2026-06-14

### Synced on 2026-06-22

* 2.0.4 - Replicache Pull Cookie Monotonicity Fix - stable 2026-06-14
* 2.0.5 - Share Redeem Error UX Hardening - stable 2026-06-14
* 2.0.6 - Yjs Collaborative Item Notes - stable 2026-06-16
* 2.0.7 - Realtime Poke Send Authorization - stable 2026-06-16
* 2.0.8 - Remove Dead Replicache License Config - stable 2026-06-16
* 2.0.9 - Retire Legacy Overlay / Outbox-Render / tRPC-Render Paths - stable 2026-06-17
* 2.1.0 - Deploy Env Documentation - stable 2026-06-17
* 2.1.1 - Build/Migration Readiness - stable 2026-06-18
* 2.1.2 - Production Smoke Checklist - stable 2026-06-18
* 2.2.0 - Visual Review Pass - stable 2026-06-18
* 2.2.1 - Retire test:e2e:replicache Render Gate - stable 2026-06-18
* 2.2.2 - View Create Idempotency Hardening - stable 2026-06-18
* 2.2.3 - seriesComplete Flag Reconciliation - stable 2026-06-19
* 3.0.0 - Collab Arc Roadmap Pin - stable 2026-06-19
* 3.0.1 - Version History Re-Ownership - stable 2026-06-19
* 3.0.2 - Repo, Docs & Skills Cleanup - stable 2026-06-19
* 3.0.3 - Startup Context Budget Rebaseline - stable 2026-06-19
* 3.0.4 - Design System Source of Truth - stable 2026-06-19
* 3.1.0 - Sync Latency Measurement Spike - stable 2026-06-19
* 3.1.1 - Sync Latency Fix - stable 2026-06-19
* 3.1.2 - Automated Two-User Sync-Latency Harness - stable 2026-06-20
* 3.2.0 - Design Tokens & Dark Mode - stable 2026-06-20
* 3.2.1 - Collapsible Left Sidebar & Canvas Shell - stable 2026-06-20
* 3.2.2 - Workspace Navigation - stable 2026-06-20
* 3.2.3 - Views Reorder Snap-Back Patch - stable 2026-06-20
* 3.2.4 - Sidebar Navigation Redesign - stable 2026-06-20
* 3.2.5 - List Item Cross-List Move Snap-Back Patch - stable 2026-06-21
* 3.2.6 - Sidebar Accordion Conversion & Collapsed-Avatar Open - stable 2026-06-21
* 3.2.7 - Workspace Section Parity & Selection Styling - stable 2026-06-21
* 3.2.8 - Concurrent-Pull Resilience & Fast-Switch View Convergence - stable 2026-06-22
* 3.2.9 - Create-Path Idempotency Hardening (TOCTOU) - stable 2026-06-22

### Synced on 2026-06-26

* 3.3.0 - Item Detail Panel & Notes - stable 2026-06-22
* 3.3.1 - Item Properties (Status & Assignee) - stable 2026-06-23
* 3.4.0 - Presence Transport Spike - stable 2026-06-23
* 3.4.1 - Multiplayer Board - stable 2026-06-24
* 3.4.2 - Collaboration & Sharing UX - stable 2026-06-24
* 3.4.3 - Presence Transport Hardening - stable 2026-06-24
* 3.4.4 - Live Presence - stable 2026-06-24
* 3.4.5 - Board Progress & Rollups - stable 2026-06-26
* 3.5.0 - Mutation Ledger - stable 2026-06-26
* 3.5.1 - Time-Travel Read - stable 2026-06-26

### Synced on 2026-06-28

* 3.5.2 - Revert - stable 2026-06-26
* 3.6.0 - Tidy Stewardship Foundation - stable 2026-06-27
* 3.6.1 - Repo Staleness Audit - stable 2026-06-28
* 3.6.2 - Docs Consolidation Cleanup - stable 2026-06-28
* 3.6.3 - Agent Workflow Realignment - stable 2026-06-28
* Next product source-of-truth phase: 3.6.4 - Workspace OS Rebase RFC

## Files Read / Used During 1.9.29 Session

Product repo:

* `STATE.json`
* `docs/AI_HANDOFF.md`
* `docs/FUTURE_PLANS.md`
* `docs/VERSIONING.md`
* `components/list/ListsContainer.tsx`
* `components/list/ListItemComponent.tsx`
* `components/SyncStatusBadge.tsx`
* `hooks/use-sync-status-surface.ts`
* `hooks/use-offline-replay-trigger.ts`
* `trpc/client.tsx`
* `app/api/sync/route.ts`
* `lib/sync/offline-write-prototype.ts`
* `lib/sync/sync-status-surface.ts`
* `lib/sync/sync-batch-contract.ts`
* `lib/sync/sync-endpoint-contract.ts`
* `lib/local-db/outbox-repository.ts`

Study repo:

* `STUDY_STATE.json`
* `PRODUCT_SYNC_STATE.json`
* `handoffs/latest.md`

## Files Read During 3.2.9 Sync

Product repo:

* `STATE.json`
* `codebase-graph.json`
* `docs/CONTEXT_INDEX.md`
* `docs/AI_HANDOFF.md`
* `docs/FUTURE_PLANS.md`
* `docs/VERSIONING.md`

Study repo:

* `STUDY_STATE.json`
* `PRODUCT_SYNC_STATE.json`
* `STUDY_INDEX.md`
* `PRODUCT_VERSION_MATRIX.md`
* `handoffs/latest.md`
* `chapters/01-pre-versioning-product-baseline.md`

## Files Read During 3.5.1 Sync

Product repo:

* `STATE.json`
* `codebase-graph.json`
* `docs/CONTEXT_INDEX.md`
* `docs/AI_HANDOFF.md`
* `docs/FUTURE_PLANS.md`
* `docs/VERSIONING.md`

Study repo:

* `STUDY_STATE.json`
* `PRODUCT_SYNC_STATE.json`
* `STUDY_INDEX.md`
* `PRODUCT_VERSION_MATRIX.md`
* `handoffs/latest.md`
* `chapters/01-pre-versioning-product-baseline.md`

## Files Read During 3.6.3 Sync / Closeout

Product repo:

* `STATE.json`
* `docs/FUTURE_PLANS.md`
* `docs/AI_HANDOFF.md`
* `docs/WORKFLOW.md`
* `docs/CODEX_RULES.md`
* `docs/VERSIONING.md`

Study repo:

* `STUDY_STATE.json`
* `PRODUCT_SYNC_STATE.json`
* `STUDY_INDEX.md`
* `PRODUCT_VERSION_MATRIX.md`
* `handoffs/latest.md`
* `chapters/01-pre-versioning-product-baseline.md`
* `chapters/3.3.0-3.5.1-item-panel-presence-history-series.md`

## Mental Model

Tidy 1.9.x delivered the local-first write path: Dexie-first dashboard writes by default with bounded batch sync to the server. The sync status badge was a real outbox surface that reported pending, syncing, and failed local outbox work rather than acting as decoration.

The 2.0.x arc changed the read/render model: the dashboard renders from the Replicache local store by default and later retired the old overlay/outbox-render/tRPC-render compatibility paths. As of 2.0.9, Replicache is the dashboard render/write spine.

2.0.3 added sharing and permissions on top of Replicache. 2.0.6 added Yjs collaborative item notes, while 2.0.7 fixed realtime poke authorization and 2.0.9 retired legacy dashboard paths.

The 3.0 arc pins Tidy's collaboration direction: one Replicache sync spine for web and future mobile, presence separate from Replicache, existing workspaces kept, and design governed by `docs/design.md`.

The 3.1 arc measured and fixed sync latency. The 3.2 arc introduced design tokens, dark mode, the collapsible sidebar/canvas shell, workspace navigation, sidebar UX refinements, drag/drop snap-back fixes, concurrent-pull resilience, and create-path idempotency hardening.

The 3.3 arc adds an item detail panel, moves notes into that panel, and adds structured item properties such as status and assignee while keeping those properties on the Replicache spine.

The 3.4 arc introduces the multiplayer board, collaboration/sharing UX polish, and live presence. Presence is intentionally separate from Replicache: structural sync stays in Replicache while cursors/typing/who-is-here use the realtime presence transport.

The 3.5 arc adds a mutation ledger, read-only time-travel/history view, and replay-based revert/write-back. 3.5.2 uses ledger replay to reconstruct prior state and writes corrective operations through server-apply with the existing Replicache/poke path.

The 3.6 arc prepares the repo for the Workspace OS pivot: `docs/tidy/*` acts as a support layer for source-of-truth mapping, staleness audit, cleanup backlog, and agent support checklists; 3.6.3 realigns roles so ChatGPT is the second-opinion/docs-workflow auditor, Claude Code is the future-plan architect and Codex-ready implementation explainer, Codex implements and reports automated validation evidence, and the user/controller owns manual validation and closeout.

## Runtime Flows Observed From 1.9.29 Session

1. Dashboard mounted under `TRPCReactProvider`.
2. `OfflineReplayTrigger` mounted globally and initialized replay after Supabase user resolution.
3. Local Dexie/outbox operations were read by the sync status surface.
4. `/api/sync` validated each operation and returned per-operation statuses even when the HTTP response was 200.
5. Empty-payload removal operations were rejected by validation and remained visible as failed local outbox rows.

This flow is historical. Product truth now says the old local outbox render/replay/status surface and `/api/sync` dashboard batch endpoint were retired by the 2.0.9 Replicache-only transition.

## Latest 3.6.3 Study Questions

* How did 2.0.4 fix Replicache pull cookie monotonicity, and what failure did it prevent?
* How did 2.0.6 introduce Yjs item notes while keeping notes outside Replicache entity storage?
* How did 2.0.7 restore realtime poke authorization for shared-change propagation?
* Which old dashboard paths did 2.0.9 remove, and which sync/apply contracts remained because Replicache still uses them?
* What did 3.1.0 measure, and how did 3.1.1/3.1.2 turn that spike into a repeatable sync-latency proof?
* How do 3.2.0-3.2.7 reshape the app shell, workspace navigation, theme tokens, and sidebar behavior?
* How does 3.2.8 harden concurrent pull behavior and selected-view convergence?
* How does 3.2.9 close the `findUnique` -> `create` TOCTOU race in `lib/sync/server-apply.ts`?
* How did 3.3.0 move item notes into the item detail panel without changing the Yjs note document boundary?
* How do status, assignee, and board order sync through the existing Replicache item mutation path?
* How does 3.4 keep live presence separate from structural Replicache sync?
* What proof distinguishes the 3.4.0 presence spike, 3.4.3 transport hardening, and 3.4.4 UI?
* How does 3.5.0 record mutation history without turning rejected/no-op mutations into history entries?
* What does 3.5.1 expose as read-only time travel, and how does 3.5.2 write corrective revert operations without creating a second sync path?
* What does the `docs/tidy/*` support layer own, and which product/workflow facts must remain owned elsewhere?
* How did 3.6.3 change the ChatGPT / Claude Code / Codex / user-controller role model?
* What must 3.6.4 decide before the 4.0 Workspace OS Product Model Rebase begins?

## Tests / Validation Evidence From 1.9.29 Session

Reported by Prince before 1.9.29 merge/promotion:

* `git status --short` clean
* `./scripts/validate.ps1` passed: 16/16
* `npm run test:ci` passed: typecheck, lint, 402 unit tests, 5 unauthenticated e2e
* `npm run test:e2e:auth` passed: 31 passed, 1 skipped

No local validation was run during the 2026-06-22, 2026-06-26, or 2026-06-28 lab sync because these were GitHub study-repo metadata updates only.

## Slop/Risk Review

Historical risk found after 1.9.29 stable:

* Client/server outbox payload contract mismatch for removal operations.
* Client-side Dexie/outbox producers could emit empty removal payloads.
* Server sync validation rejected empty removal payloads.
* The visible symptom was a sync badge showing failed local operations after `/api/sync` returned per-operation rejections.

Product truth later shows 1.9.30 completed as the Delete Outbox Payload Validation Fix, and 2.0.9 retired the legacy local-outbox dashboard path.

Current study risks:

* The lab has not yet reviewed 2.0.4-2.0.9 deeply enough to explain the Replicache-only dashboard boundary.
* The lab has not yet reviewed the 3.0 collaboration arc or the 3.1 sync-latency measurement/fix path.
* The lab has not yet reviewed the 3.2 shell/design/workspace UX sequence or the 3.2.8-3.2.9 sync-resilience/idempotency fixes.
* The lab has not yet reviewed the 3.3 item detail panel / properties path, the 3.4 board/presence path, or the 3.5 ledger/time-travel/revert path.
* The lab has not yet reviewed the 3.6 stewardship/workflow realignment path or the new ChatGPT / Claude Code / Codex responsibility split.
* 3.6.4 Workspace OS Rebase RFC should not be studied as the next implementation target until the 2.0.4-3.6.3 catch-up path is understood at least at a map level.

## Senior Lessons

* Passing HTTP 200 from a batch endpoint is not enough; inspect per-operation results.
* A newly visible status surface can reveal real latent contract bugs rather than create them.
* Before architecture closeout, verify the user-visible local-first sync path under real browser IndexedDB state, not only test harness state.
* When a client/server contract mismatch appears, choose one contract owner and make the opposite side conform.
* Before collaboration work, study the authorization model as a first-class product behavior, not only as a schema/API addition.
* A sync spine transition is not complete until obsolete render/write/status paths are removed or explicitly retained with a current owner.
* Measurement spikes should produce reusable evidence paths, not only one-off observations.
* History/read-only time travel and revert/write-back are different product capabilities; do not treat the ledger as a complete undo feature until the revert path ships.
* Docs support folders are not source-of-truth owners; they should map, audit, and route back to canonical owner docs.
* Agent role realignment must be reflected in workflow docs, Codex rules, handoffs, and skills together or future prompts will drift.

## Self-Check Questions

* Where are all removal outbox operations produced, and how did 1.9.30 close the payload mismatch?
* How did 1.9.32 close the local-first dashboard architecture while leaving `seriesComplete` false for the 2.0 arc?
* How did Replicache replace the 1.9.x render path in 2.0.0?
* How did fractional indexing in 2.0.1 change list/item/view ordering?
* How did the 2.0.2 Supabase Broadcast poke trigger Replicache pull without carrying data?
* How did 2.0.3 enforce sharing permissions across read, write, invite, and revoke paths?
* Which concrete files prove 2.0.9 removed the old overlay/outbox-render/tRPC-render dashboard paths?
* How does the Yjs note path interact with list permissions?
* How does the 3.2 shell preserve dashboard state while changing navigation layout?
* Why is the 3.2.9 create-path race a transaction-abort problem rather than only a duplicate-id problem?
* How do item status, assignee, and board ordering extend list-item sync without creating a second write path?
* Why is live presence intentionally not a Replicache entity?
* What ledger entries does 3.5.0 intentionally not record?
* What is the boundary between 3.5.1 read-only history and 3.5.2 revert?
* How does `docs/tidy/*` support source-of-truth ownership without becoming source of truth?
* What automated validation evidence belongs to Codex after 3.6.3, and what remains user/controller-owned?

## Session Links

* Session summary: `sessions/2026/06/2026-06-28-3.6.3-workflow-realignment-sync-closeout.md`
* Current handoff: `handoffs/latest.md`
