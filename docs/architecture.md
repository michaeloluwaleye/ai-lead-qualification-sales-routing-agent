# Architecture and integration notes

![Workflow architecture](../assets/architecture.svg)

## Platforms
- **Brevo:** source contact records and Cold nurture destination.
- **Make:** 15-minute scheduled orchestration, validation, normalisation, scoring and routing.
- **Slack:** Hot, Warm and manual-review destinations.

## Implementation path
1. Brevo Watch Contacts (module 2)
2. Router 13: complete vs incomplete required fields
3. Tools 3: normalisation
4. Router 17: recognised scoring values
5. Tools 5, 6, 7: deterministic scoring
6. Router 8: Hot/Warm/Cold
7. Slack 9 Hot; Slack 10 Warm; Brevo 12 Cold nurture
8. Invalid: Slack 24; incomplete: Slack 14

## Failure behaviour
A controlled invalid Slack destination caused a failed incomplete execution, three retries and a retained Unresolved state. Restoring the destination allowed a **fresh** invalid-scoring lead to succeed; automatic recovery of the earlier retained execution was not demonstrated.

## Explicit non-features
No automatic archiving, automatic reprocessing of corrected leads, autonomous LLM qualification, persistent consolidated audit database or production monitoring service was implemented or verified.
