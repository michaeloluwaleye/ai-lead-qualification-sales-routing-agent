# Case study: lead qualification and sales routing

## Context
Self-directed portfolio simulation of a B2B sales team assessing incoming leads.

## Challenge
Manual lead assessment can delay sales follow-up and produce inconsistent prioritisation, particularly when data is missing or ambiguous.

## Business Analysis
I defined the problem, mapped AS-IS and TO-BE workflows, wrote requirements, prioritised with MoSCoW, documented user stories and acceptance criteria, and traced the tests to requirements.

## Engineering
I implemented Brevo → Make → Slack/Brevo, with required-field validation, normalisation, a recognised-value gate, deterministic 15-point scoring and Hot/Warm/Cold routing. Invalid and incomplete inputs go to human review.

## Testing and problem solving
UAT covered boundaries 5/6/10/11, missing data, unrecognised values and downstream failures. I discovered that Unknown company size could create a Warm classification; I implemented Router 17 and verified the fix with regression testing.

## Results
The MVP demonstrates consistent automated classification, prioritised alerts, nurture routing and visible exception handling.

## What I would do next
Pilot with real users, add a consolidated audit store, monitor operational outcomes, test expected volume, improve error messages and complete security/privacy reviews.

**No production savings or client outcomes are claimed.**
