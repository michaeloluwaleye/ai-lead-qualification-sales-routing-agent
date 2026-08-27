# AI Lead Qualification & Sales Routing Agent

## Structured AI Output Contract v1.0

**Organisation:** NexaFlow Solutions  
**Project Type:** Portfolio Simulation  
**Document Status:** Draft  
**Version:** 1.0

## 1. Purpose

This document defines the structured data contract between the AI qualification component and the downstream automation workflow.

The contract specifies the fields, data types, permitted values and validation rules required before an AI qualification result can influence automated routing.

The objective is to ensure that downstream business actions depend on predictable, machine-readable and validated AI output rather than unrestricted natural-language responses.

---

## 2. Design Principle

The AI component provides structured decision-support information.

The automation layer remains responsible for:

- Validating the AI response.
- Enforcing permitted values and ranges.
- Verifying score consistency.
- Evaluating confidence thresholds.
- Applying deterministic routing rules.
- Escalating invalid or uncertain results.
- Executing downstream business actions.

An AI recommendation must therefore not directly control a business action without validation.

---

## 3. Required Output Fields

The AI qualification response must contain the following fields:

| Field | Type | Required | Purpose |
| --- | --- | --- | --- |
| qualification_status | String | Yes | Indicates overall qualification outcome |
| priority | String | Yes | Indicates calculated lead priority |
| business_fit_score | Integer | Yes | Business Fit score |
| role_influence_score | Integer | Yes | Role / Decision Influence score |
| need_fit_score | Integer | Yes | Need / Use-Case Fit score |
| buying_intent_score | Integer | Yes | Buying Intent score |
| information_completeness_score | Integer | Yes | Information Completeness score |
| total_score | Integer | Yes | Total qualification score |
| confidence | Number | Yes | Confidence in the assessment |
| reasoning | String | Yes | Concise explanation of the assessment |
| recommended_action | String | Yes | AI recommendation for downstream consideration |

---

## 4. Permitted Values

### qualification_status

Permitted values:

- qualified
- nurture
- insufficient_information

No other value should be accepted by the normal automated routing path.

### priority

Permitted values:

- HIGH
- MEDIUM
- LOW
- REVIEW

### recommended_action

Permitted MVP values:

- priority_sales_follow_up
- standard_sales_follow_up
- nurture
- human_review

Additional actions must not be introduced without updating the agreed contract and corresponding routing logic.

---

## 5. Score Validation Rules

The following ranges apply:

| Field | Minimum | Maximum |
| --- | ---: | ---: |
| business_fit_score | 0 | 25 |
| role_influence_score | 0 | 20 |
| need_fit_score | 0 | 25 |
| buying_intent_score | 0 | 20 |
| information_completeness_score | 0 | 10 |
| total_score | 0 | 100 |
| confidence | 0.00 | 1.00 |

Values outside these ranges must be treated as invalid.

---

## 6. Total Score Validation

The automation must verify that:

**total_score = business_fit_score + role_influence_score + need_fit_score + buying_intent_score + information_completeness_score**

If the reported total does not equal the sum of the component scores, the response must not proceed through normal automated routing.

The case should follow the defined exception or human-review process.

---

## 7. Priority Validation

Where no human-review condition exists, priority must correspond to the approved scoring thresholds:

- **75–100 → HIGH**
- **50–74 → MEDIUM**
- **0–49 → LOW**

If the AI-provided priority conflicts with the validated total score, deterministic workflow logic takes precedence.

The inconsistency should be treated as a validation exception rather than allowing the AI classification to override the approved business rule.

---

## 8. Confidence Validation

Confidence must be represented as a numeric value between:

**0.00 and 1.00**

For the MVP:

**confidence < 0.60 → Human Review**

A lead below the approved confidence threshold must not proceed through the normal automated sales-routing path regardless of its lead score.

---

## 9. Missing Information

Where available lead information is insufficient for reliable qualification:

- qualification_status should be `insufficient_information`
- priority should be `REVIEW`
- recommended_action should be `human_review`

The reasoning should identify the important missing or ambiguous information without inventing unsupported facts.

---

## 10. Reasoning Requirements

The reasoning field must:

- Be concise.
- Refer to relevant available lead evidence.
- Explain the principal factors affecting qualification.
- Identify significant missing information where relevant.
- Avoid unsupported assumptions.
- Avoid unnecessary narrative.

The reasoning is intended to support transparency and human review rather than control routing directly.

---

## 11. Example Valid Output

```json
{
  "qualification_status": "qualified",
  "priority": "HIGH",
  "business_fit_score": 23,
  "role_influence_score": 18,
  "need_fit_score": 24,
  "buying_intent_score": 18,
  "information_completeness_score": 9,
  "total_score": 92,
  "confidence": 0.94,
  "reasoning": "Strong automation need, relevant decision-making role and clear consultation intent.",
  "recommended_action": "priority_sales_follow_up"
}
