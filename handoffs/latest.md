# Latest Study Handoff

## Status

Product repo sync refreshed after 1.9.29 was merged and promoted on `master`.

This is a study-repo-only sync. No product code was changed.

## Product repo

`princeoncada/tidy`

## Product state read during sync

* Version: 1.9.29
* State: stable
* Phase: 1.9.29
* Phase title: Direct-Write Retirement & Default Dexie-First
* Next phase: 1.9.30 - Local-First Dashboard Architecture Closeout
* Last updated: 2026-06-13

## Completed 1.9.29 branch-review context

Prince manually resolved and validated the 1.9.29 branch. Final local proof reported before sync:

* `git status --short` clean
* `./scripts/validate.ps1` passed: 16/16
* `npm run test:ci` passed: typecheck, lint, 402 unit tests, 5 unauthenticated e2e
* `npm run test:e2e:auth` passed: 31 passed, 1 skipped

Important fixes made during review:

* `components/list/ListsContainer.tsx` removed render-time ref access in the authoritative query snapshot helper.
* `components/list/ListItemComponent.tsx` stopped keeping deleted items mounted as matching `data-testid=list-item` rows.
* `components/list/ListsContainer.tsx` preserved the final coalesced item movement when multiple drops happen before the debounced item-order write flushes.
* `tests/e2e/utils/seed.ts` ignored transient Supabase auth `_getUser` fetch noise in e2e console collection.

## Current product arc

Tidy has completed the 1.9.29 Direct-Write Retirement & Default Dexie-First phase. The next planned phase is 1.9.30, a local-first dashboard architecture closeout decision. The product roadmap describes this as evaluating the shipped reconciled read graph, Dexie-first dashboard writes, and bounded server batch sync, then recording whether the 1.9.x local-first series is complete or whether another explicitly versioned product phase remains.

## Current synced study state

* `PRODUCT_SYNC_STATE.json` synced to product `1.9.29`
* `STUDY_STATE.json` last product read synced to product `1.9.29`
* Recommended study/review target: `1.9.30-local-first-dashboard-architecture-closeout`

## Carry forward

* `princeoncada/tidy` owns product truth.
* `princeoncada/tidy-engineering-lab` owns learning/sync truth.
* Do not write to `princeoncada/tidy` in normal study/review mode.
* Read product source-of-truth fresh before making product claims.
* For 1.9.30, focus on architecture decision evidence, not more product implementation unless Prince explicitly enters implementation mode.
