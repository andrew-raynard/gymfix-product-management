# GymFix — Lovable MVP Build Specification

**Purpose:** Implementation handoff for Phase 6. Do not present generated screens as a functional MVP until persistence and permissions have been tested.

## Prompt to paste into Lovable

Build **GymFix**, a responsive single-branch gym equipment fault reporting and maintenance tracking web application using React and TypeScript. Use a real backend with persisted data and secure authentication/authorisation (Supabase or Lovable's supported backend). The app is a portfolio MVP, not a production-certified gym safety system.

### Roles
1. **Public gym member:** No login required. Can view equipment details, submit a fault report, receive a ticket reference, and view sanitised public ticket status.
2. **Staff/manager:** Authenticated. Can see all tickets, filter by status/equipment/assignee, assign technicians, update statuses, record blockers, confirm resolutions and view history.
3. **Technician:** Authenticated. Can view assigned tickets, update their progress and record blockers. Cannot assign other technicians or confirm final resolution.

Enforce permissions on the backend, not only in the UI. Never allow public visitors to choose a privileged role.

### Screens
- Mobile-friendly equipment report page at a stable URL such as `/equipment/:id/report` (QR-compatible).
- Report confirmation with persisted ticket reference.
- Public equipment/ticket status page that never reveals staff identities or private notes.
- Staff dashboard with filters, ticket details, assignment and status actions.
- Technician assigned-work view.
- Sign-in screen and accessible error/empty/loading states.

### MVP data model
Equipment (id, name, location, active); Ticket (id, equipment_id, fault_category, description, status, assignee_id, created_at, updated_at, resolved_at); StaffProfile (user_id, role, display_name); Blocker (ticket_id, category, internal_note, created_at, cleared_at); TicketEvent (ticket_id, actor_id, event_type, old_value, new_value, created_at).

### Ticket workflow
Statuses: Reported, Assigned, In Progress, Awaiting Parts, Resolved.
Allowed transitions: Reported→Assigned; Assigned→In Progress; In Progress→Awaiting Parts or Resolved; Awaiting Parts→In Progress; Resolved→In Progress (staff reopen). Assignment must specify an authorised technician. Awaiting Parts requires a blocker category. Resolution requires a completion note and manager confirmation. Persist each update and a timestamped event.

### Design
Clean, professional gym operations SaaS. Mobile-first public flow; desktop-friendly staff dashboard. Clear hierarchy, accessible labels, readable contrast and keyboard support. Use realistic **clearly labelled demo data** (e.g., 8 equipment items). Do not invent research outcomes, customer testimonials or business performance results.

### Implementation constraints
- Persist data to a backend; no local-only state masquerading as a working system.
- Add validation and clear failure states; show confirmation only after a successful write.
- Secure private tables and notes with backend access policies.
- Avoid collecting member personal details in the initial public form.
- Do not implement AI diagnosis, predictive maintenance, multi-branch management, billing, push/email notifications, or advanced analytics.

### Acceptance test
Demonstrate this end-to-end: public member submits a treadmill fault → unique ticket persisted → staff assigns technician → technician marks In Progress and Awaiting Parts with a blocker → staff confirms resolution → public status shows Resolved without internal notes → unauthorised write attempts fail. Include instructions for testing with demo accounts without exposing secrets.

Before building extra features, ask for clarification if backend authentication or access-control assumptions are ambiguous.

## Build sequence
1. Generate navigation and UI using demo seed data.
2. Connect real persistence and authentication.
3. Implement permissions and status-transition rules.
4. Run the acceptance scenario and fix failures.
5. Capture screenshots and document actual limitations in Phase 6.
