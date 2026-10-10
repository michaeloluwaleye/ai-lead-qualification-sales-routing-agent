# UAT summary and defect remediation

**Outcome:** MVP UAT passed with accepted/deferred non-functional items.

| ID | Scenario | Result |
|---|---|---|
| E01 | Complete workflow | Verified configuration |
| E02 | Hot lower boundary: 11 | Pass |
| E03A | Warm lower boundary: 6 | Pass |
| E03B | Warm upper boundary: 10 | Pass |
| E04 | Cold nurture routing | Pass |
| E05 | Missing required data | Manual review |
| E06 | Unrecognised company size | Blocked after remediation |
| E07 | Slack downstream failure | Three attempts; Unresolved |

## Defect found during UAT
**Observed:** Company Size `Unknown`, budget 3 and timeline 3 resulted in a Warm score of 6.

**Root cause:** unrecognised company size contributed zero because there was no recognised-value gate before scoring.

**Fix:** inserted Router 17 after normalisation to reject invalid scoring values and send the lead to Slack manual review.

**Regression:** `InvalidScoreRetest` and `InvalidScoreRecoveryTest` confirmed invalid data was blocked.

## Resilience test
An intentionally invalid Slack destination triggered `channel_not_found (200)`; the execution retried three times and remained Unresolved. A later fresh test succeeded after Slack restoration. The retained failed execution was not demonstrated as automatically recovered.

## Accepted/deferred
No measured ROI, 100-lead load test, consolidated audit store or independently verified full privacy/security review. Required-field alerts did not dynamically enumerate every missing field.
