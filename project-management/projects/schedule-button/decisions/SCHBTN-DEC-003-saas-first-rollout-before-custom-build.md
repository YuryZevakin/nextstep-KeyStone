# SCHBTN-DEC-003: SaaS-First Rollout Before Custom Build

## Metadata

- ID: `SCHBTN-DEC-003`
- Status: `Accepted`
- Owner: `Product Owner`
- Date: `2026-06-01`
- Project Key: `SCHBTN`

## Context

Current priority is fast validation of demand and booking conversion with minimal implementation risk.

## Weighted Decision Matrix

Decision goal: choose between building SCHBTN now or using SaaS first.

Scoring model:
- Score each criterion from `1` (poor) to `5` (excellent).
- Weighted score = `score x weight`.
- Total score = sum of weighted scores.

| Criterion | Weight | Build (score) | Build (weighted) | SaaS (score) | SaaS (weighted) |
|---|---:|---:|---:|---:|---:|
| Time to launch | 20 | 2 | 40 | 5 | 100 |
| Initial cost (first 3 months) | 15 | 3 | 45 | 4 | 60 |
| Cost at scale (12+ months) | 15 | 4 | 60 | 2 | 30 |
| Localization for Russia market | 15 | 5 | 75 | 2 | 30 |
| Custom booking logic flexibility | 10 | 5 | 50 | 2 | 20 |
| Data ownership and analytics control | 10 | 5 | 50 | 2 | 20 |
| Compliance and sanctions resilience | 10 | 4 | 40 | 2 | 20 |
| Operations/maintenance simplicity | 5 | 2 | 10 | 5 | 25 |
| **Total** | **100** |  | **370** |  | **305** |

Interpretation rules:
- If difference is `< 30` points: choose `SaaS-first`, reassess after 60-90 days.
- If Build leads by `>= 30` points: start custom implementation now.
- If SaaS leads by `>= 30` points: use SaaS now, defer custom build.

## Decision

Use SaaS scheduling solution for initial rollout.  
Do not start custom backend/frontend implementation now.  
Run a pilot and reassess using the same weighted model after collecting real usage data.

## Consequences

- Positive consequence 1: Fastest time to market with low delivery risk.
- Positive consequence 2: Lower short-term engineering effort and maintenance overhead.
- Positive consequence 3: Real user data will improve accuracy of future build/buy decision.
- Negative consequence 1: Less control over UX, data model, and custom booking logic.
- Negative consequence 2: Potential constraints from vendor pricing, policy, and integrations.

## Alternatives

- Alternative 1: Build custom SCHBTN immediately.
- Alternative 2: Hybrid model (SaaS UI + partial custom middleware) from day one.

## Decision Checklist Review

Checklist file: `project-management/templates/decision-checklist.md`

- Review Date: `2026-06-01`
- Reviewer: `Project Team`
- Result: `Pass`
- Triage: `High`

### Checklist Summary

- [x] Decision conflict check completed
- [x] Decision triage assigned
- [x] Context is clear
- [x] Alternatives were considered
- [x] Consequences are understood
- [x] Links to impacted artifacts are recorded

### Review Notes

- Re-evaluation checkpoint required after pilot completion (2-4 weeks).

## Links

- Related requirements: `SCHBTN-REQ-001`
- Related solutions: `TBD`
- Related implementation: `TBD`
- Related technology stack entries: `TBD`
- Related portfolio or project decision register: `project-management/projects/schedule-button/decision-register.md`
