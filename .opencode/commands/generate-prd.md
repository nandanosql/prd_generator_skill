---
description: Generate a PRD from a BRD Feishu Doc URL.
agent: quick
model: anthropic/claude-3-5-sonnet-20241022
skill: prd-generator
---

Generate a comprehensive **Product Requirement Document (PRD)** based on the Business Requirement Document (BRD) found at this URL: `$ARGUMENTS`.

Please:
1.  **Fetch the content** of the BRD using the `feishu-mcp_fetch-doc` tool.
2.  **Analyze the BRD** to extract key information (Problem, Goals, Features, Constraints).
3.  **Use the `prd-generator` skill logic** to structure this information into the Golden Template (6 Sections + Header/Footer).
4.  **Create a new Feishu Doc** named `PRD | [Project Name]` with the fully formatted content.
5.  **Return the link** to the new PRD.

If any critical information (like "Initiated By" or specific technical constraints) is missing from the BRD, make reasonable assumptions or mark them as `[TBD]` in the PRD draft.
