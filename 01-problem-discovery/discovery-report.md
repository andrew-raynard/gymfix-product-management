# GymFix — Phase 1 Problem Discovery Report (Updated)

**Project:** GymFix | **Role:** Independent PM case study | **Updated:** 14 October 2026  
**Status:** Secondary discovery complete; market and usability validation pending.

## Executive summary

A qualitative review of **22 selected public accounts/comments across 11 Reddit discussion threads** found recurring reports of equipment downtime, repair coordination difficulties, and uncertainty about repair progress. Several counterexamples described quick repairs or inexpensive existing processes. These are **not 22 independent gym users**, and the findings cannot establish prevalence, causation, or market demand. The linked [evidence log](GymFix_Research_Evidence_Log_v2.xlsx) records each paraphrase, thread, coding and caveat.

## Problem framing

**Initial hypothesis:** Gym members find it inconvenient to report broken equipment.  
**Revised hypothesis:** Some gym members and operators experience a breakdown between reporting an equipment fault, coordinating the repair, and communicating progress. A lightweight shared ticket workflow *may* help, if it offers more value than existing low-cost methods.

## Research questions

1. Where in the report-to-repair journey do problems occur?
2. Are problems driven by missing reports, technician/parts constraints, or status communication?
3. Which operators would need a dedicated product rather than forms, email, or existing software?
4. What should an MVP test before investing in advanced features?

## Methodology and limits

- Desk research of public Reddit member/operator discussions and official vendor websites, reviewed October 2026.
- 22 **purposefully selected comments/accounts**, coded with one primary theme each, from 11 discussion threads. Multiple comments can come from one thread or potentially the same respondent.
- Dates and roles are based on publicly displayed information and self-description; identities and operational claims are unverified.
- Comments are paraphrased, not copied. Original thread URLs are in the workbook. No interviews, representative survey, internal gym data, or real pilot were conducted.
- **No numerical inference about gym populations or willingness to pay is warranted.** The counts below describe this selected sample only.

## Thematic synthesis

| Primary theme | Selected accounts | Interpretation |
|---|---:|---|
| Downtime | 5 | Qualitative signal; not prevalence |
| Repair variability | 4 | Qualitative signal; not prevalence |
| Existing alternatives | 4 | Qualitative signal; not prevalence |
| Repair coordination | 3 | Qualitative signal; not prevalence |
| Status visibility | 3 | Qualitative signal; not prevalence |
| Reporting friction | 1 | Qualitative signal; not prevalence |
| Repair quality | 1 | Qualitative signal; not prevalence |
| Willingness to pay | 1 | Qualitative signal; not prevalence |

**Evidence supporting the opportunity:** Members describe broken equipment remaining unavailable, sometimes without clear updates. A self-described technician explains that parts, travel, and missed work orders can create genuine operational delays. [Member discussion](https://www.reddit.com/r/PlanetFitnessMembers/comments/1t4t0nk/lengthy_repairs/) · [Technician discussion](https://www.reddit.com/r/PlanetFitnessMembers/comments/1h2ef64) · [GoodLife discussion](https://www.reddit.com/r/goodlifefitness/comments/1ron5pa/how_long_does_it_take_for_the_broken_machines_to/)

**Evidence against an overly broad claim:** Some members report quick repairs. An operator describes QR stickers plus Google Forms as sufficient and says they would not pay a recurring subscription for simple reporting. Another commenter says spreadsheets and communication work well. [GoodLife counterexamples](https://www.reddit.com/r/goodlifefitness/comments/1sr7vkg/are_goodlifes_usually_like_this/) · [Owner discussion](https://www.reddit.com/r/gymowner/comments/1vaikzu/gym_owners_how_does_your_team_find_out_when/) · [Spreadsheet alternative](https://www.reddit.com/r/gymowner/comments/1uk0x7z/gym_equipment_repair/)

## Competitive analysis

| Alternative | What is publicly described | Implication |
|---|---|---|
| [Orbit4](https://orbit4.org/us/) | Asset register, ticketing, technician statuses, service metrics | End-to-end maintenance workflow is not new |
| [GymGuard](https://gymguard.io/) | QR member reporting, photo/text, repair notification | QR and member updates are not unique differentiators |
| [KineticPro](https://kineticpro.app/) | QR asset records, service tickets, maintenance history | Asset-linked reporting is already available |
| QR + Google Forms | An operator reports inexpensive QR forms sent to email | GymFix must justify switching costs and ongoing expense |

*Competitor capabilities are vendor claims, not independently tested usability or pricing comparisons.*

## Opportunity assessment

**Potential target:** Independent or smaller multi-branch gyms **as a hypothesis**, not an established underserved segment.  
**User problem to test:** Staff need to know which equipment is broken, who owns the repair, and why it is delayed; members need confidence that a reported issue is acknowledged.  
**Value proposition hypothesis:** A shared, lightweight maintenance workflow that closes the loop from report to resolution without requiring members to install an app.

### Risks and uncertainties

- A reporting app cannot itself solve vendor parts shortages or insufficient technicians.
- Existing QR/form workflows may already be good enough for small operators.
- Public online accounts skew toward people motivated to post.
- Most sampled accounts are from outside Singapore; local relevance remains unverified.
- No willingness-to-pay, adoption, or measured repair-time data exists for GymFix.

## Decision and next steps

**Decision: Proceed to a narrowly scoped prototype as a learning experiment, not a validated business launch.**

1. Test a report → acknowledgement → assignment → blocked/in-progress → resolved flow.
2. Make ticket status and repair blockers visible to staff; evaluate optional member-facing status.
3. Compare this workflow with a basic QR + Google Form baseline.
4. If possible, conduct 3–5 short usability sessions and 1–2 operator conversations; document what is actually observed.
5. Define success measures before testing: reporting task completion, time to submit, clarity of status, and staff workflow completion.

## Portfolio integrity note

This is an independent, secondary-research-led case study. No interviews, adoption figures, business impact, or production deployments are claimed. Qualitative coding counts must not be presented as representative statistics.
