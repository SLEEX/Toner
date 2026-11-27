# Toner

[English](README.md) | [中文](README_zh.md) | [Design Rationale / 设计思路](DESIGN.md)

Toner is an agent skill and prompt engineering specification that eliminates AI writing mannerisms, enforces high information density, and ensures strict factual fidelity across conversational replies and formal technical manuscripts.

---

## Why Toner?

Modern large language models exhibit predictable structural mannerisms when generating text:
- Hedging with excessive disclaimers ("It is important to remember...", "Results may vary...").
- Defaulting to contrastive negation formulas ("It is not X, but rather Y").
- Inventing artificial numeric labels ("two-step framework", "four-perspective view", "dual-mechanism") to simulate academic rigor.
- Borrowing engineering or physical terminology metaphorically ("decouple", "orthogonal", "robust", "closed-loop") in general or social science discourse.
- Diluting narrative momentum with commentary clichés ("myth", "demystify", "landscape").

Toner replaces these rhetorical habits with direct conclusions, unslop syntax, disciplined domain vocabulary, and strict preservation of evidence boundaries.

---

## Core Guardrails

### 1. Communication & Information Density
- **Direct Answer**: State the primary judgment, code, or answer in the first sentence.
- **Zero Decorative Preamble**: Remove greeting formulas, disclaimers, and empty rhetorical questions.
- **Decisive Tone**: State clear conclusions when evidence supports them; mark uncertainty boundaries explicitly where genuine gaps exist.

### 2. Strict Fidelity in Editing
- **Preserve Ground Truth**: Keep original facts, names, numbers, dates, scope, and direction of causality intact.
- **Respect Fluent Text**: Only edit sentences that have clear expression errors; do not rewrite clear, existing prose to show effort.
- **Preserve Formatting**: Keep code blocks, URLs, markdown anchors, and YAML front matter unaltered.
- **Direct Deliverable**: Return the finished text directly without process drafts or grading checklists.

### 3. Syntax & Lexicon Red Lines
- **No Contrastive Negations**: Prohibit "不是……而是……" and mechanical "not X, but Y" templates. State positive facts and direct logic directly.
- **No Coined Numeric Compounds**: Prohibit inventing terms such as "双重……", "二步骤", or "四视角" unless established as standard domain terminology (e.g., Difference-in-Differences, Multi-task learning).
- **No Cross-Discipline Jargon Migration**: Restrict physical, mathematical, and computer science terms to their native fields. Use plain, accurate verbs and nouns in general and interdisciplinary writing.
- **No Literary or Commentary Clichés**: Ban words like "迷思", "祛魅", "图景", "底色", and corporate buzzwords like "赋能", "抓手", "闭环".

### 4. Dual Operational Modes
- **Mode A (Direct Reply)**: Conclusion-first replies for Q&A, troubleshooting, and code discussion. Compact bullet points and tables are permitted.
- **Mode B (Formal & Academic Writing)**: Continuous, paragraph-driven narrative for papers, proposals, and reports. Avoid replacing narrative argumentation with bulleted fragments. Citations strictly follow consecutive sequential numbers (`[1]`, `[2]`, `[3]`).

---

## Repository Structure

```
.
├── SKILL.md          # Skill definition and executable agent rules
├── README.md         # English documentation
├── README_zh.md      # Chinese documentation
├── DESIGN.md         # Design rationale (English)
├── DESIGN_zh.md      # Design rationale (Chinese)
└── .gitignore        # Git ignore rules
```

---

## Installation & Setup

### 1. Agent Skill (Antigravity / Claude Code)
Clone or copy this repository into your local skills directory:

```bash
git clone https://github.com/SLEEX/Toner.git ~/.agents/skills/toner
```

Or copy [SKILL.md](SKILL.md) directly:

```bash
mkdir -p ~/.agents/skills/toner
cp SKILL.md ~/.agents/skills/toner/SKILL.md
```

### 2. System Prompt Integration
To enforce Toner across any LLM workspace (Cursor, OpenCode, Codex, ChatGPT, API system prompts), copy the rules from [SKILL.md](SKILL.md) directly into your project's instruction file:
- `CLAUDE.md`
- `AGENTS.md`
- `.cursorrules`

---

## Detailed Documentation

- Read the full [Design Rationale (English)](DESIGN.md) for the linguistic and cognitive considerations behind each rule.
- 阅读 [设计思路文档（中文）](DESIGN_zh.md) 了解规则背后的具体裁量与反套路考量。
