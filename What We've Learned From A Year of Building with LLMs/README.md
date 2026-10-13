[🏠 **Main Repository**](../README.md) &nbsp;•&nbsp; [⏮️ **AI Engineering (Chip Huyen, O'Reilly, 2024)**](../AI%20Engineering%20%28Chip%20Huyen%2C%20O%27Reilly%2C%202024%29/README.md) &nbsp;•&nbsp; [**Next module: Real Python - Python's asyncio A Hands-On Walkthrough** ⏭️](../Real%20Python%20-%20Python%27s%20asyncio%20A%20Hands-On%20Walkthrough/README.md)

---

# 🧭 What We've Learned From A Year of Building with LLMs (Week 31)

### *Six practitioners on what actually works in production: the Tactical section in full, the Operational section skimmed*

[![Time](https://img.shields.io/badge/Time_budget-2_hrs-blue?style=flat-square)](#-the-study-path)
[![Source](https://img.shields.io/badge/applied--llms.org-June_2024-555?style=flat-square)](https://applied-llms.org/)

> [!NOTE]
> **Roadmap assignment:** the **Tactical** section fully, the **Operational** section skimmed. **Skip** the Strategy section until Month 13.
> **What you produce:** a checklist of **ten practices** you will apply to S8.
>
> 📄 https://applied-llms.org/ · by Eugene Yan, Bryan Bischof, Charles Frye, Hamel Husain, Jason Liu and Shreya Shankar · *checked 12 Oct 2026*

> [!TIP]
> Several of these authors return later in the plan: Eugene Yan (this month and Month 10), Hamel Husain (Month 10). Reading this first means their longer posts will feel familiar.

---

## 🗺 The study path

| Part | Section | Time | Status |
| :-: | :--- | :-: | :-: |
| 1 | 1.1 Prompting | 20 min | ☐ |
| 2 | 1.2 Information Retrieval / RAG (a Month 7 refresher) | 15 min | ☐ |
| 3 | 1.3 Tuning and optimizing workflows | 20 min | ☐ |
| 4 | ⭐ 1.4 Evaluation & Monitoring | 30 min | ☐ |
| 5 | Operational: 2.1 Data, 2.2 Working with models (skim) | 20 min | ☐ |
| 6 | Your ten-practice checklist | 15 min | ☐ |
| | **Total** | **2 h** | |

---

### Part 1 — 1.1 Prompting · 20 min
- [ ] [Focus on getting the most out of fundamental prompting techniques](https://applied-llms.org/#focus-on-getting-the-most-out-of-fundamental-prompting-techniques)
- [ ] ⭐ [Structure your inputs and outputs](https://applied-llms.org/#structure-your-inputs-and-outputs): directly relevant to S8's schema
- [ ] [Have small prompts that do one thing, and only one thing, well](https://applied-llms.org/#have-small-prompts-that-do-one-thing-and-only-one-thing-well)
- [ ] [Craft your context tokens](https://applied-llms.org/#craft-your-context-tokens)

### Part 2 — 1.2 Information Retrieval / RAG · 15 min *(you built this in Month 7; read fast)*
- [ ] [RAG is only as good as the retrieved documents' relevance, density, and detail](https://applied-llms.org/#rag-is-only-as-good-as-the-retrieved-documents-relevance-density-and-detail)
- [ ] [Don't forget keyword search; use it as a baseline and in hybrid search](https://applied-llms.org/#dont-forget-keyword-search-use-it-as-a-baseline-and-in-hybrid-search)
- [ ] [Prefer RAG over finetuning for new knowledge](https://applied-llms.org/#prefer-rag-over-finetuning-for-new-knowledge) and [Long-context models won't make RAG obsolete](https://applied-llms.org/#long-context-models-wont-make-rag-obsolete)

### Part 3 — 1.3 Tuning and optimizing workflows · 20 min
- [ ] [Step-by-step, multi-turn "flows" can give large boosts](https://applied-llms.org/#step-by-step-multi-turn-flows-can-give-large-boosts)
- [ ] ⭐ [Prioritize deterministic workflows for now](https://applied-llms.org/#prioritize-deterministic-workflows-for-now): the same advice as Month 9's "workflow before agent"
- [ ] [Getting more diverse outputs beyond temperature](https://applied-llms.org/#getting-more-diverse-outputs-beyond-temperature)
- [ ] ⭐ [Caching is underrated](https://applied-llms.org/#caching-is-underrated): Week 34's exact-request cache
- [ ] [When to finetune](https://applied-llms.org/#when-to-finetune): keep for Month 11

### Part 4 — ⭐ 1.4 Evaluation & Monitoring · 30 min *(the most important part for this plan)*
- [ ] [Create a few assertion-based unit tests from real input/output samples](https://applied-llms.org/#create-a-few-assertion-based-unit-tests-from-real-inputoutput-samples)
- [ ] [LLM-as-Judge can work (somewhat), but it's not a silver bullet](https://applied-llms.org/#llm-as-judge-can-work-somewhat-but-its-not-a-silver-bullet)
- [ ] [The "intern test" for evaluating generations](https://applied-llms.org/#the-intern-test-for-evaluating-generations)
- [ ] [Overemphasizing certain evals can hurt overall performance](https://applied-llms.org/#overemphasizing-certain-evals-can-hurt-overall-performance)
- [ ] [Simplify annotation to binary tasks or pairwise comparisons](https://applied-llms.org/#simplify-annotation-to-binary-tasks-or-pairwise-comparisons)
- [ ] [(Reference-free) evals and guardrails can be used interchangeably](https://applied-llms.org/#reference-free-evals-and-guardrails-can-be-used-interchangeably)
- [ ] [LLMs will return output even when they shouldn't](https://applied-llms.org/#llms-will-return-output-even-when-they-shouldnt) and [Hallucinations are a stubborn problem](https://applied-llms.org/#hallucinations-are-a-stubborn-problem)

### Part 5 — Operational, skimmed · 20 min
- [ ] [Check for development-prod skew](https://applied-llms.org/#check-for-development-prod-skew) and ⭐ [Look at samples of LLM inputs and outputs every day](https://applied-llms.org/#look-at-samples-of-llm-inputs-and-outputs-every-day)
- [ ] ⭐ [Generate structured output to ease downstream integration](https://applied-llms.org/#generate-structured-output-to-ease-downstream-integration)
- [ ] [Migrating prompts across models is a pain in the ass](https://applied-llms.org/#migrating-prompts-across-models-is-a-pain-in-the-ass), [Version and pin your models](https://applied-llms.org/#version-and-pin-your-models), [Choose the smallest model that gets the job done](https://applied-llms.org/#choose-the-smallest-model-that-gets-the-job-done)

**Skip:** [2.3 Product](https://applied-llms.org/#product) and [2.4 Team & Roles](https://applied-llms.org/#team-roles) for now, and the whole Strategy part (Month 13).

### Part 6 — The checklist · 15 min
- [ ] Write `notes/applied-llms-checklist.md`: **ten practices**, one line each, each tagged with the S8 file or step where you will apply it (e.g. *"pin the model version → `config.yaml`"*).

---

## 🧪 Exercise on your own work

Take two practices from your list, **"structure your outputs"** and **"assertion-based unit tests from real samples"**. In S8, write three pytest assertions from real documents (e.g. *date field is ISO format*, *amount is positive*, *missing fields are `null` not invented*) before you tune any prompt.

## 📦 What this module produces

- [ ] `notes/applied-llms-checklist.md`: ten practices mapped to S8
- [ ] Three assertion-based tests in the S8 repo
