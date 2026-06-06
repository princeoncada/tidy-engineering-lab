# Version Sync Prompt

Use this when the product repo advances to a new version.

Steps:

1. Read lab state files: `PRODUCT_SYNC_STATE.json`, `PRODUCT_VERSION_MATRIX.md`, `STUDY_STATE.json`, and `handoffs/latest.md`.
2. Read product source documents fresh: `STATE.json`, `docs/VERSIONING.md`, `docs/AI_HANDOFF.md`, `docs/FUTURE_PLANS.md`, and `docs/CONTEXT_INDEX.md`.
3. Compare last seen lab product version with current product version.
4. Add a version snapshot only from facts actually read.
5. Add or update a product evolution case study only when enough evidence was reviewed.
6. Update the product version matrix.
7. Add rebaseline notes when a prior chapter mental model may be outdated.
8. Update the latest handoff.
9. Report exact files changed.

Rules:

* The lab is not product truth.
* Only mark a version deeply studied after a real chapter or case study is completed.
* Keep product docs in the product repo.
