# Business Analysis deliverables

## Problem and scope
This is a simulated B2B lead qualification process, not an actual client deployment. The objective was to improve consistency of qualification and routing.

## AS-IS
Sales staff manually review incoming leads, interpret qualification details and decide follow-up priority. Potential issues include delay, inconsistency and incomplete lead data.

## TO-BE
Brevo lead intake → completeness checks → value normalisation → recognised-value validation → deterministic scoring → Hot/Warm/Cold routing. Incomplete or invalid inputs go to human review.

## Requirements and priorities
**Must have:** required-field validation; scoring rules; route Hot/Warm/Cold leads; prevent invalid inputs from scoring; manual review exceptions.

**Should have:** visible error handling and traceable UAT evidence.

**Deferred production enhancements:** consolidated audit store, scale/load testing, detailed missing-field messages, extended monitoring and access/privacy review.

## BA methods applied
- AS-IS and TO-BE process modelling
- Functional and non-functional requirements
- MoSCoW prioritisation
- User stories and acceptance criteria
- Requirements Traceability Matrix (RTM)
- UAT planning, evidence and closure

## Example user story
As a sales team member, I want valid incoming leads classified consistently so that urgent opportunities receive priority follow-up.

**Acceptance criteria:** a valid score of 11 routes to Hot; 10 routes to Warm; 5 routes to Cold; unrecognised company size is blocked from scoring and sent to manual review.

## Limitations
No actual sales stakeholders were interviewed for this portfolio simulation. Claimed efficiency gains are hypotheses, not measured customer outcomes.
