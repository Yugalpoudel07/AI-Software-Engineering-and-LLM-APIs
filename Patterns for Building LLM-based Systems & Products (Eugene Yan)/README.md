[🏠 **Main Repository**](../README.md) &nbsp;•&nbsp; [⏮️ **Ollama - documentation, and OpenAI compatibility**](../Ollama%20-%20documentation%2C%20and%20OpenAI%20compatibility/README.md) &nbsp;•&nbsp; [**Next module: FastAPI - Server-Sent Events, and StreamingResponse** ⏭️](../FastAPI%20-%20Server-Sent%20Events%2C%20and%20StreamingResponse/README.md)

---

# 🧩 Patterns for Building LLM-based Systems & Products — Eugene Yan (Weeks 31–34)

### *Seven patterns in one essay, which together make a map of Months 8–13*

[![Time](https://img.shields.io/badge/Time_budget-2_hrs-blue?style=flat-square)](#-the-study-path)
[![Source](https://img.shields.io/badge/eugeneyan.com-July_2023-555?style=flat-square)](https://eugeneyan.com/writing/llm-patterns/)

> [!NOTE]
> **Roadmap assignment:** all seven patterns. **Skip:** the extended reference list.
> **What you produce:** for each pattern, **one line on which month of this plan covers it**.
>
> 📄 https://eugeneyan.com/writing/llm-patterns/ · *checked 12 Oct 2026*

> [!TIP]
> Written in 2023, so some tool names are dated (and the evals part predates LLM-as-judge best practice). **The patterns themselves have held up.** Read for the ideas, not the libraries.

---

## 🗺 The study path

| Part | Pattern | Covered in | Time | Status |
| :-: | :--- | :-: | :-: | :-: |
| 1 | ⭐ [Evals: To measure performance](https://eugeneyan.com/writing/llm-patterns/#evals-to-measure-performance) | Month 10 | 25 min | ☐ |
| 2 | [Retrieval-Augmented Generation: To add knowledge](https://eugeneyan.com/writing/llm-patterns/#retrieval-augmented-generation-to-add-knowledge) | Month 7, 13 | 15 min | ☐ |
| 3 | [Fine-tuning: To get better at specific tasks](https://eugeneyan.com/writing/llm-patterns/#fine-tuning-to-get-better-at-specific-tasks) | Month 11 | 15 min | ☐ |
| 4 | ⭐ [Caching: To reduce latency and cost](https://eugeneyan.com/writing/llm-patterns/#caching-to-reduce-latency-and-cost) | Month 8 (W34), 12 | 15 min | ☐ |
| 5 | ⭐ [Guardrails: To ensure output quality](https://eugeneyan.com/writing/llm-patterns/#guardrails-to-ensure-output-quality) | Month 8 (validation), 10 | 20 min | ☐ |
| 6 | [Defensive UX: To anticipate & handle errors gracefully](https://eugeneyan.com/writing/llm-patterns/#defensive-ux-to-anticipate--handle-errors-gracefully) | Month 8 (W34) | 10 min | ☐ |
| 7 | [Collect user feedback: To build our data flywheel](https://eugeneyan.com/writing/llm-patterns/#collect-user-feedback-to-build-our-data-flywheel) | Month 10 (W42) | 10 min | ☐ |
| 8 | Your pattern map | | 10 min | ☐ |
| | **Total** | | **2 h** | |

For each pattern, read its three parts in order: *Why …?*, *More about …*, *How to apply …*.

**Skip:** the *Other patterns common in machine learning* section on first read, and the [References](https://eugeneyan.com/writing/llm-patterns/#references) list.

---

### Part 8 — Your pattern map · 10 min
- [ ] Write `notes/llm-patterns-map.md`: seven lines, each one *pattern → month → the concrete thing you'll build* (e.g. *Caching → Week 34 → exact-request cache in S8; Month 12 → prefix caching in vLLM*).

## 🧪 Exercise on your own work

Before Week 34, decide **which three patterns S8 uses** and why: probably guardrails (Pydantic validation and one repair attempt), caching (identical requests) and defensive UX (a clear error when extraction fails, never invented fields). Put the three in the S8 README's design section.

## 📦 What this module produces

- [ ] `notes/llm-patterns-map.md`
- [ ] A "patterns used" paragraph in the S8 README
