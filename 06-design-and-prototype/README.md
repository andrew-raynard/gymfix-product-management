# GymFix — Phase 6: Design & Prototype

**Status:** Completed  
**Platform:** Lovable  
**Prototype:** https://gymfix-demo.lovable.app/  
**Implementation:** Interactive browser-based demo

## 1. Objective

Translate the prioritised MVP requirements into a functional prototype demonstrating the equipment maintenance reporting-to-resolution workflow.

## 2. Implemented Features

- Equipment fault reporting
- Unique ticket ID generation
- Staff maintenance dashboard
- Technician assignment
- Technician interface
- Ticket status updates
- Member-facing ticket tracking
- Browser-based data persistence
- Demo role switching

## 3. Design Decisions

### Mobile-Friendly Reporting
Prioritised a straightforward reporting experience with clear equipment identification and minimal required information.

### Role-Specific Interfaces
Separated Member, Staff, and Technician experiences to support their different responsibilities.

### Maintenance Visibility
Introduced ticket statuses to help users understand repair progress.

### Demo Mode
Used browser-based storage and role switching to demonstrate the workflow without implementing production authentication.

## 4. Functional Testing

Seven manual functional checks were performed.

| Test | Result |
|---|---|
| Submit fault report and receive ticket ID | Pass |
| Find ticket in staff dashboard | Pass |
| Assign ticket to technician | Pass |
| Open technician interface | Pass |
| Update ticket status | Pass |
| View updated status as member | Pass |
| Confirm ticket persists after refresh | Pass |

**Result: 7/7 functional checks passed.**

## 5. Iteration and Improvements

The initial prototype contained navigation issues, including pages returning 404 errors.

These issues were addressed before functional testing.

The resulting demo supports the core tested maintenance workflow.

## 6. Limitations

- Browser-based storage is not shared multi-user persistence.
- Demo role switching does not provide authentication.
- Production-level security has not been validated.
- Usability performance has not yet been measured.
- The prototype has not been deployed in an actual gym.

## 7. Product Outcome

Delivered an interactive prototype that demonstrates the proposed fault reporting and maintenance tracking experience.

The prototype provides a foundation for usability testing and further product iteration.

## 8. Next Steps

Proceed to Phase 7: Usability Testing & Iteration.

Evaluate reporting speed, task completion, navigation clarity, and user experience against the proposed success metrics.
