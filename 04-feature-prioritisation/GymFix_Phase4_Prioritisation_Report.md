# GymFix — Feature Prioritisation Report

**Phase:** 4 — Feature Prioritisation  
**Date:** October 2026  
**Status:** Proposed MVP; research-based hypotheses, not validated demand

## Decision Summary

GymFix's proposed MVP focuses on a single reporting-to-resolution workflow: equipment fault reporting, centralised ticket management, ticket assignment, repair status tracking, and a lightweight repair-blocker field.

The decision is based on preliminary secondary research into equipment downtime, maintenance coordination, and repair visibility. No production analytics, actual reach forecasts, or engineering estimates are available.

## RICE Method

**RICE = Reach × Impact × Confidence / Effort**

- Reach: estimated affected interactions per 100 hypothetical monthly maintenance interactions (not users).
- Impact: 3 massive; 2 high; 1 medium; 0.5 low; 0.25 minimal.
- Confidence: 0.8, 0.6, or 0.4 subjective evidence confidence.
- Effort: illustrative person-weeks, not engineering commitments.

See [RICE workbook](GymFix_Phase4_RICE_Prioritisation.xlsx) for editable assumptions and formula-driven scores.

## Feature Priorities

| Feature | Reach | Impact | Confidence | Effort | RICE | Proposed decision |
|---|---:|---:|---:|---:|---:|---|
| QR-based fault reporting | 80 | 2 | 60% | 1 | 96.0 | MVP |
| Centralised ticket dashboard | 95 | 3 | 60% | 2 | 85.5 | MVP |
| Ticket assignment | 65 | 3 | 60% | 1.5 | 78.0 | MVP |
| Repair status tracking | 90 | 2 | 60% | 1.5 | 72.0 | MVP |
| Repair blocker tracking | 55 | 2 | 60% | 1.5 | 44.0 | MVP-lite |
| Fault photo upload | 55 | 1 | 40% | 1 | 22.0 | Later |
| Maintenance history | 45 | 1 | 60% | 2 | 13.5 | Later |
| Member notifications | 60 | 1 | 40% | 2 | 12.0 | Later |
| Multi-branch dashboard | 25 | 1 | 40% | 3 | 3.3 | Later |
| Predictive maintenance | 10 | 2 | 40% | 8 | 1.0 | Later |

All values are hypothetical prioritisation assumptions, not observed customer data. Scores may change substantially after testing.

## Why These Features?

The MVP must support an end-to-end maintenance workflow. Reporting alone would duplicate existing inexpensive tools; adding assignment and status tracking tests the proposed operational value. Blocker tracking is kept lightweight because repair delays can stem from external dependencies.

## Explicit Trade-offs

- **No predictive AI:** lacks historical data, adds complexity, and does not validate the core workflow.
- **No multi-branch features:** start with one gym location to limit complexity.
- **No automatic notifications:** test whether users value status visibility before implementing delivery, consent, and privacy workflows.
- **No advanced reporting:** prioritise operational reliability over analytics polish.
- **No photo uploads initially:** test whether structured descriptions are sufficient before adding file storage.

## MVP Success Criteria

In a prototype usability test, evaluate: reporting task completion, median reporting time, status lookup success, ticket assignment success, and critical usability blockers. Proposed targets are >=90% task success and <=60 seconds median reporting time; these are goals, not achieved results.

A production pilot would additionally need reliable operational baselines, repair time, ticket reopening rate, and adoption measurements.

## Open Risks and Validation Questions

1. Do small gyms actually need a dedicated system beyond Forms and messaging apps?
2. Will staff reliably update statuses and assignments?
3. Do members prefer QR reporting to speaking to staff?
4. Can a digital workflow meaningfully improve coordination when parts or technicians are unavailable?
5. Are our impact, reach, and effort assumptions directionally accurate?

## Next Step

Proceed to Phase 5: PRD, user stories, acceptance criteria, and instrumentation requirements. Revisit prioritisation after usability testing.
