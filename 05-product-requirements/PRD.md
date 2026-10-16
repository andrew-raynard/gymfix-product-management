# GymFix — Product Requirements Document (PRD)

**Version:** 0.1 | **Date:** 16 October 2026 | **Status:** Proposed MVP specification  
**Product:** GymFix | **Owner:** Independent PM case study  
**Research:** [Phase 1](../01-problem-discovery/discovery-report.md) · [Phase 2](../02-user-research/user-personas.md) · [Phase 4](../04-feature-prioritisation/GymFix_Phase4_MVP_Scope.md)

## 1. Executive summary
GymFix is a proposed single-branch, mobile-first equipment fault reporting and maintenance coordination application. Gym members report issues; staff triage, assign and track tickets; technicians update progress; members view public equipment status. The first MVP tests whether a complete reporting-to-resolution workflow is usable and understandable, **not** whether it reduces real repair time.

## 2. Problem and evidence
Public discussions reviewed in Phase 1 suggest that equipment downtime, unclear progress and repair coordination can be frustrating. Some operators already use QR codes, forms or dedicated software. These findings are exploratory, self-selected, and do not establish prevalence, willingness to pay or a validated customer segment.

**Hypothesis:** A lightweight, unified workflow may reduce reporting and coordination friction and improve status visibility for a small gym.

## 3. Users and jobs
| Role | Job to be done | Access |
|---|---|---|
| Member | Report a fault and check whether equipment is available | Public report/status pages, no account required |
| Branch staff/manager | Review, assign, track and close reports | Authenticated staff dashboard |
| Technician | See assigned work and update progress/blockers | Authenticated technician view |

## 4. Goals and non-goals
**Goals:** Demonstrate an end-to-end persisted ticket workflow; make public reporting and status lookup usable; provide explicit ownership and repair blockers; collect testable interaction data.

**Non-goals:** AI diagnosis, predictive maintenance, multi-branch support, payments, automatic push/email notifications, inventory management, and verified improvement to real-world repair turnaround.

## 5. MVP scope
1. Public equipment-specific fault reporting via a seeded equipment directory and QR-compatible URL.
2. Ticket creation with a unique ID and `Reported` initial status.
3. Authenticated staff dashboard with ticket list, filters and details.
4. Staff assignment to a technician and a clear status transition workflow.
5. Staff/technician repair blocker notes and a timestamped history.
6. Public, read-only equipment/ticket status without revealing reporter details or internal notes.

**Implementation note:** QR codes may be generated for stable equipment URLs; a QR scanner is not necessary for the MVP. A direct link should work in the prototype.

## 6. Main user flows
**Member:** Open equipment URL → confirm equipment → choose fault category → add description (optional) → submit → receive ticket reference → see public status.

**Staff:** Sign in → open dashboard → review ticket → assign owner → change status → record blocker if applicable → confirm repair → resolve ticket.

**Technician:** Sign in → see assigned tickets → view fault details → set `In Progress` / `Awaiting Parts` → add work note → notify staff in-app through status update (no automatic messaging).

## 7. Functional requirements
| ID | Requirement | Priority | Verification |
|---|---|---|---|
| FR-01 | Show equipment identifier and location on reporting page | Must | Correct seeded equipment shown |
| FR-02 | Require valid equipment ID and fault category; accept optional description | Must | Invalid inputs blocked |
| FR-03 | Persist ticket with unique ID, creation time and initial `Reported` status | Must | Refresh retains ticket |
| FR-04 | Display confirmation and reference after successful submission | Must | Ticket ID visible |
| FR-05 | Restrict staff dashboard and management actions to authorised accounts | Must | Unauthenticated write blocked server-side |
| FR-06 | List/filter tickets by status, equipment and assignee | Must | Filters return correct tickets |
| FR-07 | Assign or reassign ticket owner | Must | Change persisted and auditable |
| FR-08 | Enforce allowed ticket status transitions | Must | Invalid transitions rejected |
| FR-09 | Allow blocker category and internal note for delayed tickets | Must | Notes stored privately |
| FR-10 | Publish sanitised status on equipment status page | Must | No private details exposed |
| FR-11 | Store timestamped change history | Should | History accurately reflects updates |
| FR-12 | Provide clear loading, empty and error states | Must | Tested for each main view |

## 8. Business rules and ticket lifecycle
**Statuses:** `Reported`, `Assigned`, `In Progress`, `Awaiting Parts`, `Resolved`.

**Allowed transitions:** `Reported → Assigned`; `Assigned → In Progress`; `In Progress → Awaiting Parts` or `Resolved`; `Awaiting Parts → In Progress`; `Resolved → In Progress` (reopen, staff only). Staff may reassign open tickets. A resolution requires a completion note and staff confirmation. Reopened tickets remain linked to their original ID.

Duplicate reports are allowed initially, but the reporting page should display existing unresolved reports for the same equipment before submission; automatic deduplication is deferred.

## 9. Data model (conceptual)
| Entity | Core fields |
|---|---|
| Equipment | id, name, location, active |
| Ticket | id, equipment_id, fault_category, description, status, assignee_id, created_at, updated_at, resolved_at |
| Staff user | id, display_name, role |
| Ticket event | id, ticket_id, actor_id, event_type, old_value, new_value, created_at |
| Blocker | id, ticket_id, category, internal_note, created_at, cleared_at |

Avoid collecting member names, emails or phone numbers for the initial anonymous reporting flow. Use database row-level security or equivalent backend authorisation; client-side role toggles alone are insufficient.

## 10. Non-functional requirements
- Responsive layouts usable on mobile and desktop.
- Keyboard-accessible controls, labels, contrast and clear error messages.
- Persisted backend storage; no local-only mock state represented as production functionality.
- Role-based authorisation enforced on the backend.
- Public pages expose only equipment identifiers, non-sensitive fault categories and public status.
- Basic error handling and recovery after network failure.

## 11. Metrics and instrumentation
**Prototype test:** reporting task completion, median reporting time, status lookup success, assignment success, critical usability failures. Proposed targets: ≥90% task success and ≤60 seconds median reporting time; these are **hypotheses, not achieved outcomes**.

**Future pilot:** weekly confirmed resolutions (proposed North Star), ticket assignment time, repair resolution time, reopened-ticket rate. No live operational baseline exists.

Track `report_started`, `report_submitted`, `ticket_assigned`, `status_updated`, `blocker_recorded`, `ticket_resolved`, `resolution_confirmed`, and `ticket_reopened` with timestamps and ticket IDs; avoid unnecessary personal data.

## 12. Risks, assumptions and dependencies
- Gym operators may prefer existing free forms or maintenance products.
- Members may not scan equipment QR codes.
- Staff may not maintain accurate statuses.
- Repair time depends on technicians, parts and procurement outside GymFix.
- Prototype authentication, database access rules and persistence require explicit verification.

## 13. Release acceptance and validation
The MVP is demo-ready only if: a report persists across refresh; staff can authenticate and assign it; an authorised technician can update it; blockers persist; staff can resolve it; the public status updates; and unauthorised users cannot edit or read internal notes. Test on both mobile and desktop.

## 14. Open decisions
- Which login provider and staff provisioning approach?
- Who is permitted to confirm repair resolution?
- How long should public ticket status remain visible?
- Is equipment QR code printing in scope for a future pilot?

**Next:** Build Phase 6 prototype from this specification, then run Phase 7 usability tests and revise based on observed evidence.
