# Tidy Engineering Lab

Persistent study companion for `princeoncada/tidy`.

This repo exists to help Prince develop maintainer-level understanding of the Tidy codebase through guided reverse engineering, version-aware case studies, session handoffs, slop audits, open questions, and senior-level engineering lessons.

## Boundary

`princeoncada/tidy` owns product truth.

This repo owns learning truth.

Do not treat this repo as the source of truth for product version, roadmap, architecture invariants, validation rules, or implementation state. Always read the product repo source-of-truth docs fresh.

## Core files

* `STUDY_STATE.json` tracks study progress.
* `PRODUCT_SYNC_STATE.json` tracks the latest product state seen by the lab.
* `STUDY_INDEX.md` is the human study dashboard.
* `PRODUCT_VERSION_MATRIX.md` tracks product versions from the learning perspective.
* `CHATHEAD_OPENER.md` starts future study chatheads.
* `handoffs/latest.md` carries compact continuity between sessions.
* `LEARNING_WORKFLOW.md` defines the study workflow.
* `VERSION_SYNC_WORKFLOW.md` defines how the lab follows new product versions.

## Default mode

Reading and navigation only.

Implementation mode requires Prince to explicitly say:

`implementation mode`

## First study target

`00-navigation-bootcamp`

Start with:

`/start-study 00-navigation-bootcamp`
