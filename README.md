# Toner

Toner is an agent skill and prompt guardrail framework designed to enforce clean, direct, and unslop AI writing and communication.

## Core Principles

- **Direct Answers**: Provide conclusions and solutions immediately without opening disclaimers or repetitive greetings.
- **High Information Density**: Strip boilerplate filler, redundant transitions, and empty summaries.
- **Editing Fidelity**: When polishing or revising existing text, preserve facts, certainty levels, causal links, and untouched fluent passages.
- **Prohibited Syntax & Rhetoric**:
  - Contrastive negation templates (such as "不是……而是……" or mechanical "not X, but Y").
  - Unsubstantiated numeric compound coinages ("双重……", "四视角", "二步骤") unless established as standard domain terminology.
  - Cross-disciplinary metaphorical migration (such as misusing "耦合", "正交", "鲁棒", "熵增" in non-STEM contexts).
  - Literary clichés and philosophical buzzwords ("迷思", "祛魅", "图景", "底色").
- **Mode Switching**:
  - **Mode A (Direct Reply)**: Fast, conclusion-first technical problem solving with structured points when needed.
  - **Mode B (Formal & Academic Writing)**: Cohesive, paragraph-driven narrative argumentation with strict citation fidelity and evidence bounds.

## Project Structure

```
.
├── SKILL.md       # Skill definition and runtime execution rules
└── README.md      # Documentation and overview
```

## Usage

### As an Agent Skill
Place this folder or `SKILL.md` into your agent skills path:
- Antigravity / Claude Code: `~/.agents/skills/toner/SKILL.md`

### As System Prompt Rules
Include the guardrails from `SKILL.md` into `CLAUDE.md`, `AGENTS.md`, or your environment's system instructions.
