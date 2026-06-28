# Study Session Index

Tracks completed and restudy-ready Tidy Engineering Lab study sessions.

Use this file to list prior sessions, choose a session to review, or set a past session as a restudy target.

## Session Table

| Session ID | Date | Title | Chapter / Target | Product Version | Status | Summary File | Restudy Command |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 2026-06-28-3.6.3-workflow-realignment-sync-closeout | 2026-06-28 | 3.6.3 Workflow Realignment Sync Closeout | `01-pre-versioning-product-baseline` / product-sync closeout | 3.6.3 | Completed | `sessions/2026/06/2026-06-28-3.6.3-workflow-realignment-sync-closeout.md` | `/restudy-session 2026-06-28-3.6.3-workflow-realignment-sync-closeout` |
| 2026-06-13-1.9.29-branch-review-sync-badge-diagnosis | 2026-06-13 | 1.9.29 Branch Review and Sync Badge Diagnosis | `01-pre-versioning-product-baseline` / `1.9.29-direct-write-retirement` | 1.9.29 | Needs refresh | `sessions/2026/06/2026-06-13-1.9.29-branch-review-sync-badge-diagnosis.md` | `/restudy-session 2026-06-13-1.9.29-branch-review-sync-badge-diagnosis` |
| 2026-06-07-product-first-roadmap-rebaseline | 2026-06-07 | Product-First Roadmap Rebaseline | `1.10.0-product-first-planning-contract-roadmap-rebaseline` | 1.9.10 | Restudy-ready | `sessions/2026/06/2026-06-07-product-first-roadmap-rebaseline.md` | `/restudy-session 2026-06-07-product-first-roadmap-rebaseline` |
| 2026-06-06-navigation-bootcamp | 2026-06-06 | Navigation Bootcamp | `00-navigation-bootcamp` | 1.9.5 | Restudy-ready | `sessions/2026/06/2026-06-06-navigation-bootcamp.md` | `/restudy-session 2026-06-06-navigation-bootcamp` |

## Status Values

| Status | Meaning |
| --- | --- |
| Completed | Session was closed and persisted. |
| Restudy-ready | Session can be used as a future study target. |
| Needs refresh | Session content may be stale against current product truth. |
| Superseded | Session was replaced by a newer study or rebaseline. |

## Restudy Rules

When Prince runs `/restudy-session [session-id]`:

1. Read `SESSION_INDEX.md`.
2. Find the session row by Session ID.
3. Read the linked session summary file.
4. Read current product source-of-truth files fresh.
5. Report what still holds, what is stale, and what changed.
6. Set the current target to restudy that session.

When Prince runs `/session [session-id]`:

1. Read `SESSION_INDEX.md`.
2. Read the linked session summary file.
3. Summarize what was learned, what files were touched/read, what open questions remain, and what follow-up target fits.

When Prince runs `/sessions`:

1. Read `SESSION_INDEX.md`.
2. Show a compact list of available sessions.
3. Recommend the best session to continue or restudy based on current lab state.

## Close Study Index Contract

Every `/close-study` should update this file by adding or updating one row for the closed session.

The row should include:

- stable session ID
- date
- title
- chapter or study target
- product version studied
- status
- summary file path
- restudy command
