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

---

## Language Rule (CRITICAL — Must Follow)

> **The PRD output language MUST match the BRD input language. Always.**

*   If the BRD is written in **Chinese (中文)** → Generate the entire PRD in **Chinese**.
*   If the BRD is written in **English** → Generate the entire PRD in **English**.
*   If the BRD is written in **any other language** (Japanese, French, Arabic, Hindi, etc.) → Generate the entire PRD in **that same language**.
*   If the BRD is **mixed language** (e.g., Chinese body with English field names) → Use the **dominant language** for all prose, and preserve technical terms (field names, API names, system names) in their original language.

**Detection Method:** Identify the language by reading the BRD body text (not headers or labels). The language of the majority of the body content determines the output language.

**This rule overrides all other defaults. No exceptions.**

---

## Workflow
1.  **Read BRD:** Fetch the content of the provided Feishu Doc URL using `feishu-mcp_fetch-doc`.
2.  **Detect Language:** Identify the language of the BRD content (see Language Rule above).
3.  **Structure Content:** Map the raw BRD information into the 6 mandatory PRD sections in the **detected language**.
4.  **Add Meta-Data:** Prepend the "Demand Doc" & "Key Persons" tables and append the "High Risk Element Review" table — all in the detected language.
5.  **Create PRD:** Generate a new Feishu Doc in My Library with the fully structured, language-matched content.
6.  **Return Link:** Provide the Feishu Doc URL to the user.

---

## Golden Template Structure

The output PRD MUST always follow this structure (section names translated to match the BRD language):

```
[Header]
  - BRD Demand Doc (BRD需求文档 / BRD 需求文档)
  - Demand Related Key Persons (需求相关负责人 / Key Persons Table)

[Body]
  01 Background          (背景)
  02 Objectives          (目标)
  03 Features            (功能需求)
  04 User Experience     (用户体验)
  05 Milestones          (里程碑)
  06 Technical Requirements (技术要求)

[Footer]
  - High Risk Element Review (高风险要素审查)
```

### Section Name Translation Reference

| English | Chinese | Notes |
| :--- | :--- | :--- |
| BRD Demand Doc | BRD 需求文档 | Header section |
| Initiated By | 提出人 | From BRD metadata |
| Demand Related Key Persons | 需求相关负责人 | Key persons table |
| Department | 部门 | Table column |
| Related Person | 负责人 | Table column |
| Remark | 备注 | Table column |
| Background | 背景 | Section 01 |
| Context | 背景介绍 | Sub-section |
| Problem Statement | 问题陈述 | Sub-section |
| Market Opportunity | 市场机会 | Sub-section |
| User Personas | 用户画像 | Sub-section |
| Vision Statement | 愿景 | Sub-section |
| Objectives | 目标 | Section 02 |
| SMART Goals | SMART 目标 | Sub-section |
| KPIs | 关键绩效指标 | Sub-section |
| Risk Mitigation | 风险应对 | Sub-section |
| Features | 功能需求 | Section 03 |
| Core Features | 核心功能 | Sub-section |
| User Benefits | 用户价值 | Sub-section |
| Technical Specifications | 技术说明 | Sub-section |
| Feature Prioritization | 功能优先级 | Sub-section |
| User Experience | 用户体验 | Section 04 |
| UI Design | 界面设计 | Sub-section |
| User Journey | 用户旅程 | Sub-section |
| Usability Testing | 可用性测试 | Sub-section |
| Milestones | 里程碑 | Section 05 |
| Development Phases | 开发阶段 | Sub-section |
| Critical Path | 关键路径 | Sub-section |
| Launch Plan | 发布计划 | Sub-section |
| Technical Requirements | 技术要求 | Section 06 |
| Tech Stack | 技术栈 | Sub-section |
| System Architecture | 系统架构 | Sub-section |
| Security Measures | 安全措施 | Sub-section |
| Integration Requirements | 集成需求 | Sub-section |
| High Risk Element Review | 高风险要素审查 | Footer section |
| High Risk Items | 高风险项目 | Table row |
| Does it involve private fields? | 是否涉及隐私字段？ | Table row |

---

## Template Logic (Internal)

```markdown
### PRD | [Project Name]

<callout emoji="📝" background-color="light-blue">
**Version:** 1.0 (Draft) | **Author:** [User Name] | **Date:** [Today] | **Status:** Draft
</callout>

### BRD 需求文档  ← (or "BRD Demand Doc" if English)
*   **提出人 (Initiated By):** [Extracted Name or 'Business Team']
*   **BRD 链接 (BRD Link):** [Original BRD URL]

### 需求相关负责人  ← (or "Demand Related Key Persons" if English)
(Standard Table with placeholders — in detected language)

---

### 01 背景  ← (or "01 Background" if English)
(Content derived from BRD — in detected language)

### 02 目标  ← (or "02 Objectives" if English)
...

... (Sections 03-06 in detected language) ...

---

### 高风险要素审查  ← (or "High Risk Element Review" if English)
(Standard Risk Table — in detected language)
```

---

## Quality Checklist (Before Creating Feishu Doc)

Before calling `feishu-mcp_create-doc`, verify:
- [ ] Language detected correctly from BRD body text.
- [ ] All section headings are in the correct language.
- [ ] All prose, descriptions, and analysis are in the correct language.
- [ ] Technical terms (API names, field names, system names) preserved as-is.
- [ ] No section skipped. Missing info marked as `[TBD]` in the correct language.
- [ ] High Risk Review accurately reflects content (not always "No" — assess the actual BRD).
