# Study Index

## Current Position

Current chapter: `01-pre-versioning-product-baseline`
Current mode: Reading, navigation, and product-sync catch-up
Latest product sync: `3.2.9` stable, synced into the lab on 2026-06-22
Next recommended target: `2.0.4-2.0.9-replicache-hardening-legacy-retirement-review`

## Source Repos

| Repo | Role |
| --- | --- |
| `princeoncada/tidy` | Product repo, owns product truth |
| `princeoncada/tidy-engineering-lab` | Study repo, owns learning truth |

## Study Tracks

| Track | Chapter | Status | Purpose |
| --- | --- | --- | --- |
| Navigation Bootcamp | `00-navigation-bootcamp` | Completed | Learn repo navigation, source-of-truth docs, and safe reading workflow |
| Product Baseline | `01-pre-versioning-product-baseline` | Active / needs rebaseline | Understand the actual app architecture before versioned workflow history; currently carrying product sync through 3.2.9 |
| Dexie Foundation | `02-dexie-foundation` | Not started | Understand local DB foundation and non-runtime boundaries |
| Outbox Sync Queue | `03-outbox-sync-queue` | Not started | Understand outbox helpers, coalescing, replay, and deferred sync |
| View Filter Hardening | `04-view-filter-hardening` | Not started | Understand projection correctness and view/list/tag consistency |
| 1.4 Regression Series | `05-1.4-regression-series` | Not started | Understand race regressions, E2E hardening, and workflow patches |
| 1.5 Harness/Skills/Hooks | `06-1.5-harness-skills-hooks` | Not started | Understand AI harness, skills, hooks, context budget, and local memory |
| 1.6 Ownership/Security | `07-1.6-ownership-security` | Not started | Understand server-side ownership boundaries and regression tests |
| 1.7 Optimistic Queue | `08-1.7-optimistic-queue` | Not started | Understand optimistic queue race behavior and rollback rules |
| 1.8 Local DB/Offline Prototype | `09-1.8-local-db-offline-prototype` | Not started | Understand local-first scaffolding and offline prototype boundaries |
| 1.9 Dashboard Mutation Chokepoint | `10-1.9-dashboard-mutation-chokepoint` | Not started / needs rebaseline | Understand dashboard mutation cache seam, local-first write path, bounded sync, and later Replicache supersession |
| 2.0 Replicache / Sharing / Legacy Retirement | `2.0.0-2.0.9-replicache-legacy-retirement-series` | Planned / needs study | Understand Replicache render inversion, permissions, Yjs notes, realtime poke authorization, and legacy path retirement |
| 2.1-2.2 Deploy / Visual Readiness | `2.1.0-2.2.3-deploy-visual-readiness-series` | Planned / needs study | Understand deployment readiness, visual pass, render-gate cleanup, idempotency, and seriesComplete reconciliation |
| 3.0-3.2 Collaboration Shell / Sync Hardening | `3.0.0-3.2.9-collaboration-shell-sync-series` | Planned / needs study | Understand collaboration roadmap pinning, design source of truth, sync-latency work, shell/workspace UX, and Replicache resilience fixes |

## Continuity

Latest handoff:
`handoffs/latest.md`

Session index:
`SESSION_INDEX.md`

Open questions:
`ledgers/open-questions.md`

Slop log:
`ledgers/slop-log.md`

Product version matrix:
`PRODUCT_VERSION_MATRIX.md`
