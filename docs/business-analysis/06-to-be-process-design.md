# AI Lead Qualification & Sales Routing Agent

## TO-BE Process Design v1.0

**Organisation:** NexaFlow Solutions  
**Project Type:** Portfolio Simulation  
**Document Status:** Draft  
**Version:** 1.0

## 1. Purpose

This document defines the proposed future-state lead qualification and sales routing process for NexaFlow Solutions.

The TO-BE process redesigns the existing manual workflow by introducing structured AI-assisted qualification, deterministic routing rules, automated actions and human oversight for uncertain or exceptional cases.

The objective is not simply to automate the existing process, but to create a more consistent, scalable, transparent and controlled lead-management process.

---

## 2. TO-BE Process Trigger

The future-state process begins when a new lead is created within the defined lead-management system.

For the portfolio implementation, Brevo will represent the lead-management platform.

---

## 3. Future-State Process

### Step 1 — Lead Captured

A prospective customer submits information through a lead-generation channel.

A new contact is created in Brevo.

The creation of the new lead triggers the automated qualification workflow.

### Step 2 — Lead Data Retrieved

The automation retrieves the available information required for qualification.

Relevant information may include:

- Name
- Email
- Company
- Job title
- Lead source
- Enquiry or submitted message
- Other available qualification information

### Step 3 — Lead Data Validated

The workflow checks whether sufficient information exists to support automated qualification.

If critical information is missing or the available data is insufficient, the lead is routed for human review or appropriate exception handling.

### Step 4 — AI-Assisted Qualification

Valid lead information is submitted to the AI qualification component.

The AI evaluates the lead against defined qualification criteria and returns a structured result.

The result may include:

- Qualification status
- Lead priority
- Lead score
- Qualification reasoning
- Recommended action
- Confidence indicator

### Step 5 — AI Output Validated

The automation validates the AI response before any downstream business action occurs.

The workflow checks that required fields exist and that expected values conform to the defined structure.

Invalid or unusable AI outputs are routed to controlled exception handling rather than being trusted automatically.

### Step 6 — Routing Rules Applied

Validated qualification results are evaluated using deterministic business rules.

The automation determines the appropriate processing route based on factors such as:

- Qualification status
- Lead priority
- Lead score
- Confidence
- Completeness of information
- Defined exception conditions

### Step 7 — Appropriate Action Executed

Depending on the routing decision:

**High-Priority Lead**

The lead is routed for timely sales attention and the appropriate sales notification or task is generated.

**Medium-Priority Lead**

The lead is routed to an appropriate follow-up or nurturing process.

**Low-Priority Lead**

The lead is handled according to the defined low-priority business rules.

**Uncertain / Exception Lead**

The lead is routed for human review with sufficient context explaining why automated processing was not completed.

### Step 8 — Qualification Outcome Recorded

Relevant qualification information and routing outcomes are recorded for traceability.

The recorded information may include:

- Qualification result
- Priority
- Score
- AI reasoning
- Confidence
- Routing decision
- Processing status

### Step 9 — Sales or Human Follow-Up

Sales personnel or the designated reviewer receives the lead through the appropriate route and performs the required business action.

---

## 4. TO-BE Process Flow

**Lead Generated**  
↓  
**Contact Created in Brevo**  
↓  
**Automation Triggered**  
↓  
**Retrieve Lead Data**  
↓  
**Validate Lead Data**  
↓  
**Sufficient Information?**

**No → Human Review / Exception Handling**

**Yes ↓**

**AI-Assisted Lead Qualification**  
↓  
**Structured AI Result Returned**  
↓  
**Validate AI Output**  
↓  
**Valid Output?**

**No → Human Review / Exception Handling**

**Yes ↓**

**Apply Deterministic Routing Rules**  
↓  
**High / Medium / Low / Uncertain**  
↓  
**Execute Appropriate Action**  
↓  
**Record Qualification & Routing Outcome**  
↓  
**Sales / Human Follow-Up**

---

## 5. Human-in-the-Loop Control

Human oversight is retained as a deliberate design feature rather than treating every AI output as automatically trustworthy.

Human review may be triggered when:

- Important lead information is missing.
- AI confidence falls below the defined threshold.
- AI output does not match the required structure.
- Qualification results are ambiguous.
- An exception condition occurs.
- The workflow cannot safely determine the appropriate automated action.

This provides a controlled fallback mechanism while allowing routine qualification activities to be automated.

---

## 6. AI and Automation Responsibilities

### AI Responsibilities

The AI component will:

- Interpret relevant lead information.
- Assess the lead against defined qualification criteria.
- Produce structured qualification results.
- Provide concise reasoning.
- Indicate uncertainty where appropriate.

### Automation Responsibilities

The automation layer will:

- Detect new leads.
- Retrieve and map lead information.
- Validate required data.
- Send appropriate information to the AI component.
- Validate the AI response.
- Apply deterministic routing rules.
- Execute approved downstream actions.
- Route exceptions to human review.
- Record relevant processing outcomes.

### Human Responsibilities

Human users will:

- Review uncertain or exceptional leads.
- Act on appropriately routed sales opportunities.
- Investigate workflow exceptions where necessary.
- Provide feedback that may support future process improvement.

---

## 7. Key Process Improvements

Compared with the AS-IS process, the TO-BE process introduces:

| AS-IS | TO-BE |
| --- | --- |
| Manual identification of leads requiring assessment | Automated workflow trigger |
| Repetitive manual lead review | Automated retrieval and structured processing |
| Individual judgement | Standardised AI-assisted qualification criteria |
| Inconsistent prioritisation | Structured scoring and priority classification |
| Manual routing | Deterministic automated routing |
| Limited decision transparency | Qualification reasoning and outcome recording |
| Manual handling of every lead | Human review focused on uncertain or exceptional cases |
| Difficult to scale without additional manual effort | Automation designed to support increased lead volume |

---

## 8. Expected Business Benefits

The redesigned process is expected to:

- Reduce repetitive manual qualification effort.
- Improve consistency of lead assessment.
- Reduce the time required to identify high-priority leads.
- Improve utilisation of sales personnel.
- Provide greater visibility into qualification decisions.
- Support increasing lead volumes.
- Maintain human oversight where automated decisions are uncertain.
- Create a traceable and maintainable qualification process.

These benefits will be evaluated during testing using the simulated project baseline and defined acceptance criteria.

---

## 9. TO-BE Process Outcome

The TO-BE design establishes the future operational process that the AI Lead Qualification & Sales Routing Agent will implement.

The process separates responsibilities between AI interpretation, deterministic automation logic and human judgement.

This design will provide the foundation for the product backlog, user stories, acceptance criteria and technical automation architecture.
