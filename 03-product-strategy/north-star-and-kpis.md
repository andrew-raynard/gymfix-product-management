# GymFix — North Star Metric & KPI Framework

**Project:** GymFix  
**Phase:** 3 — Product Strategy  
**Date:** October 2026  
**Status:** Proposed Measurement Framework

## 1. Purpose

This document defines how GymFix would measure product value, user experience, and operational performance.

Metrics are designed to evaluate whether GymFix improves equipment maintenance coordination and reporting visibility.

No production data or validated business results are currently available.

## 2. North Star Metric

### Weekly Confirmed Maintenance Resolutions

**Definition:** Number of unique equipment maintenance tickets confirmed as successfully resolved through GymFix during a calendar week.

**Calculation:**

Weekly Confirmed Resolutions = Count of distinct tickets with a confirmed resolution timestamp during the week.

Each ticket should count once per confirmed resolution cycle, excluding duplicate or test tickets.

### Why This Metric?

- Focuses on completed maintenance workflows.
- Connects reporting to operational outcomes.
- Encourages clear ticket ownership and resolution tracking.
- Can be measured through structured ticket data.

### Limitations

- Higher resolution counts may reflect more equipment failures.
- Gym size and equipment volume affect ticket counts.
- Closing tickets does not guarantee repair quality.
- Repair outcomes depend on external operational factors.

Therefore, the North Star Metric must be interpreted alongside guardrail metrics.

## 3. KPI Framework

### A. Adoption Metrics

**Weekly Active Staff**

Definition: Number of unique staff members performing at least one meaningful maintenance action during a week.

Examples of qualifying actions:
- Assigning a ticket.
- Updating repair status.
- Recording a repair blocker.
- Confirming resolution.

**Digital Reporting Adoption Rate**

Formula:

GymFix reports / All known equipment fault reports × 100%

Requires an independent record of faults submitted through other channels.

### B. Efficiency Metrics

**Median Fault Reporting Time**

Definition: Median duration from opening the reporting form to successful submission.

Target for prototype testing: <= 60 seconds.

**Median Ticket Assignment Time**

Definition: Median duration between ticket creation and first assignment.

Operational pilot target: <= 4 hours for at least 90% of eligible tickets.

The four-hour threshold is a proposed service-level objective, not an established industry benchmark.

### C. Operational Metrics

**Ticket Resolution Time**

Definition: Time from ticket creation to confirmed repair resolution.

Report median and 90th-percentile resolution times.

**Ticket Resolution Rate**

Definition: Percentage of tickets created in a defined cohort that are confirmed resolved within a specified observation period.

Formula:

Resolved eligible tickets in cohort / All eligible tickets in cohort × 100%

The cohort, observation period, and exclusions must be documented.

**Ticket Assignment Coverage**

Formula:

Open tickets with an assigned owner / All open tickets requiring assignment × 100%

Proposed pilot target: >= 95%.

### D. Quality & Experience Metrics

**Ticket Reopening Rate**

Formula:

Tickets reopened within seven days / Resolved tickets with seven days of follow-up × 100%

**Reporting Task Success Rate**

Formula:

Participants completing the reporting task successfully / Participants attempting the task × 100%

Proposed prototype target: >= 90%.

**Status Lookup Success Rate**

Formula:

Participants correctly locating equipment repair status / Participants attempting the lookup task × 100%

Proposed prototype target: >= 90%.

## 4. Proposed OKRs

### Objective 1 — Improve Maintenance Accountability

- KR1: >= 95% of open tickets requiring assignment have an assigned owner.
- KR2: >= 90% of eligible tickets are assigned within four hours.

### Objective 2 — Improve Repair Visibility

- KR1: >= 90% of usability-test participants can correctly locate ticket status.

### Objective 3 — Reduce Reporting Friction

- KR1: >= 90% reporting task success.
- KR2: Median reporting completion time <= 60 seconds.

All targets are provisional and subject to baseline measurement and testing.

## 5. Measurement Plan

### Prototype Testing

Metrics that can be evaluated without a live gym deployment:

- Reporting task success.
- Reporting completion time.
- Status lookup success.
- Staff ticket assignment success.
- Critical usability issues.

### Operational Pilot

Metrics requiring a real gym environment:

- Weekly confirmed maintenance resolutions.
- Digital reporting adoption.
- Ticket assignment time.
- Ticket resolution time.
- Ticket reopening rate.
- Weekly active staff.

## 6. Suggested Event Tracking

| Event | Trigger | Key Properties |
|---|---|---|
| report_started | Reporting form opened | Equipment ID, timestamp |
| report_submitted | Ticket successfully created | Ticket ID, equipment ID, timestamp |
| ticket_assigned | Staff assigns ticket | Ticket ID, assignee ID, timestamp |
| status_updated | Ticket status changes | Ticket ID, old status, new status |
| blocker_recorded | Repair blocker added | Ticket ID, blocker category |
| ticket_resolved | Repair marked complete | Ticket ID, timestamp |
| resolution_confirmed | Repair completion verified | Ticket ID, confirmation timestamp |
| ticket_reopened | Previously resolved ticket reopened | Ticket ID, timestamp |

Tracking should avoid unnecessary collection of personal information.

## 7. Guardrail Metrics

To prevent misleading interpretations of the North Star Metric, GymFix should also monitor:

- Ticket reopening rate.
- Unresolved ticket backlog.
- Repair resolution time.
- Data completeness.
- Staff workflow completion.

A rise in resolved ticket volume should not be considered successful if repair quality deteriorates.

## 8. Baselines and Targets

No real operational baselines have been established.

Targets in this document are planning hypotheses rather than achieved performance.

During testing, actual results will be compared against these targets and documented transparently.

## 9. Risks and Limitations

- Small usability-test samples limit generalisability.
- Prototype task completion does not prove real-world adoption.
- GymFix cannot directly control technician or spare-part availability.
- Staff may update statuses inconsistently.
- Ticket closure may not reflect actual equipment availability.

## 10. Next Steps

- Define MVP features in Phase 4.
- Establish event-tracking requirements in the PRD.
- Test critical workflows using the Lovable prototype.
- Record actual task completion times and success rates.
- Revise targets based on observed results.

---

*Independent Product Management case study. All KPI targets are proposed and have not yet been achieved.*
