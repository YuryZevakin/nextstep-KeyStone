# SCHBTN-DEC-001: Azure Function + API Gateway for Availability API

## Metadata

- ID: `SCHBTN-DEC-001`
- Status: `Draft`
- Owner: `Engineering Lead`
- Date: `2026-06-01`
- Project Key: `SCHBTN`

## Context

Schedule button requires a backend API that returns available time slots and marks selected slots as busy. Expected traffic is low in early stages, so fixed-cost infrastructure would be inefficient.

## Decision

The availability API will be implemented as an Azure Function behind Azure API Management (API Gateway).  
The Function will expose endpoints for:
- `GET /availability` to return available meeting slots.
- `POST /bookings` (or equivalent) to set a selected slot as busy.

## Consequences

- Positive consequence 1: Low operating cost at low load due to serverless consumption pricing.
- Positive consequence 2: API Gateway adds centralized routing, security policy, and versioning controls.
- Positive consequence 3: Architecture scales automatically as usage grows.
- Negative consequence 1: Cold starts may increase first-request latency.
- Negative consequence 2: API Management configuration adds operational complexity versus direct function exposure.
- Negative consequence 3: Lock-in risk to Azure-specific platform services.

## Alternatives

- Alternative 1: Always-on containerized API (higher fixed monthly cost at low usage).
- Alternative 2: Traditional VM-hosted API service (higher operations overhead).
- Alternative 3: Direct Google Calendar embedding without custom backend (does not satisfy custom slot state handling requirements).

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

- Validate projected monthly request volume against Azure consumption tier limits before production.

## Links

- Related requirements: `SCHBTN-REQ-001`
- Related solutions: `TBD`
- Related implementation: `TBD`
- Related technology stack entries: `TBD`
- Related portfolio or project decision register: `project-management/projects/schedule-button/decision-register.md`
