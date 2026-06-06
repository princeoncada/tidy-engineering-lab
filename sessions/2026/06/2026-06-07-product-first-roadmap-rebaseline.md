# Session Summary: Product-First Roadmap Rebaseline

## Session ID

`2026-06-07-product-first-roadmap-rebaseline`

## Date

2026-06-07

## Session Type

Product direction / workflow correction / roadmap rebaseline planning.

This was not a normal code-study session. It was still valid lab work because it produced durable product-direction and workflow decisions that should guide the next product phase.

## Product Repo State Read

Product repo: `princeoncada/tidy`

Latest pushed product state read during this session:

* Version: 1.9.10
* State: stable
* Phase: 1.9.10
* Phase title: Local DB Source-of-Truth Decision
* Product `STATE.json` next phase before this discussion: 1.10.0 - Deploy Env Documentation
* Last updated: 2026-06-06

## Why This Session Happened

Prince flagged that the recent 1.9.x work exposed a workflow problem: phases were allowed to ship infrastructure, gated behavior, and decision-only work while still feeling like product progress.

The specific concern was Dexie/local DB. Dexie was originally considered to support a fast local-first dashboard experience, smoother CRUD, fewer flicker/rollback glitches, and offline-capable interactions. However, 1.9.10 recorded that the server/TanStack path remains the dashboard read authority and Dexie/outbox remains a write-side buffer only. That made the delivered work feel misaligned with the original product goal.

## Core Diagnosis

The workflow allowed technical readiness to look like shipped product progress.

1. 1.9.2 to 1.9.4 were valid mutation-cache/helper extraction phases.
2. 1.9.5 to 1.9.10 shifted into Dexie/offline infrastructure and decisions.
3. The final 1.9.10 decision preserved server/TanStack as the dashboard read authority and did not make Dexie the local runtime source for user-visible dashboard CRUD.
4. This created a mismatch between the intended product outcome and the actual shipped runtime behavior.

The issue is not that infrastructure exists. The issue is that the roadmap and closeout format did not force clear distinctions between product behavior, infrastructure, decisions, refactors, and deferred integration.

## Locked Product Direction

Tidy's near-term identity is:

> A fast personal todo app with local-first UX, built as a portfolio-grade engineering showcase.

This means product direction should prioritize:

1. Fast and smooth personal task management.
2. Local-first behavior where it improves UX.
3. Portfolio-grade engineering proof.
4. Thin vertical product slices instead of long horizontal infrastructure chains.

## Locked Dexie Direction

Dexie continues, but only as product-integrated local-first dashboard behavior, not hidden infrastructure.

Near-term target:

* Dexie becomes the local runtime source for dashboard CRUD slices.
* Start with a working implementation, not a full-app migration.
* Expand to a full local-first database only if the dashboard implementation proves it is the correct long-term solution.

Final phrasing:

> Dexie should move forward as local runtime source for dashboard CRUD first, then full local-first database ownership later only if proven correct.

## Locked TanStack Direction

TanStack Query should not be deleted immediately.

It stays as a server sync/hydration bridge during migration, but it should not permanently block Dexie from becoming the local runtime source for dashboard behavior.

Target direction:

* Dexie/local state drives immediate dashboard rendering for local-first slices.
* TanStack/tRPC remains useful for initial server hydration, background sync, invalidation, remote persistence, and non-local-first data.
* PostgreSQL/Supabase remains the remote durable source of truth.
* Outbox stores pending local writes for replay.

## Redis Decision

Redis is deferred.

Redis may be useful later for server-side caching, queues, rate limiting, sync coordination, or scaling. It is not a replacement for Dexie for browser-side offline/local-first UX.

Do not introduce Redis until Dexie is product-integrated and the app has a real server-side performance or scaling need.

## Locked Feature Flag Direction

Dexie/local-first work should be dev-gated first, then activated only after product proof.

Feature flags must include:

* Flag name.
* Default value.
* Dev test path.
* Activation condition.
* Removal or default-on plan.

No feature flag should become a hiding place for unfinished work.

## Locked Validation Direction

Targeted validation during alpha.

Full validation only before stable promotion.

During alpha:

* Run focused tests for the changed behavior.
* Run typecheck/lint when the touched surface makes them relevant.
* Include a manual product proof for the workflow being built.

Before stable:

* Full test suite.
* Typecheck.
* Lint.
* Validation script.
* Manual product proof summary.

## Locked Roadmap Format

Keep the roadmap linear.

Do not split into multiple lanes yet. Instead, every planned phase must clearly state:

* Type.
* Implementation goal.
* Product/user impact.
* Runtime integration target.
* Deferral boundaries.
* Validation target.

Y-level phases do not need to be strictly product behavior every time, but each phase must declare its implementation intent and product relationship clearly enough to avoid hidden drift.

Core rule:

> Phases do not need to be strictly user-visible, but every phase must declare its implementation intent, product relationship, runtime integration target, and deferral boundary. No phase may silently defer expected product integration without naming the follow-up phase or decision.

## Final Next Phase Name

Locked next recommended phase:

`1.10.0 - Product-First Planning Contract and Roadmap Rebaseline`

This should replace or supersede the current product roadmap's next planned item, `1.10.0 - Deploy Env Documentation`, unless Prince explicitly chooses otherwise later.

## Recommended Scope For 1.10.0

1. Add the product-first planning contract to the appropriate workflow docs.
2. Rebaseline `docs/FUTURE_PLANS.md` under the new phase format.
3. Preserve a linear roadmap.
4. Rewrite the next Dexie work as product-integrated local-first dashboard slices.
5. Add feature-flag activation/removal requirements.
6. Document targeted-alpha/full-stable validation policy.
7. Make the next implementation phase after 1.10.0 a Dexie product slice, not deploy docs.

## Proposed Follow-Up Roadmap Direction

Recommended sequence:

1. `1.10.0 - Product-First Planning Contract and Roadmap Rebaseline`
2. `1.10.1 - Dev-Gated Local-First Create List Slice`
3. `1.10.2 - Stabilize and Enable Local-First Create List Slice`
4. `1.10.3 - Local-First List Rename Slice`
5. `1.10.4 - Local-First Item Create and Complete Slice`
6. `1.10.5 - Local-First Delete and Recovery Slice`
7. `1.10.6 - Local-First Dashboard CRUD Rebaseline Decision`

## Main Slop Finding

The workflow currently has no strong enough gate preventing infrastructure, gated behavior, and decision-only work from being mistaken for delivered product behavior.

This should be recorded as a high-severity workflow/product-planning drift finding.

## Carry Forward

Next session should not continue normal study by default.

Recommended next action:

`/study-target 1.10.0-product-first-planning-contract-roadmap-rebaseline`

or open implementation planning for:

`1.10.0 - Product-First Planning Contract and Roadmap Rebaseline`

Do not write product code unless Prince explicitly enters implementation mode.