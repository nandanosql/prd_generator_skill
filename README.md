# PRD Generator Skill (OpenCode)

A custom skill for **OpenCode** that automates the creation of comprehensive Product Requirement Documents (PRDs) from Business Requirement Documents (BRDs), strictly following your organization's "Golden Template".

## 🚀 Features

*   **Automated Structuring:** Maps raw BRD content into a standardized 6-section PRD.
*   **Golden Template Compliance:** Enforces the mandatory structure:
    1.  Background (Problem, Context, Personas)
    2.  Objectives (SMART Goals, KPIs)
    3.  Features (Core, Tech Specs, MoSCoW)
    4.  User Experience (UI, Journey)
    5.  Milestones (Phases, Launch Plan)
    6.  Technical Requirements (Stack, Security)
*   **Header/Footer Compliance:** Adds required metadata tables ("Demand Doc", "Key Persons", "High Risk Review").
*   **Rich Formatting:** Generates Feishu Docs with callouts, tables, and grids.

## 📦 Installation

Simply clone this repository into your OpenCode workspace or copy the `.opencode` folder:

```bash
git clone https://github.com/your-org/prd-generator-skill.git
```

## 🛠️ Usage

Once installed, use the slash command in your OpenCode chat:

```bash
/generate-prd <BRD_Feishu_URL>
```

**Example:**
```bash
/generate-prd https://mi.feishu.cn/wiki/KrXcwsU7aivtOpkiTjPc6mvNnXd
```

## 📂 Project Structure

```
.
├── .opencode/
│   ├── skills/
│   │   └── prd-generator/
│   │       └── SKILL.md       # The core logic & template
│   └── commands/
│       └── generate-prd.md    # The slash command trigger
├── opencode.json              # Configuration file
└── README.md                  # This file
```

## 📝 Template Structure

The generated PRD will always follow this structure:

1.  **BRD Demand Doc** (Header)
2.  **Demand Related Key Persons** (Header Table)
3.  **01 Background**
4.  **02 Objectives**
5.  **03 Features**
6.  **04 User Experience**
7.  **05 Milestones**
8.  **06 Technical Requirements**
9.  **High Risk Element Review** (Footer Table)

## 📄 License

MIT License.
