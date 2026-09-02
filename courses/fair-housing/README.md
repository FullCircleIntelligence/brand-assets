# Fair Housing Training Program — Design Package (Vermont)

**Prepared for:** Full Circle Property Management
**Jurisdiction:** State of Vermont, United States (plus federal law and municipal overlays)
**Last researched:** September 2026
**Status:** Design specification — not legal advice. Have Vermont counsel or the
CVOEO Fair Housing Project review the finished curriculum before rollout.

---

## What is in this package

| File | Purpose |
|---|---|
| `01-recommendation.md` | The one-course vs. two-course question, answered, with rationale and a rollout cadence |
| `02-course-a-fair-housing-foundations.md` | Full topic outline for Course A (all staff) |
| `03-course-b-reasonable-accommodations.md` | Full topic outline for Course B (disability / RA / RM) |
| `04-role-matrix.md` | Who takes what, and role-specific scenario banks for all five worker contexts |
| `05-legal-frameworks.md` | Every statute, regulation, and guidance document the course must be built on, with citations and current status |
| `06-glossary.md` | ~110 terms learners and the verification agent both need |
| `07-verification-agent-prompt.md` | The ready-to-use prompt for your AI agent to audit the built course against this spec |

## The short answer on structure

**Build two courses, not one — but make them a single required sequence for
anyone who touches a resident, an owner, or a request.**

- **Course A — Fair Housing Foundations** (~90 min, all staff, annual)
- **Course B — Disability, Reasonable Accommodations & Modifications** (~120 min,
  everyone except a narrow accounting-only carve-out, annual)

Course A carries a short mandatory *"Recognize and Route"* disability module so
that nobody — including accounting and maintenance — can complete only Course A
and still believe they are allowed to answer an accommodation request. Full
reasoning in `01-recommendation.md`.

## The single most important Vermont-specific point

Vermont law is materially broader than federal law, and the gap widened in 2025
while federal enforcement narrowed. As of July 1, 2025 Vermont protects
**citizenship and immigration status** (Act 69), on top of six categories the
federal Fair Housing Act does not cover. Meanwhile, in September 2025 HUD
withdrew eight fair housing guidance documents — including both assistance-animal
notices — and in January 2026 proposed rescinding its disparate impact rule.

**Training consequence:** the course must be taught from the *Vermont* baseline,
not the federal one. A course built from a national LMS template will be
under-inclusive and, on assistance animals and immigration status, actively
wrong for Vermont. This is the single highest-value thing your verification
agent should check.

## How to use this with your AI agent

1. Build (or buy) the course.
2. Feed the agent `07-verification-agent-prompt.md` as its system prompt, with
   `02`, `03`, `04`, `05`, and `06` attached as the reference corpus.
3. Feed it the course material (outline, slides, script, assessment bank).
4. It returns a gap report with severities, plus a per-role coverage matrix.

## Currency warning

Fair housing law is unusually unsettled right now. Three items should be
re-verified before every annual re-issue of the course — they are listed with
citations under "Watch List" in `05-legal-frameworks.md`.
