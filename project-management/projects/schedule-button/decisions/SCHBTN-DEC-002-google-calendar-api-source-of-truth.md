# SCHBTN-DEC-002: Google Calendar API as Source of Truth for Availability

## Metadata

- ID: `SCHBTN-DEC-002`
- Status: `Draft`
- Owner: `Engineering Lead`
- Date: `2026-06-01`
- Project Key: `SCHBTN`

## Context

Schedule button needs reliable availability data and must mark selected slots as busy after booking confirmation. A calendar provider integration is required for read/write slot state.

## Decision

Google Calendar API will be used as the calendar integration layer and source of truth for slot availability and busy-slot updates.

## Consequences

- Positive consequence 1: Direct integration with Google ecosystem used by target users.
- Positive consequence 2: Standard API support for reading free/busy data and writing booking events.
- Positive consequence 3: Reduces need for custom calendar state storage in MVP.
- Negative consequence 1: Dependency on Google API quotas and rate limits.
- Negative consequence 2: OAuth and token lifecycle management adds implementation complexity.
- Negative consequence 3: Integration behavior can be affected by Google API policy changes.

## Alternatives

- Alternative 1: Microsoft Graph Calendar API.
- Alternative 2: Custom calendar database as system of record.
- Alternative 3: Third-party scheduling SaaS API abstraction.

## Decision Checklist Review

Checklist file: `project-management/templates/decision-checklist.md`

- Review Date: `TBD`
- Reviewer: `TBD`
- Result: `Fail`
- Triage: `High`

### Checklist Summary

- [x] Decision conflict check completed
- [x] Decision triage assigned
- [x] Context is clear
- [x] Alternatives were considered
- [x] Consequences are understood
- [x] Links to impacted artifacts are recorded

### Review Notes

- Confirm minimum OAuth scopes and service-account feasibility before production design freeze.

## Links

- Related requirements: `SCHBTN-REQ-001`
- Related solutions: `TBD`
- Related implementation: `TBD`
- Related technology stack entries: `TBD`
- Related portfolio or project decision register: `project-management/projects/schedule-button/decision-register.md`
