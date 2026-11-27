# Toner Design Rationale

[English](DESIGN.md) | [中文](DESIGN_zh.md) | [Back to README](README.md)

This document outlines the linguistic, cognitive, and structural rationale behind Toner, explaining why specific rules were chosen and how they constrain large language model outputs.

---

## 1. The Core Problem: AI Writing Mannerisms

Standard LLMs trained with reinforcement learning from human feedback (RLHF) tend to develop recurring stylistic artifacts:

1. **Defensive Hedging**: Habitual inclusion of disclaimers ("It is crucial to remember", "While there are many perspectives") to avoid risk.
2. **Symmetrical Pseudo-Dialectics**: Overusing contrastive negation formulas ("It is not merely A, but fundamentally B") to manufacture depth without presenting substantive evidence.
3. **Manufactured Conceptualization**: Inventing numeric compound labels ("two-step mechanism", "four-perspective framework", "dual-track paradigm") to sound scholarly.
4. **Disciplinary Jargon Migration**: Borrowing terms from physics, math, and software engineering ("decouple", "orthogonal", "robust", "entropy", "closed-loop") as generic rhetorical metaphors in non-technical writing.
5. **Humanities and Commentary Clichés**: Peppered references to "myths", "demystification", "landscapes", "undercurrents", and "gaze".

These patterns reduce information density and signal machine-generated text. Toner was designed to dismantle these tendencies through explicit, enforceable constraints.

---

## 2. Rationale Behind Key Rules

### 2.1 The Ban on Contrastive Negation ("不是……而是……")

#### The Problem
The construction "不是……而是……" (and its variants like "并不在于 A，而在于 B", or "not X, but Y") is one of the most frequent patterns in LLM-generated prose. Models rely on it because:
- It consumes token budget smoothly while stalling for the actual point.
- It mimics philosophical contrast and rhetorical punch without requiring empirical data.
- It frequently sets up a strawman (X) that nobody actually claimed, just to validate Y.

#### The Solution
Toner strictly prohibits this pattern. Writers and models must state the direct positive thesis, the exact mechanism, or the empirical evidence immediately.
- **Before**: 该系统的优势不在于运行速度，而在于提供了良好的容错能力。
- **After**: 该系统的核心优势为容错能力较强，能够在节点失效时维持服务。

---

### 2.2 The Ban on Coined Numeric Labels ("双重……" / "四视角" / "二步骤")

#### The Problem
AI writing frequently compresses everyday parallel lists into coined academic-sounding phrases:
- Calling an experiment with two steps a "二步骤流程" or "双阶段设计".
- Calling two checks a "双重校验机制".
- Calling an analysis from four angles a "四视角分析框架".

Unless these are established, formalized concepts with recognized domain literature (such as Difference-in-Differences / 双重差分法, or Multi-task learning / 多任务学习), self-coining numeric compounds produces artificial pseudo-academic jargon.

#### The Solution
Toner restricts numeric compounds strictly to recognized domain terminology. All ordinary workflows and analyses must be written in natural, descriptive language:
- **Before**: 本文构建了包含四视角、二步骤的评估机制。
- **After**: 本文从模型准确率、响应延迟、资源消耗和安全边界四个指标出发，分两步测试系统性能。

---

### 2.3 Boundary Enforcement on Cross-Disciplinary Jargon

#### The Problem
Modern technical and management writing often borrows hard-science vocabulary as loose metaphors:
- "解耦" used for simply measuring two variables separately.
- "正交" used for two distinct or independent topics.
- "鲁棒性" used for organizational adaptability or general software stability.
- "底层逻辑" used for simple causes or basic principles.
- "闭环" used for finishing a standard procedure.

This degrades clarity and strips technical terms of their mathematical or engineering precision.

#### The Solution
Toner establishes disciplinary boundaries:
- Physics, control theory, and electronics terms ("耦合", "共振", "阻尼", "跃迁") remain restricted to physical and engineering domains.
- Mathematics and statistics terms ("正交", "收敛", "拐点", "方差") remain restricted to strict calculations.
- General discussions must use plain, accurate verbs and nouns ("独立测试", "稳健", "转折点", "前后一致").

---

### 2.4 Editing Fidelity: The Non-Destructive Invariant

#### The Problem
When tasked with "polishing" or "refining" text, LLMs routinely:
1. Elevate certainty levels (turning "may lead to" into "leads to").
2. Transform correlations into explicit causal relationships.
3. Rewrite sentences that were already clear, introducing unnecessary synonyms just to show output volume.
4. Hallucinate sources or statistics to fill presumed gaps.

#### The Solution
Toner enforces strict fidelity constraints during text revision:
- Original facts, numbers, dates, names, scopes, and degrees of certainty must remain intact.
- Fluent sentences must be left untouched.
- The deliverable must be the final text directly, with zero review chatter or meta-commentary.

---

### 2.5 Dual-Mode Architecture

Communication needs differ across contexts:

```
┌─────────────────────────────────────────────────────────────┐
│                          Toner                              │
├──────────────────────────────┬──────────────────────────────┤
│      Mode A: Direct Reply    │ Mode B: Formal & Academic    │
├──────────────────────────────┼──────────────────────────────┤
│ • Conclusion in first line   │ • Continuous paragraphs      │
│ • Compact bullet points      │ • No fragmented lists        │
│ • Immediate code fixes       │ • Strict citation integrity  │
│ • High-velocity troubleshooting│ • Evidence-bounded claims  │
└──────────────────────────────┴──────────────────────────────┘
```

- **Mode A** prioritizes speed, actionability, and high-density technical feedback.
- **Mode B** enforces cohesive academic prose, eliminating bulleted fragments and ensuring citation continuity (`[1]`, `[2]`, `[3]`).

---

## 3. The Silent Self-Audit Loop

To ensure rules are not merely read but executed, Toner specifies an automated self-audit pass before the final output is emitted:
1. Check first sentence: Did a greeting, disclaimer, or background preamble sneak in? Delete it.
2. Check negations: Is there any "不是……而是……"? Rewrite directly.
3. Check labels: Are there unearned numeric coinages? Unpack them into plain language.
4. Check terminology: Are cross-disciplinary metaphors present? Replace them with native vocabulary.
5. Check editing bounds: Did certainty levels drift? Revert to the original evidence scope.
