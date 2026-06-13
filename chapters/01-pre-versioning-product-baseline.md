# Pre-Versioning Product Baseline

## Status

Checkpointed after 2026-06-13 repo-review/support session.

This chapter has not been completed as a full baseline study. It now carries the latest practical product-review checkpoint so the next session does not lose context.

## Purpose

Understand the actual app architecture before versioned workflow history and maintain enough product-direction context to support branch reviews safely.

## Related Product Versions

* 1.9.29 - Direct-Write Retirement & Default Dexie-First - stable 2026-06-13
* Next product source-of-truth phase at close: 1.9.30 - Local-First Dashboard Architecture Closeout
* Study recommendation after close: resolve the outbox removal payload validation bug before pure architecture closeout.

## Files Read / Used During Session

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

## Mental Model

Tidy 1.9.x is in a local-first dashboard series. By 1.9.29, dashboard writes are intended to be Dexie-first by default with bounded batch sync to the server. The sync status badge is a real outbox surface: it reports pending, syncing, and failed local outbox work rather than acting as decoration.

A key product invariant from the session: when the badge reports failed operations, the local outbox and `/api/sync` response must be inspected before assuming the UI is wrong.

## Runtime Flows Observed

1. Dashboard mounts under `TRPCReactProvider`.
2. `OfflineReplayTrigger` mounts globally and should initialize replay after Supabase user resolution.
3. Local Dexie/outbox operations are read by the sync status surface.
4. `/api/sync` validates each operation and returns per-operation statuses even when the HTTP response is 200.
5. Empty-payload removal operations are rejected by validation and remain visible as failed local outbox rows.

## Tests / Validation Evidence

Reported by Prince before 1.9.29 merge/promotion:

* `git status --short` clean
* `./scripts/validate.ps1` passed: 16/16
* `npm run test:ci` passed: typecheck, lint, 402 unit tests, 5 unauthenticated e2e
* `npm run test:e2e:auth` passed: 31 passed, 1 skipped

## Slop/Risk Review

New risk found after 1.9.29 stable:

* Client/server outbox payload contract mismatch for removal operations.
* Client-side Dexie/outbox producers can emit empty removal payloads.
* Server sync validation rejects empty removal payloads.
* The visible symptom is a sync badge showing failed local operations after `/api/sync` returns per-operation rejections.

Prince prefers Option A for the next fix:

* keep server validation strict,
* do not relax empty-payload validation,
* update every removal outbox producer to emit a non-empty payload, using `{ deleted: true }` as the canonical shape.

## Senior Lessons

* Passing HTTP 200 from a batch endpoint is not enough; inspect per-operation results.
* A newly visible status surface can reveal real latent contract bugs rather than create them.
* Before architecture closeout, verify the user-visible local-first sync path under real browser IndexedDB state, not only test harness state.
* When a client/server contract mismatch appears, choose one contract owner and make the opposite side conform. Prince chose client conformance for this issue.

## Self-Check Questions

* Where are all removal outbox operations produced?
* Do every removal producer and every test fixture use the same non-empty payload shape?
* Should legacy failed empty-payload rows be migrated/reset, or only manually cleared in dev?
* Should 1.9.30 remain architecture closeout, or should a fix phase be inserted first?
* Does manual browser proof show a removal operation returning `applied` or `already-applied` from `/api/sync`?

## Session Links

* Session summary: `sessions/2026/06/session-summary.md`
* Current handoff: `handoffs/latest.md`
