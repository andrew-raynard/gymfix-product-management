# GymFix — MVP Scope & Trade-offs

**Phase:** 4 — Feature Prioritisation  
**Status:** Proposed MVP, not yet built or validated

## Product Hypothesis

A lightweight reporting-to-resolution workflow may help smaller gym operators manage equipment faults more consistently and give members clearer status visibility.

## In Scope

1. **Equipment identification and fault reporting:** a member selects or scans an equipment identifier, describes the issue, and submits a ticket. Provide a manual fallback if QR scanning is unavailable.
2. **Ticket dashboard:** staff view and filter submitted tickets, including equipment, creation date, and status.
3. **Ticket assignment:** staff assign a responsible person and record assignment time.
4. **Status tracking:** Reported, Assigned, In Progress, Awaiting Parts, Resolved. Members can see appropriate non-sensitive status information.
5. **Lightweight blocker tracking:** staff can optionally specify a blocker category such as parts, technician availability, or approval.

## Out of Scope

- AI diagnosis and predictive maintenance
- Multi-branch administration
- Automatic email/SMS/push notifications
- Advanced business analytics and forecasting
- Full inventory and procurement management
- Subscription billing
- Photo upload (reconsider after testing)

## Core User Flow

Member identifies equipment → submits report → ticket is recorded → staff reviews and assigns → staff or technician updates status/blocker → staff confirms resolution → member can see resolved status.

## Dependencies and Non-functional Requirements

- Each ticket has a unique ID, equipment identifier, created timestamp, and current status.
- Only authorised staff can assign tickets or mark repairs resolved.
- Members must not see internal notes or personal technician information.
- Duplicate reports should be detectable or flagged for review.
- A prototype may use seeded data; clearly distinguish demo data from production records.
- A real deployment requires security, access controls, privacy review, and operational support.

## Acceptance Criteria for MVP Demonstration

- A member can submit a fault with equipment ID, category, and description.
- Staff can see the newly created ticket in the dashboard.
- Staff can assign an owner and update the ticket status.
- Staff can record a blocker when a repair is delayed.
- A member can locate the equipment's current status without seeing restricted information.
- Ticket changes persist across refreshes if a real backend is configured; otherwise explicitly label the prototype as a simulation.

## Validation

Conduct scenario-based usability testing for member reporting, member status lookup, and staff assignment. Capture success, task time, errors, and feedback. Do not claim real-world repair improvements from a prototype test.

## Why This Scope?

This is the smallest coherent workflow that can test GymFix's proposed value beyond a simple online reporting form. Scope should be revised when user feedback or implementation constraints reveal a better approach.
