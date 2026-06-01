# Schedule button

- Project Key: `SCHBTN`
- Status: `Closed`
- Owner: `TBD`

## Project Description

Special button linked to calendar availability that opens a dialog and shows available time slots for meetings or events.

## Competitors

- Calendly
- Cal.com
- Google Calendar Appointment Scheduling
- Microsoft Bookings
- CalEmbed

## Competitor Geography and Market Space

- US/Global competitors: `Calendly`, `Cal.com`, `Google Calendar Appointment Scheduling`, `Microsoft Bookings`
- Russia/CIS competitors: `YCLIENTS`, `DIKIDI`, `GBooking`, `2minutes`, `Calink`
- China: no single dominant standalone competitor identified in this project context; scheduling is often embedded into broader platform ecosystems.

Market space for SCHBTN:
- Localized scheduling product for Russia-focused operations.
- Deep integrations with local payment and communication channels.
- Vertical-specific booking flows (beauty, clinics, education, services).
- Compliance-aware architecture due to cross-border financial/sanctions constraints.

## AI-First Estimation

- MVP (embed button + dialog + availability list + mark slot busy + Google Calendar API + Azure Function/API Gateway): `5-8 working days`
- Production-ready v1 (security hardening, idempotency, retries, monitoring, analytics, tests, docs): `2-4 weeks`

Estimated effort split:
- Backend/API + Google Calendar integration: `40%`
- Frontend embed widget/dialog: `20%`
- Security/reliability/observability: `25%`
- QA + release + docs: `15%`

Core project files:

- `project-charter.md`
- `decision-register.md`
- `requirements/`
- `decisions/`
