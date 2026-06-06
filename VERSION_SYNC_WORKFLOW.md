# Version Sync Workflow

## Purpose

This workflow keeps the lab aligned with new versions of the product repo without duplicating product truth.

`princeoncada/tidy` owns product truth. This lab owns learning truth.

## Trigger

Run when Prince says `/sync-product-version` or `/sync-product-version [version]`.

## Product Read Set

Read from `princeoncada/tidy`:

* `STATE.json`
* `docs/VERSIONING.md`
* `docs/AI_HANDOFF.md`
* `docs/FUTURE_PLANS.md`
* `docs/CONTEXT_INDEX.md`
* relevant source files only if the version impact requires it

## Lab Read Set

Read from this repo:

* `PRODUCT_SYNC_STATE.json`
* `PRODUCT_VERSION_MATRIX.md`
* `STUDY_STATE.json`
* `handoffs/latest.md`
* `ledgers/rebaseline-needed.md`

## Sync Steps

1. Read product repo source documents.
2. Compare product state against `PRODUCT_SYNC_STATE.json`.
3. Detect new or unsynced product versions.
4. Create or update snapshots and case studies only when supported by source reads.
5. Update product version matrix.
6. Decide affected chapters and rebaseline needs.
7. Update ledgers and handoff.
8. Report exact changes.

## Drift Rules

* Do not duplicate product source documents.
* Do not claim a version is deeply studied unless a study chapter or case study was completed.
* Do not overwrite old learning silently.
* If a new product version changes an old mental model, add a rebaseline note instead of erasing history.
* Always read fresh product source documents before syncing.

## Commands

* `/sync-product-version`
* `/sync-product-version [version]`
* `/create-version-case-study [version]`
* `/check-lab-drift`
* `/rebaseline-chapter [chapter]`
