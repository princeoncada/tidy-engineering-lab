# Latest Study Handoff

## Status

Study repo synced to the latest pushed product source-of-truth state on 2026-06-26.

This is a study-repo-only sync handoff. No product code was changed by the assistant.

## Product repo

`princeoncada/tidy`

## Product state read during sync

* Version: 3.5.1
* State: stable
* Phase: 3.5.1
* Phase title: Time-Travel Read
* Next phase in product source of truth: 3.5.2 - Revert
* Last updated: 2026-06-26

## Latest implementation checked

Product source-of-truth now records 3.5.1 as stable. The roadmap shows the first Planned item as 3.5.2 - Revert.

Important implementation surfaces visible in the latest product handoff/source:

* The dashboard remains Replicache-only for render/write behavior; legacy dashboard tRPC render, pending outbox overlay, local outbox write-capture/replay worker, `/api/sync`, and local-outbox sync badge paths remain retired from the 2.0.9 arc.
* Current user actions include list/item/tag/view CRUD, item note editing, status and assignee changes, board interactions, sharing/workspace management, read-only history, and theme switching.
* Current key surfaces include `components/ReplicacheProvider.tsx`, `hooks/useReplicacheDashboard.ts`, `hooks/useDashboardMutations.ts`, `lib/sync/replicache/*`, `lib/sync/server-apply.ts`, `lib/dashboard/server-read.ts`, `lib/collab/*`, `components/item/ItemDetailPanel.tsx`, `components/item/ItemNotesField.tsx`, `components/board/*`, `lib/realtime/*`, `components/history/HistoryPanel.tsx`, `lib/history/*`, `components/sharing/*`, and `lib/sync/permissions.ts`.
* Collaboration arc invariants still matter for study: one Replicache sync spine for web and future mobile, presence separate from Replicache, workspace model kept, and UI/design governed by `docs/design.md`.
* Current known risk/focus areas include flag-gated item panel/history/presence surfaces, presence RLS/transport boundaries, board legacy-null `boardOrderKey` fallback, and the boundary between 3.5.1 read-only history and 3.5.2 revert/write-back.

## Study repo sync changes

* `PRODUCT_SYNC_STATE.json` now points to product 3.5.1 stable.
* `STUDY_STATE.json` now records the latest product read as 3.5.1 stable.
* `STUDY_INDEX.md` now marks the lab as synced through 3.5.1 and adds a planned study track for the 3.3-3.5 item panel / presence / history arc.
* `PRODUCT_VERSION_MATRIX.md` now tracks product releases through 3.5.1.
* `chapters/01-pre-versioning-product-baseline.md` now carries a 3.5.1 sync overlay and updated study questions.
* `chapters/3.3.0-3.5.1-item-panel-presence-history-series.md` was added as a placeholder study chapter for the newly synced arc.

## Recommended next study action

Recommended study target:

`2.0.4-2.0.9-replicache-hardening-legacy-retirement-review`

Reason: the lab still has not deeply reviewed the transition from early Replicache/sharing into a fully Replicache-only dashboard with Yjs notes, realtime poke authorization, dead config removal, and legacy path retirement. That boundary should be understood before studying the later item panel, board/presence, history, or revert arcs.

## Carry forward

* `princeoncada/tidy` owns product truth.
* `princeoncada/tidy-engineering-lab` owns learning/sync truth.
* Read product source-of-truth fresh before making product claims.
* Do not write to `princeoncada/tidy` in normal study/review mode.
* Do not enter implementation unless Prince explicitly says `implementation mode`.
