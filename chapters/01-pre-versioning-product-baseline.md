# Pre-Versioning Product Baseline

## Status

Checkpointed after 2026-06-13 repo-review/support session and updated after 2026-06-14 product-sync catch-up.

This chapter has not been completed as a full baseline study. It carries practical product-review checkpoints so the next session does not lose context.

## Current Product Sync Overlay

Latest product source-of-truth read during sync:

* Version: 2.0.3
* State: stable
* Phase: 2.0.3
* Phase title: Sharing & Permissions
* Next phase: 2.0.4 - Yjs Collaborative Item Notes
* Last updated: 2026-06-14

The 1.9.30 delete-payload fix, 1.9.31 auth-suite sync-timing hardening, 1.9.32 local-first dashboard architecture closeout, 1.10.0 copy/metadata hygiene, 1.10.1 landing branding polish, and 2.0.0-2.0.3 Replicache/sharing phases are now completed in product truth and pending lab study review.

## Purpose

Understand the actual app architecture before versioned workflow history and maintain enough product-direction context to support branch reviews safely.

## Related Product Versions

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
* Next product source-of-truth phase: 2.0.4 - Yjs Collaborative Item Notes

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

## Files Read During 2.0.3 Sync

Product repo:

* `STATE.json`
* `codebase-graph.json`
* `docs/AI_HANDOFF.md`
* `docs/FUTURE_PLANS.md`
* `docs/VERSIONING.md`
* `prisma/schema.prisma`
* `lib/sync/permissions.ts`
* `trpc/routers/shareRouter.ts`

Study repo:

* `STUDY_STATE.json`
* `PRODUCT_SYNC_STATE.json`
* `STUDY_INDEX.md`
* `PRODUCT_VERSION_MATRIX.md`
* `handoffs/latest.md`

## Mental Model

Tidy 1.9.x delivered the local-first write path: Dexie-first dashboard writes by default with bounded batch sync to the server. The sync status badge is a real outbox surface: it reports pending, syncing, and failed local outbox work rather than acting as decoration.

The 2.0.x arc changes the read/render model: the dashboard now renders from the Replicache local store by default, while the legacy tRPC/overlay path remains only as gate-off compatibility until 2.0.5.

2.0.3 adds sharing and permissions on top of that Replicache architecture. The study repo should review how ownership, list/workspace sharing, invite links, effective roles, and shared-list pull behavior interact before moving into 2.0.4 Yjs notes.

## Runtime Flows Observed From 1.9.29 Session

1. Dashboard mounts under `TRPCReactProvider`.
2. `OfflineReplayTrigger` mounts globally and should initialize replay after Supabase user resolution.
3. Local Dexie/outbox operations are read by the sync status surface.
4. `/api/sync` validates each operation and returns per-operation statuses even when the HTTP response is 200.
5. Empty-payload removal operations are rejected by validation and remain visible as failed local outbox rows.

## Latest 2.0.3 Study Questions

* What does `getEffectiveListRole` allow for owner, direct share, workspace owner, and workspace member cases?
* Where does the UI expose owner controls versus recipient read/edit behavior?
* How does Replicache pull include shared lists without leaking owner tags/custom views?
* How are push permissions enforced for VIEWER versus EDITOR/OWNER?
* Which tests prove unauthorized pull/push/share actions are rejected?

## Tests / Validation Evidence From 1.9.29 Session

Reported by Prince before 1.9.29 merge/promotion:

* `git status --short` clean
* `./scripts/validate.ps1` passed: 16/16
* `npm run test:ci` passed: typecheck, lint, 402 unit tests, 5 unauthenticated e2e
* `npm run test:e2e:auth` passed: 31 passed, 1 skipped

## Slop/Risk Review

Risk found after 1.9.29 stable:

* Client/server outbox payload contract mismatch for removal operations.
* Client-side Dexie/outbox producers could emit empty removal payloads.
* Server sync validation rejected empty removal payloads.
* The visible symptom was a sync badge showing failed local operations after `/api/sync` returned per-operation rejections.

Product truth now shows 1.9.30 completed as the Delete Outbox Payload Validation Fix. The old 1.9.30 recommendation is historical, not current.

Current study risk:

* The lab has not yet reviewed 2.0.3 Sharing & Permissions deeply enough to explain the full permission boundary.
* 2.0.4 Yjs notes should not be studied as the next implementation target until the 2.0.3 permission model is understood.

## Senior Lessons

* Passing HTTP 200 from a batch endpoint is not enough; inspect per-operation results.
* A newly visible status surface can reveal real latent contract bugs rather than create them.
* Before architecture closeout, verify the user-visible local-first sync path under real browser IndexedDB state, not only test harness state.
* When a client/server contract mismatch appears, choose one contract owner and make the opposite side conform.
* Before collaboration work, study the authorization model as a first-class product behavior, not only as a schema/API addition.

## Self-Check Questions

* Where are all removal outbox operations produced, and how did 1.9.30 close the payload mismatch?
* How did 1.9.32 close the local-first dashboard architecture while leaving `seriesComplete` false for the 2.0 arc?
* How does Replicache replace the 1.9.x render path in 2.0.0?
* How does fractional indexing in 2.0.1 change list/item/view ordering?
* How does the 2.0.2 Supabase Broadcast poke trigger Replicache pull without carrying data?
* How does 2.0.3 enforce sharing permissions across read, write, invite, and revoke paths?

## Session Links

* Session summary: `sessions/2026/06/2026-06-13-1.9.29-branch-review-sync-badge-diagnosis.md`
* Current handoff: `handoffs/latest.md`
