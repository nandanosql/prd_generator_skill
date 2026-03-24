---
name: prd-generator
description: Generate a comprehensive PRD from a BRD document URL following the Golden Template.
compatibility: opencode
metadata:
  input: Feishu Doc URL (BRD)
  output: Feishu Doc (PRD)
  template: Golden Template (6 Sections + Header/Footer)
---

## What I do
I transform a Business Requirement Document (BRD) into a fully structured Product Requirement Document (PRD) following your organization's "Golden Template".

### Workflow
1.  **Read BRD:** I fetch the content of the provided Feishu Doc URL.
2.  **Structure Content:** I map the raw BRD information into the 6 mandatory PRD sections:
    *   **01 Background** (Context, Problem, Market, Personas, Vision)
    *   **02 Objectives** (SMART Goals, KPIs, Risks)
    *   **03 Features** (Core, Benefits, Tech Specs, Prioritization)
    *   **04 User Experience** (UI, Journey, Usability)
    *   **05 Milestones** (Phases, Critical Path, Launch)
    *   **06 Technical Requirements** (Stack, Architecture, Security)
3.  **Add Meta-Data:** I prepend the "Demand Doc" & "Key Persons" tables and append the "High Risk Element Review" table.
4.  **Create PRD:** I generate a new Feishu Doc with the structured content.

## When to use me
Use this skill when you have a finalized BRD and need to create the initial draft of the PRD for developer handover.

## How to use me
Run the command: `/generate-prd <BRD_URL>`

## Template Logic (Internal)
The output PRD will always follow this structure:

```markdown
### PRD | [Project Name]

<callout emoji="📝" background-color="light-blue">
**Version:** 1.0 (Draft) | **Author:** [User Name] | **Date:** [Today] | **Status:** Draft
</callout>

### BRD Demand Doc
*   **Initiated By:** [Extracted Name or 'Business Team']
*   **BRD Link:** [Original BRD URL]

### Demand Related Key Persons
(Standard Table with placeholders)

---

### 01 Background
(Content derived from BRD Problem Statement & Context)

### 02 Objectives
(Content derived from BRD Goals & Success Metrics)

... (Sections 03-06) ...

---

### High Risk Element Review
(Standard Risk Table)
```
