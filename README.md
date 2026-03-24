# 🚀 PRD Generator Skill (Universal)

![OpenCode Skill](https://img.shields.io/badge/OpenCode-Supported-blueviolet?style=for-the-badge)
![Cursor Compatible](https://img.shields.io/badge/Cursor-Compatible-black?style=for-the-badge&logo=cursor)
![Windsurf Ready](https://img.shields.io/badge/Windsurf-Ready-blue?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Active-success?style=for-the-badge)

A powerful **AI Skill** that automates the creation of comprehensive **Product Requirement Documents (PRDs)** from **Business Requirement Documents (BRDs)**. 

It strictly enforces a "Golden Template" structure to ensure every PRD is developer-ready, consistent, and professional.

---

## 📖 Compatibility

| Tool | Integration Method | Usage |
| :--- | :--- | :--- |
| **OpenCode** | Native Skill | `/generate-prd <URL>` |
| **Cursor** | `.cursorrules` | "Generate PRD from [File/URL]" |
| **Windsurf** | Generic Prompt | Copy `prompts/generate_prd_prompt.md` |
| **ChatGPT** | System Prompt | Copy `prompts/generate_prd_prompt.md` |

---

## 🛠️ Installation & Usage

### 1️⃣ OpenCode (Native)
Clone this repository into your OpenCode workspace or copy the `.opencode` folder.

```bash
git clone https://github.com/nandanosql/prd_generator_skill.git
```

**Run Command:**
```bash
/generate-prd https://feishu.cn/wiki/wikcnP4Z8X...
```

### 2️⃣ Cursor (IDE)
Just open this project folder in Cursor! The `.cursorrules` file is automatically loaded.

**In Chat:**
> "Generate a PRD for the new User Login feature based on the text below..."

### 3️⃣ Windsurf / Antigravity / OpenClaw
Use the generic prompt file located at `prompts/generate_prd_prompt.md`.

1.  **Copy** the content of `prompts/generate_prd_prompt.md`.
2.  **Paste** it into the AI Chat or System Prompt settings.
3.  **Provide** your BRD content or URL.

---

## 📝 The "Golden Template" Structure

The generated PRD will always follow this mandatory structure:

1.  **Header:** Demand Doc Info & Key Persons Table.
2.  **01 Background:** Context, Problem, Personas.
3.  **02 Objectives:** SMART Goals, KPIs.
4.  **03 Features:** Core Specs, MoSCoW.
5.  **04 UX:** Journey, UI.
6.  **05 Milestones:** Phases, Launch Plan.
7.  **06 Technical:** Stack, Security.
8.  **Footer:** High Risk Element Review Table.

---

## ⚙️ Configuration (OpenCode)

The `opencode.json` file controls the skill's behavior and permissions for OpenCode users.

```json
{
  "agent": {
    "default": {
      "model": "anthropic/claude-3-5-sonnet-20241022",
      "temperature": 0.5
    }
  },
  "permission": {
    "tool": {
      "feishu-mcp_*": "allow"
    }
  }
}
```

---

## 📄 License

MIT License. Created by **Nandan Priyadarshi**.
