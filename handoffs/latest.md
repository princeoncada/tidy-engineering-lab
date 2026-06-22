# Latest Study Handoff

## Status

Study repo synced to the latest pushed product source-of-truth state on 2026-06-22.

This is a study-repo-only sync handoff. No product code was changed by the assistant.

## Product repo

`princeoncada/tidy`

## Product state read during sync

* Version: 3.2.9
* State: stable
* Phase: 3.2.9
* Phase title: Create-Path Idempotency Hardening (TOCTOU)
* Next phase in product source of truth: 3.3.0 - Item Detail Panel & Notes
* Last updated: 2026-06-22

## Latest implementation checked

Product source-of-truth now records 3.2.9 as stable. The roadmap shows the first Planned item as 3.3.0 - Item Detail Panel & Notes.

Important implementation surfaces visible in the latest product handoff/source:

* The dashboard is now Replicache-only for render/write behavior; legacy dashboard tRPC render, pending outbox overlay, local outbox write-capture/replay worker, `/api/sync`, and local-outbox sync badge paths were retired in the 2.0.9 arc.
* Current user actions include list/item/tag/view CRUD, item note editing, sharing/workspace management, and theme switching.
* Current key surfaces include `components/ReplicacheProvider.tsx`, `hooks/useReplicacheDashboard.ts`, `hooks/useDashboardMutations.ts`, `lib/sync/replicache/*`, `lib/sync/server-apply.ts`, `lib/dashboard/server-read.ts`, `lib/collab/*`, `components/list/ItemNotesEditor.tsx`, `components/sharing/*`, and `lib/sync/permissions.ts`.
* Collaboration arc invariants now matter for study: one Replicache sync spine for web and future mobile, presence separate from Replicache, workspace model kept, and UI/design governed by `docs/design.md`.
* Current known risk/focus area: 3.2.9 hardens create-path idempotency in `lib/sync/server-apply.ts` with transaction/savepoint recovery for unique-constraint races across list, listItem, tag, and view creates.

## Study repo sync changes

* `PRODUCT_SYNC_STATE.json` now points to product 3.2.9 stable.
* `STUDY_STATE.json` now records the latest product read as 3.2.9 stable.
* `STUDY_INDEX.md` now marks the lab as synced through 3.2.9 and adds planned study tracks for the 2.0, 2.1-2.2, and 3.0-3.2 catch-up arcs.
* `PRODUCT_VERSION_MATRIX.md` now tracks product releases through 3.2.9.
* `chapters/01-pre-versioning-product-baseline.md` now carries a 3.2.9 sync overlay and updated study questions.

## Recommended next study action

Recommended study target:

`2.0.4-2.0.9-replicache-hardening-legacy-retirement-review`

Reason: the lab had only synced to 2.0.3 before this handoff. Before studying 3.3.0 Item Detail Panel & Notes, the lab should understand the 2.0.4-2.0.9 transition from early Replicache/sharing into a fully Replicache-only dashboard with Yjs notes, realtime poke authorization, dead config removal, and legacy path retirement.

## Carry forward

* `princeoncada/tidy` owns product truth.
* `princeoncada/tidy-engineering-lab` owns learning/sync truth.
* Read product source-of-truth fresh before making product claims.
* Do not write to `princeoncada/tidy` in normal study/review mode.
* Do not enter implementation unless Prince explicitly says `implementation mode`.
