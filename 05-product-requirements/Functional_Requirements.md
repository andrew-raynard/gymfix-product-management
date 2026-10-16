# GymFix — Functional Requirements and Technical Handoff

**Phase:** 5 | **Status:** Proposed implementation specification

## Roles and permissions
| Action | Public member | Staff/manager | Technician |
|---|---|---|---|
| View public equipment status | Yes | Yes | Yes |
| Submit fault report | Yes | Yes | Yes |
| View private ticket details | No | Yes | Assigned tickets |
| Assign ticket | No | Yes | No |
| Update progress | No | Yes | Assigned tickets |
| Add internal blocker note | No | Yes | Assigned tickets |
| Confirm resolution | No | Yes | No |

All restrictions must be enforced server-side (e.g., database policies), not solely by hiding UI elements.

## Ticket lifecycle
`Reported → Assigned → In Progress → Awaiting Parts → In Progress → Resolved`; `In Progress → Resolved` is also permitted. Staff can reopen `Resolved → In Progress`.

**Rules:** Assignment requires a valid technician; `Awaiting Parts` requires a blocker category; `Resolved` requires staff confirmation and completion note; all status changes create history events.

## Data requirements
- Equipment: stable unique ID, name, location, active flag.
- Ticket: unique ID, equipment ID, fault category, optional description, status, owner, timestamps.
- Staff profile: user ID, role, display name.
- Blocker: ticket ID, category, optional internal note, timestamps.
- Event history: actor, action, old/new value, timestamp.

## UX states
Every form and list should support loading, empty, invalid-input, success and network-error states. Confirm report creation only after the backend returns success. Display safe, plain-language messages; never leak database errors or sensitive details publicly.

## Security and privacy
Anonymous reports do not collect personal identifiers. Public views reveal only safe equipment and ticket-status fields. Authenticated roles use real access controls; do not implement role selection as an unprotected public dropdown. Seed demo accounts/data only in a clearly marked demo environment. Do not publish credentials in the repository.

## Analytics events
`report_started`, `report_submitted`, `ticket_assigned`, `status_updated`, `blocker_recorded`, `ticket_resolved`, `resolution_confirmed`, `ticket_reopened`.

## Demo acceptance scenario
1. Open seeded treadmill equipment page.
2. Submit a fault report and note the ticket ID.
3. Reload and confirm persistence.
4. Sign in as manager, assign a technician.
5. Sign in as technician, update to In Progress, then Awaiting Parts with a blocker.
6. Sign in as manager, confirm resolution with a completion note.
7. Open public status page and confirm it reflects Resolved but hides internal notes.
8. Attempt private edits while signed out; verify backend denies access.
