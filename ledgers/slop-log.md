# Slop Log

Append-only list of quality, drift, risk, or unclear-design findings discovered during study.

| ID | Date | Chapter | Finding | Severity | Evidence | Status |
| --- | --- | --- | --- | --- | --- | --- |
| SL-2026-06-06-001 | 2026-06-06 | `00-navigation-bootcamp` | Product `docs/AI_HANDOFF.md` top state is current, but lower sections still reference older 1.5.x and 1.6.x continuation guidance. | High | `docs/AI_HANDOFF.md` Latest Completed Change and Next Session sections | Open |
| SL-2026-06-06-002 | 2026-06-06 | `00-navigation-bootcamp` | Product `docs/VERSIONING.md` version history has stable rows whose Notes column still says `(in progress)`. | Medium | `docs/VERSIONING.md` Version History table | Open |
| SL-2026-06-06-003 | 2026-06-06 | `00-navigation-bootcamp` | Product role docs describe ChatGPT as architect/scoper, but Prince's current workflow uses Claude Code as architect/scoper/planner/validator/prompt builder, Codex as boosted implementer, and ChatGPT as reviewer. | High | `docs/WORKFLOW.md` role model versus Prince's current workflow | Open |
| SL-2026-06-06-004 | 2026-06-06 | `00-navigation-bootcamp` | `docs/FUTURE_PLANS.md` and `docs/VERSIONING.md` both carry historical version information, creating possible duplication. | Medium | Product docs history surfaces | Open |
| SL-2026-06-06-005 | 2026-06-06 | `00-navigation-bootcamp` | Retired/pointer workflow surfaces such as `ai-harness/skills/*` may be removable or compressible if validation does not depend on them. | Low | `ai-harness/README.md` and retired skill pointers | Open |
