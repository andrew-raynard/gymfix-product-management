# GymFix — User Stories and Acceptance Criteria

**Phase:** 5 — Product Requirements | **Status:** Draft / testable specification | **Date:** 16 October 2026

All stories below describe intended MVP behaviour, not already implemented functionality. Acceptance criteria use Given / When / Then format.

## US-01 — Identify equipment (Must)
**As a** gym member, **I want** to open a link for a specific machine, **so that** I report the correct equipment.
- **Given** a valid equipment link, **when** I open it, **then** I see the equipment name and location.
- **Given** an invalid equipment ID, **when** I open the page, **then** I see a helpful not-found state and cannot submit against it.

## US-02 — Submit fault report (Must)
**As a** gym member, **I want** to submit a fault category and optional details, **so that** staff can investigate.
- **Given** valid equipment and a selected fault category, **when** I submit, **then** one ticket is persisted with status `Reported`, a unique reference and a timestamp.
- **Given** a missing fault category, **when** I submit, **then** the form displays a validation error and creates no ticket.
- **Given** a network failure, **when** submission fails, **then** I see an error and am not falsely told the ticket was saved.

## US-03 — See acknowledgement and public status (Must)
**As a** gym member, **I want** a confirmation and status view, **so that** I know the report was received.
- **Given** a successful submission, **when** confirmation appears, **then** it includes the ticket reference.
- **Given** a ticket whose status changes, **when** I reload its public page, **then** the latest public status is shown.
- **Given** a public status view, **when** I inspect it, **then** private staff notes and identities are absent.

## US-04 — View ticket dashboard (Must)
**As a** branch staff member, **I want** to review open maintenance tickets, **so that** I can manage the backlog.
- **Given** an authenticated staff account, **when** I open the dashboard, **then** I see persisted tickets and their equipment, status and owner.
- **Given** status or equipment filters, **when** I apply them, **then** the list updates correctly.
- **Given** an unauthenticated user, **when** they request private ticket data, **then** backend access is denied.

## US-05 — Assign maintenance owner (Must)
**As a** manager, **I want** to assign a ticket to a technician, **so that** ownership is explicit.
- **Given** an unassigned `Reported` ticket, **when** I assign a valid technician, **then** its owner is persisted and its status becomes `Assigned`.
- **Given** a staff user without assignment permission, **when** they attempt assignment, **then** the backend rejects it.

## US-06 — Update repair progress (Must)
**As a** technician, **I want** to update an assigned ticket, **so that** staff know its current state.
- **Given** an assigned ticket, **when** I begin work, **then** I can move it to `In Progress`.
- **Given** an invalid status transition, **when** I attempt it, **then** the update is rejected with an explanation.
- **Given** a successful update, **when** I reload the page, **then** the new status remains visible.

## US-07 — Record repair blocker (Must)
**As a** technician, **I want** to record a delay reason, **so that** staff can coordinate next steps.
- **Given** an `In Progress` ticket, **when** I set it to `Awaiting Parts`, **then** a blocker category is required.
- **Given** a recorded blocker, **when** authorised staff view the ticket, **then** they can see the category and internal note.
- **Given** a public user, **when** they view the ticket, **then** the internal blocker note is hidden.

## US-08 — Confirm resolution (Must)
**As a** manager, **I want** to confirm repairs, **so that** tickets close only after review.
- **Given** an `In Progress` ticket, **when** I enter a completion note and confirm resolution, **then** status becomes `Resolved` and a resolution timestamp is recorded.
- **Given** a `Resolved` ticket, **when** authorised staff reopen it, **then** status becomes `In Progress` and the event is logged.

## US-09 — Review ticket history (Should)
**As a** staff member, **I want** to review status and assignment changes, **so that** I can understand the repair timeline.
- **Given** ticket changes, **when** I open its history, **then** I see ordered events with timestamps.
- **Given** a public user, **when** they view ticket status, **then** internal event details are not exposed.

## Definition of Done
- Acceptance criteria demonstrated against persisted backend data.
- Backend permissions tested for public, staff and technician roles.
- Mobile and desktop main flows checked.
- Validation, loading, empty and failure states present.
- Known limitations recorded; no fabricated usability or operational results.
