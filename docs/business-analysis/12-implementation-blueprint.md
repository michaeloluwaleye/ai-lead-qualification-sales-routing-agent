# AI Lead Qualification & Sales Routing Agent

## Implementation Blueprint v1.0

**Organisation:** NexaFlow Solutions  
**Project Type:** Portfolio Simulation  
**Document Status:** Draft  
**Version:** 1.0

## 1. Purpose

This document translates the approved solution architecture, qualification model and structured AI output contract into an implementation sequence for the MVP.

The blueprint will guide the incremental Make.com build and provide a reference for module configuration, testing and troubleshooting.

---

## 2. MVP Implementation Flow

The MVP will implement the following sequence:

1. Detect new lead.
2. Retrieve and map lead data.
3. Validate required input.
4. Route insufficient input to human review.
5. Submit valid lead data for AI qualification.
6. Receive structured AI output.
7. Parse the structured response.
8. Validate required output fields and permitted values.
9. Validate component scores and total score.
10. Evaluate confidence and mandatory human-review conditions.
11. Apply deterministic priority rules.
12. Route the lead to the appropriate operational path.
13. Notify relevant users where required.
14. Record qualification and routing outcomes.
15. Handle defined workflow exceptions.

---

## 3. Proposed Implementation Components

| Stage | Component | Primary Responsibility |
| --- | --- | --- |
| 1 | Brevo Trigger | Detect eligible new leads |
| 2 | Lead Data Mapping | Prepare required qualification inputs |
| 3 | Input Validation | Check whether sufficient information exists |
| 4 | OpenAI Qualification | Evaluate lead against approved scoring criteria |
| 5 | Structured Output | Return qualification result using agreed JSON contract |
| 6 | JSON Parsing | Convert AI response into mapped workflow fields |
| 7 | Output Validation | Validate fields, types, ranges and permitted values |
| 8 | Score Validation | Verify component scores and total |
| 9 | Confidence Control | Determine whether human review is mandatory |
| 10 | Make Router | Separate operational processing paths |
| 11 | High-Priority Route | Notify sales / priority handling |
| 12 | Medium-Priority Route | Standard follow-up processing |
| 13 | Low-Priority Route | Nurture / low-priority processing |
| 14 | Human-Review Route | Escalate uncertain or exceptional cases |
| 15 | Outcome Logging | Record qualification and routing result |
| 16 | Error Handling | Capture defined technical failures |

---

## 4. Planned Routing Paths

The workflow will contain the following logical routes:

### Route A — High Priority

Used when:

- Input is valid.
- AI output passes validation.
- No mandatory human-review condition exists.
- Validated total score is between 75 and 100.
- Confidence meets the approved threshold.

Expected action:

- Priority sales notification.
- Qualification outcome recorded.

### Route B — Medium Priority

Used when:

- Input is valid.
- AI output passes validation.
- No mandatory human-review condition exists.
- Validated total score is between 50 and 74.
- Confidence meets the approved threshold.

Expected action:

- Standard follow-up handling.
- Qualification outcome recorded.

### Route C — Low Priority

Used when:

- Input is valid.
- AI output passes validation.
- No mandatory human-review condition exists.
- Validated total score is between 0 and 49.
- Confidence meets the approved threshold.

Expected action:

- Nurture or low-priority handling.
- Qualification outcome recorded.

### Route D — Human Review

Used where a mandatory review condition occurs, including:

- Insufficient lead information.
- Confidence below 0.60.
- Ambiguous qualification.
- Defined validation exception.
- Other approved review conditions.

Expected action:

- Automated sales routing blocked.
- Reviewer notified with relevant context.
- Review requirement recorded.

### Route E — Technical Exception

Used for defined processing failures such as:

- AI/API failure.
- Parsing failure.
- Integration error.
- Unexpected technical exception.

Expected action:

- Normal processing blocked where necessary.
- Error context captured.
- Appropriate operational notification generated where configured.

---

## 5. Build Strategy

The workflow will be built incrementally rather than configuring the complete scenario before testing.

### Build Increment 1

**Lead Trigger + Data Retrieval**

Objective:

Confirm that Make.com can detect and retrieve the required Brevo lead information.

### Build Increment 2

**Input Mapping + Validation**

Objective:

Confirm that lead information is mapped correctly and incomplete input follows the intended control path.

### Build Increment 3

**AI Qualification**

Objective:

Configure the qualification instructions and verify structured AI responses against representative test leads.

### Build Increment 4

**JSON Parsing + Output Validation**

Objective:

Parse AI output and validate required fields, permitted values and score ranges.

### Build Increment 5

**Scoring + Deterministic Routing**

Objective:

Implement score validation, confidence controls and High / Medium / Low / Review routing.

### Build Increment 6

**Notifications + Human Review**

Objective:

Configure operational notifications and provide sufficient context for human review.

### Build Increment 7

**Outcome Logging**

Objective:

Record relevant qualification and routing results for traceability.

### Build Increment 8

**Error Handling**

Objective:

Implement controlled handling of defined workflow and integration failures.

### Build Increment 9

**End-to-End Testing**

Objective:

Execute representative test scenarios covering normal, uncertain and failure conditions.

---

## 6. Implementation Control Principle

The workflow will follow this control sequence:

**Validate Input**

→ **AI Interpretation**

→ **Validate AI Output**

→ **Validate Scores**

→ **Evaluate Human-Review Conditions**

→ **Apply Deterministic Business Rules**

→ **Execute Permitted Action**

→ **Record Outcome**

This sequence ensures that probabilistic AI output is controlled before it influences operational actions.

---

## 7. Build Evidence

Evidence will be captured throughout implementation, including:

- Make.com scenario screenshots.
- Module configuration evidence where appropriate.
- Representative test inputs.
- Structured AI outputs.
- Routing test results.
- Human-review examples.
- Error-handling evidence.
- Final end-to-end workflow diagram.

Sensitive credentials, API keys and connection information must not be included in portfolio evidence or GitHub.

---

## 8. Implementation Outcome

The blueprint establishes the implementation sequence for the working MVP.

The project will now move from analysis and design into incremental Make.com development, with each build increment validated before the next capability is introduced.
