# Latest Study Handoff

## Status

Study session closed after 1.9.29 merge/promotion support and post-closeout sync-badge diagnosis.

This is a study-repo-only handoff. No product code was changed by the assistant.

## Product repo

`princeoncada/tidy`

## Product state read during session

* Version: 1.9.29
* State: stable
* Phase: 1.9.29
* Phase title: Direct-Write Retirement & Default Dexie-First
* Next phase in product source of truth: 1.9.30 - Local-First Dashboard Architecture Closeout
* Last updated: 2026-06-13

## Completed 1.9.29 branch-review context

Prince manually resolved and validated the 1.9.29 branch. Final local proof reported before sync:

* `git status --short` clean
* `./scripts/validate.ps1` passed: 16/16
* `npm run test:ci` passed: typecheck, lint, 402 unit tests, 5 unauthenticated e2e
* `npm run test:e2e:auth` passed: 31 passed, 1 skipped

Important fixes made during review:

* `components/list/ListsContainer.tsx` removed render-time ref access in the authoritative query snapshot helper.
* `components/list/ListItemComponent.tsx` stopped keeping removed items mounted as matching `data-testid=list-item` rows.
* `components/list/ListsContainer.tsx` preserved the final coalesced item movement when multiple drops happen before the debounced item-order write flushes.
* `tests/e2e/utils/seed.ts` ignored transient Supabase auth `_getUser` fetch noise in e2e console collection.

## New issue discovered after 1.9.29 stable

Prince noticed the sync status badge reporting local operations needing attention. IndexedDB inspection showed mostly removal operations in `outboxOperations`. A `/api/sync` request returned HTTP 200 but per-operation results rejected those removal operations with:

`Delete operations must include a non-empty payload for server validation.`

After the sync attempt, local outbox rows were marked failed with the same error message.

Diagnosis:

* The sync badge is doing its job; it reads pending/syncing/failed local outbox rows.
* Client Dexie/outbox removal producers are emitting operations with empty payloads.
* Server sync validation rejects removal operations whose payload is an empty object.
* Therefore, this is a client/server removal-operation payload contract mismatch and a product behavior bug.

## Direction chosen by Prince

Prince prefers Option A:

* Keep server validation strict.
* Do not relax the sync endpoint contract to allow empty removal payloads.
* Update every Dexie/outbox removal producer to emit a non-empty payload.
* Canonical payload direction: `{ deleted: true }`.

## Recommended next action

Do not close the 1.9.x architecture series yet. The next continuation should resolve the outbox removal payload bug before architecture closeout.

Recommended target:

`1.9.30-option-a-outbox-removal-payload-validation-fix`

Depending on product versioning rules, either convert 1.9.30 into the payload fix and push architecture closeout after it, or create an explicit patch phase and keep architecture closeout as the following versioned decision.

## Expected implementation scope for Claude Code

Search for all outbox producers that create removal operations with empty payloads. Update those operations to use the canonical non-empty payload shape:

`payload: { deleted: true }`

Likely files to inspect:

* `lib/local-db/local-write.ts`
* `components/list/ListsContainer.tsx`
* `components/list/ListComponent.tsx`
* `components/list/ListItemComponent.tsx`
* `components/views/ViewsSidebarPreview.tsx`
* `lib/sync/sync-endpoint-contract.ts`
* `lib/sync/sync-batch-contract.ts`
* `lib/local-db/outbox-repository.ts`
* `tests/unit/local-write.test.ts`
* `tests/unit/sync-endpoint-contract.test.ts`
* `tests/unit/sync-batch-contract.test.ts`
* `tests/unit/local-overlay.test.ts`
* authenticated e2e specs touching removal flows

Validation target:

* `npm test -- local-write.test.ts sync-endpoint-contract.test.ts sync-batch-contract.test.ts local-overlay.test.ts`
* `./scripts/validate.ps1`
* `npm run test:ci`
* `npm run test:e2e:auth`

Manual proof target:

1. Reset disposable local dev/test outbox rows only if safe.
2. Reload dashboard.
3. Perform a test removal operation.
4. Confirm `/api/sync` is called.
5. Confirm the operation returns `applied` or `already-applied`.
6. Confirm the sync badge no longer reports failed local removal operations.
7. Inspect IndexedDB and confirm no failed row with the empty-payload validation error.

## Current synced study state

* `PRODUCT_SYNC_STATE.json` synced to product `1.9.29`
* `STUDY_STATE.json` last product read synced to product `1.9.29`
* Recommended next target is now the outbox removal payload validation fix, not pure architecture closeout.

## Carry forward

* `princeoncada/tidy` owns product truth.
* `princeoncada/tidy-engineering-lab` owns learning/sync truth.
* Read product source-of-truth fresh before making product claims.
* Do not write to `princeoncada/tidy` in normal study/review mode.
* Do not enter implementation unless Prince explicitly says `implementation mode`.
