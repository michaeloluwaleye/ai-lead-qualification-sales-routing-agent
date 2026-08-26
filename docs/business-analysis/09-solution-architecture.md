# AI Lead Qualification & Sales Routing Agent

## Solution Architecture v1.0

**Organisation:** NexaFlow Solutions  
**Project Type:** Portfolio Simulation  
**Document Status:** Draft  
**Version:** 1.0

## 1. Purpose

This document translates the approved business requirements, TO-BE process, product backlog and user stories into a technical solution architecture for the AI Lead Qualification & Sales Routing Agent.

The architecture defines the responsibilities of the source system, automation platform, AI component, validation layer, deterministic routing logic and human-review process.

The design follows the principle that AI should provide structured decision support while deterministic automation controls business actions.

---

## 2. Proposed Technology Stack

| Component | Proposed Technology | Responsibility |
| --- | --- | --- |
| Lead / Contact Source | Brevo | Stores incoming lead/contact information |
| Automation Orchestration | Make.com | Coordinates workflow execution and system integrations |
| AI Qualification | OpenAI via Make.com | Analyses lead information against defined qualification criteria |
| Structured Data Handling | JSON | Provides predictable machine-readable AI output |
| Validation | Make.com functions / filters / JSON parsing | Validates input and AI output before routing |
| Decision Routing | Make.com Router + Filters | Applies deterministic business rules |
| Human Review / Notification | Slack | Receives uncertain, exceptional or priority lead notifications |
| Decision Record | Appropriate structured datastore / system field | Records qualification and routing outcomes |

---

## 3. High-Level Architecture

Lead Created in Brevo

↓

Make.com Detects New Lead

↓

Lead Data Retrieved and Mapped

↓

Input Validation

↓

AI Qualification Request

↓

Structured JSON Response

↓

JSON Parsing and Output Validation

↓

Deterministic Business Rules

↓

Make.com Router

↓

High / Medium / Low / Human Review / Error Path

↓

Relevant Action or Notification

↓

Qualification and Routing Outcome Recorded

---

## 4. Component Responsibilities

### 4.1 Brevo — Lead Source

Brevo will act as the initial lead/contact source for the MVP.

Relevant lead information will be retrieved and passed into the automation workflow for qualification.

The exact fields used will be confirmed during implementation based on the available Brevo contact structure and qualification requirements.

---

### 4.2 Make.com — Orchestration Layer

Make.com will coordinate the end-to-end workflow.

Responsibilities include:

- Detecting eligible new leads.
- Retrieving and mapping lead information.
- Performing input validation.
- Sending qualification requests to the AI component.
- Receiving AI responses.
- Parsing and validating structured output.
- Applying routing conditions.
- Executing approved downstream actions.
- Handling defined exceptions and errors.

Make.com therefore acts as the workflow orchestration and control layer.

---

### 4.3 AI Qualification Component

The AI component will analyse lead information against predefined qualification criteria.

Its responsibility is to produce structured decision-support information rather than independently execute business actions.

The expected output will include fields such as:

- qualification_status
- priority
- score
- confidence
- reasoning
- recommended_action

The final schema and permitted values will be defined during implementation.

---

## 5. Structured AI Output

The AI response will use JSON or an equivalent predefined structured format.

Illustrative structure:

{
  "qualification_status": "qualified",
  "priority": "high",
  "score": 85,
  "confidence": 0.92,
  "reasoning": "Decision explanation",
  "recommended_action": "priority_sales_follow_up"
}

Structured output is required because downstream automation should not depend on unpredictable free-text responses.

---

## 6. AI Output Validation

The AI response must be validated before it can influence downstream workflow behaviour.

Validation may include:

- Required fields are present.
- JSON structure is valid.
- Priority contains an approved value.
- Score falls within the defined range.
- Confidence falls within the defined range.
- Qualification status contains an approved value.
- Required decision context is available.

Malformed, incomplete or invalid AI output must not proceed through the normal automated routing path.

---

## 7. Deterministic Routing

Validated AI output will be evaluated against explicit business rules within the automation layer.

The AI may recommend a classification or action, but Make.com routing rules will determine the actual workflow path.

Illustrative routing logic:

### High Priority

If:

- qualification status is valid,
- priority = HIGH,
- confidence meets the approved threshold,

Then:

- Route to the high-priority sales path.
- Notify the appropriate stakeholder where configured.
- Record the decision.

### Medium Priority

If:

- priority = MEDIUM,
- output passes validation,

Then:

- Route to the standard follow-up process.
- Record the decision.

### Low Priority

If:

- priority = LOW,
- output passes validation,

Then:

- Route to the low-priority or nurture process.
- Record the decision.

### Human Review

If:

- confidence is below the approved automation threshold,
- information is insufficient,
- the result is ambiguous,
- or another defined review condition occurs,

Then:

- Prevent inappropriate automatic action.
- Route the case for human review.
- Provide sufficient qualification context to the reviewer.

---

## 8. Human-in-the-Loop Design

Human oversight will be retained for decisions where automated processing should not be trusted without review.

Human review may be triggered by:

- Low AI confidence.
- Missing or insufficient lead information.
- Conflicting qualification indicators.
- Invalid or unexpected AI output.
- Defined exceptional cases.

The reviewer should receive enough information to understand:

- The lead.
- The AI assessment.
- The reasoning.
- The confidence level.
- Why human review was triggered.

---

## 9. Error and Exception Handling

The workflow must fail safely.

Potential exceptions include:

- Missing lead data.
- API failure.
- AI service failure.
- Invalid JSON.
- Missing required AI fields.
- Unexpected classification values.
- Downstream integration failure.

Where a critical error occurs, the workflow must not continue as though successful.

Appropriate error information should be recorded or communicated to support investigation.

---

## 10. Separation of Responsibilities

The architecture deliberately separates responsibilities between AI, deterministic automation and human judgement.

### AI

Responsible for:

- Interpreting lead information.
- Applying qualification reasoning.
- Producing structured decision-support output.

### Automation

Responsible for:

- Validation.
- Business-rule enforcement.
- Routing.
- System actions.
- Error handling.
- Logging and traceability.

### Human

Responsible for:

- Reviewing uncertain or exceptional cases.
- Applying judgement where automation confidence is insufficient.
- Overriding or correcting decisions where appropriate.

This separation reduces the risk of uncontrolled AI behaviour while retaining the benefits of AI-assisted decision-making.

---

## 11. MVP Architecture Principle

The MVP will prioritise:

- Controlled AI use.
- Structured data.
- Deterministic routing.
- Human oversight.
- Traceability.
- Error handling.
- Maintainable workflow design.

The objective is not maximum autonomy.

The objective is reliable and explainable automation of the lead qualification process.

---

## 12. Architecture Outcome

The proposed architecture provides the technical bridge between the analysed business requirements and the implementation of the working automation.

The next stage will define the detailed lead qualification criteria, scoring model, AI output schema and routing rules required before the workflow is configured in Make.com.
