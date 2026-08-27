# AI Lead Qualification & Sales Routing Agent

## Lead Qualification & Scoring Model v1.0

**Organisation:** NexaFlow Solutions  
**Project Type:** Portfolio Simulation  
**Document Status:** Draft  
**Version:** 1.0

## 1. Purpose

This document defines the standardised qualification criteria and scoring framework used to evaluate incoming leads within the AI Lead Qualification & Sales Routing Agent.

The model converts the business need for consistent lead prioritisation into explicit decision criteria that can be applied by the AI qualification component and controlled by deterministic workflow rules.

For this portfolio simulation, the scoring model represents assumed business rules and is not derived from historical client conversion data.

---

## 2. Design Principles

The qualification model is designed around the following principles:

- Qualification criteria should be explicit rather than dependent on undefined AI judgement.
- Similar lead characteristics should be assessed consistently.
- Qualification reasoning should remain understandable to human reviewers.
- Missing information should not automatically be interpreted as negative information.
- Lead quality and AI confidence should be treated as separate concepts.
- Uncertain cases should be capable of being escalated for human review.
- Routing actions should remain controlled by deterministic automation rules.

---

## 3. Qualification Criteria

Each lead will be evaluated across five dimensions.

| Criterion | Maximum Score | Purpose |
| --- | ---: | --- |
| Business Fit | 25 | Measures alignment with the target customer profile |
| Role / Decision Influence | 20 | Measures likely ability to influence or make a purchasing decision |
| Need / Use-Case Fit | 25 | Measures evidence of a relevant automation or AI business need |
| Buying Intent | 20 | Measures demonstrated interest, urgency or readiness to engage |
| Information Completeness | 10 | Measures whether sufficient information exists for qualification and follow-up |
| **Total** | **100** | |

---

## 4. Business Fit — Maximum 25 Points

Business Fit assesses whether the organisation appears suitable for NexaFlow Solutions' B2B automation and AI services.

### Illustrative Scoring Guidance

**20–25 points**

Strong alignment with the target customer profile and clear potential relevance for business automation or AI services.

**10–19 points**

Reasonable business alignment, but the opportunity or organisational fit is less clear.

**1–9 points**

Limited evidence of alignment with the target customer profile.

**0 points**

Available information indicates that the lead is outside the defined target business profile.

The AI must base the score only on available lead information and must not invent missing company characteristics.

---

## 5. Role / Decision Influence — Maximum 20 Points

This criterion evaluates whether the contact's role suggests an ability to influence, evaluate or approve relevant business solutions.

### Illustrative Scoring Guidance

**16–20 points**

Senior decision-maker or role with strong likely influence over technology, operations, transformation, sales, marketing or business-process decisions.

**9–15 points**

Managerial, specialist or operational role with plausible involvement in evaluating or recommending relevant solutions.

**1–8 points**

Role appears to have limited purchasing influence based on available information.

**0 points**

No useful role information is available or the information clearly indicates no relevant decision influence.

Missing job-title information should contribute to lower information completeness and should not result in invented role assumptions.

---

## 6. Need / Use-Case Fit — Maximum 25 Points

This criterion measures whether the lead demonstrates a business problem or use case relevant to NexaFlow's services.

Relevant needs may include:

- Repetitive manual processes.
- Workflow inefficiency.
- Business-process automation.
- AI-assisted operations.
- Lead or customer management automation.
- System integration.
- Data movement between applications.
- Customer-support automation.
- Productivity improvement through AI or automation.

### Illustrative Scoring Guidance

**20–25 points**

Clear and specific business need strongly aligned with NexaFlow's services.

**10–19 points**

Potentially relevant need exists, but details or business impact are limited.

**1–9 points**

Weak or indirect evidence of a relevant use case.

**0 points**

No relevant business need can be identified from the available information.

---

## 7. Buying Intent — Maximum 20 Points

Buying Intent evaluates the strength of evidence that the prospect wants to explore, evaluate or acquire a solution.

### Illustrative Scoring Guidance

**16–20 points**

Strong intent such as requesting a consultation, proposal, implementation discussion, pricing information or urgent assistance.

**9–15 points**

Clear interest but without strong evidence of immediate purchasing intent.

**1–8 points**

Early-stage or exploratory interest.

**0 points**

No meaningful evidence of current buying intent.

The AI must distinguish between demonstrated intent and assumptions about what the prospect may eventually want.

---

## 8. Information Completeness — Maximum 10 Points

This criterion evaluates whether sufficient lead information is available to support reliable qualification and follow-up.

Relevant information may include:

- Contact name.
- Email or contact method.
- Company.
- Job title.
- Business need or enquiry.
- Lead source.
- Other relevant contextual information.

### Illustrative Scoring Guidance

**8–10 points**

Sufficient information is available for confident qualification and appropriate follow-up.

**4–7 points**

Some useful information is available, but important context is missing.

**1–3 points**

Significant information is missing and qualification reliability is limited.

**0 points**

Insufficient information exists to support meaningful automated qualification.

---

## 9. Overall Lead Score

The five criteria produce a maximum score of 100.

**Total Lead Score =**

Business Fit  
+ Role / Decision Influence  
+ Need / Use-Case Fit  
+ Buying Intent  
+ Information Completeness

The AI qualification component must provide the individual criterion scores as well as the calculated total score.

The automation layer will validate that the individual scores fall within their permitted ranges and that the total score is mathematically consistent.

---

## 10. Priority Classification

For the MVP, the following simulated thresholds will be used:

### HIGH

**75–100**

The lead demonstrates strong overall qualification characteristics and may warrant priority sales attention.

### MEDIUM

**50–74**

The lead demonstrates reasonable potential but does not currently meet the high-priority threshold.

### LOW

**0–49**

The lead currently demonstrates limited qualification strength based on the available information.

Priority classification alone does not determine whether automatic routing is permitted. Confidence, data completeness and validation conditions must also be considered.

---

## 11. Confidence

Confidence represents the reliability of the AI assessment based on the clarity and completeness of the available evidence.

Confidence is separate from the lead score.

For the MVP, confidence will be represented as a decimal value between:

**0.00 and 1.00**

Illustrative interpretation:

- **0.80–1.00:** High confidence
- **0.60–0.79:** Moderate confidence
- **Below 0.60:** Low confidence / human review required

The initial automated-routing confidence threshold will therefore be:

**0.60**

This threshold is a portfolio simulation assumption and may be adjusted during testing.

---

## 12. Human Review Conditions

A lead must be considered for human review where any defined review condition occurs.

Examples include:

- Confidence below 0.60.
- Insufficient information for reliable qualification.
- Conflicting lead information.
- Invalid AI output.
- Missing required qualification fields.
- Score outside permitted ranges.
- Total score inconsistent with component scores.
- Unexpected classification value.
- Other exceptional conditions identified during testing.

Human review takes precedence over normal automated routing when a review condition is triggered.

---

## 13. Decision Logic

The intended decision sequence is:

**1. Validate lead input**

↓

**2. Perform AI-assisted qualification**

↓

**3. Validate structured AI output**

↓

**4. Validate criterion scores and total**

↓

**5. Evaluate confidence and human-review conditions**

↓

If review required:

**HUMAN REVIEW**

Otherwise:

↓

Evaluate total score

↓

**75–100 → HIGH**

**50–74 → MEDIUM**

**0–49 → LOW**

↓

Execute the corresponding deterministic routing rule.

---

## 14. Explainability

For each qualification decision, the AI should provide concise reasoning based on the available lead information.

The reasoning should explain the principal factors influencing the assessment without inventing facts not contained in the lead data.

Where information is missing or ambiguous, this should be reflected in the assessment rather than replaced with unsupported assumptions.

---

## 15. Scoring Model Governance

Because this project uses simulated business assumptions, the initial weights and thresholds should be treated as configurable business rules rather than permanent values.

In a production implementation, the scoring model should be reviewed using:

- Sales stakeholder feedback.
- Qualification outcomes.
- Conversion data.
- False-positive and false-negative analysis.
- Human-review outcomes.
- Operational performance data.

This would support continuous improvement of the qualification model.

---

## 16. Scoring Model Outcome

The scoring model establishes explicit and testable business rules for lead qualification.

It provides the foundation for defining the structured AI output contract, validation logic and deterministic routing rules that will be implemented within the automation workflow.
