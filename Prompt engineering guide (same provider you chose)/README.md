[🏠 **Main Repository**](../README.md) &nbsp;•&nbsp; [⏮️ **Your LLM provider's API documentation - pick ONE**](../Your%20LLM%20provider%27s%20API%20documentation%20-%20pick%20ONE/README.md) &nbsp;•&nbsp; [**Next module: Ollama - documentation, and OpenAI compatibility** ⏭️](../Ollama%20-%20documentation%2C%20and%20OpenAI%20compatibility/README.md)

---

# ✍️ Prompt engineering guide — same provider you chose (Week 33)

### *The provider's own guide, read next to AI Engineering Chapter 5, then tested on data*

[![Time](https://img.shields.io/badge/Time_budget-3_hrs-blue?style=flat-square)](#-the-study-path)
[![OpenAI](https://img.shields.io/badge/Track_A-OpenAI-412991?style=flat-square)](https://developers.openai.com/api/docs/guides/prompt-engineering)
[![Claude](https://img.shields.io/badge/Track_B-Claude-D97757?style=flat-square)](https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/overview)

> [!NOTE]
> **Roadmap assignment:** the overview and the best-practices pages. **Skip:** model-specific marketing pages. Read it **alongside** AI Engineering Chapter 5 ([module](../AI%20Engineering%20%28Chip%20Huyen%2C%20O%27Reilly%2C%202024%29/README.md)), not instead of it.
> **What you produce:** your **versioned prompt files**, and the measured **prompt A versus B comparison** (Week 33 build task 3).
>
> *Checked 12 Oct 2026. The OpenAI guide moved to `developers.openai.com`.*

> [!TIP]
> **A prompt is code.** "This prompt seems better" is a rumour. "B passes 78% ± 4% vs A's 71% ± 4% on 100 examples" is a result.

---

## 🗺 The study path

| Part | Topic | Time | Status |
| :-: | :--- | :-: | :-: |
| 1 | Overview: when (and when not) to prompt-engineer | 20 min | ☐ |
| 2 | ⭐ Core techniques: clarity, context, examples, structure | 1 h | ☐ |
| 3 | Output format and model-specific notes | 30 min | ☐ |
| 4 | ⭐ Prompt A vs B on 100 documents, with a bootstrap CI | 1 h 10 | ☐ |
| | **Total** | **3 h** | |

---

## 🅰️ Track A — OpenAI
📄 https://developers.openai.com/api/docs/guides/prompt-engineering

- [ ] **Part 1 (20 min):** *Choosing a model*, *Prompt engineering*, *Message roles and instruction following* (the `developer` role outranks `user`)
- [ ] **Part 2 (1 h):** ⭐ *Version prompts in code* · *Message formatting with Markdown and XML* · ⭐ *Few-shot learning* · *Include relevant context information*
- [ ] **Part 3 (30 min):** *Prompting current models* → *Prompting best practices for the latest model* · *Prompting reasoning models* (high-level goals work better than step lists)

## 🅱️ Track B — Anthropic (Claude)
📄 [Overview](https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/overview) · [Prompting best practices](https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-prompting-best-practices)

- [ ] **Part 1 (20 min):** Overview: *Before prompt engineering* (it sends you to [define success criteria and build evaluations](https://platform.claude.com/docs/en/test-and-evaluate/develop-tests) first, the same order as this plan), *When to prompt engineer*, *How to prompt engineer*
- [ ] **Part 2 (1 h):** Best practices → [General principles](https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-prompting-best-practices#general-principles): ⭐ [Be clear and direct](https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-prompting-best-practices#be-clear-and-direct), [Add context to improve performance](https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-prompting-best-practices#add-context-to-improve-performance), ⭐ [Use examples effectively](https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-prompting-best-practices#use-examples-effectively), [Structure prompts with XML tags](https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-prompting-best-practices#structure-prompts-with-xml-tags), [Give Claude a role](https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-prompting-best-practices#give-claude-a-role), [Long context prompting](https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-prompting-best-practices#long-context-prompting)
- [ ] **Part 3 (30 min):** [Control the format of responses](https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-prompting-best-practices#control-the-format-of-responses), ⭐ [Migrating away from prefilled responses](https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-prompting-best-practices#migrating-away-from-prefilled-responses) (prefill is gone on new models; this is what replaces it), [Tool usage](https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-prompting-best-practices#tool-usage)

**Skip (Track B):** the *Agentic systems* group (Month 9), *Capability-specific tips*, *Migration considerations*, the frontend-design and LaTeX sections. **Optional extra:** the free [interactive prompt-engineering tutorial](https://github.com/anthropics/prompt-eng-interactive-tutorial) if a technique doesn't click. Keep it under 30 minutes.

---

## 🧪 Part 4 — Prompt A vs B, measured · 1 h 10 *(Week 33 build task 3)*

- [ ] Store prompts as files: `prompts/extract_v1.md`, `prompts/extract_v2.md`. Log the **prompt version** with every call.
- [ ] Run both on the same **100 labelled S8 documents**
- [ ] Score each document (field-level F1), then **bootstrap the paired difference** (resample documents, compute `mean(B) − mean(A)`, 10,000 times; reuse your Month 1 Week 4 bootstrap)
- [ ] Decide: does the 95% interval exclude 0?

| Prompt | Mean F1 | 95% CI | Δ vs v1 (95% CI) | Cost / 100 docs |
| :--- | :-: | :-: | :-: | :-: |
| `extract_v1` | | | — | |
| `extract_v2` | | | | |

## 📦 What this module produces

- [ ] Versioned prompt files, with the version logged in every call
- [ ] The A vs B table with a confidence interval on the difference, and a one-line decision
