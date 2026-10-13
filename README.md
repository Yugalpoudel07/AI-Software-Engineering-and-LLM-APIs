# 🧰 AI Software Engineering and LLM APIs

Production Python (async, strict typing, testing) and LLM APIs done properly. Includes an LLM client built from scratch with retries, rate limiting, streaming and cost tracking, plus **S8: a structured-extraction service with a measured evaluation.**

[![Study guides](https://img.shields.io/badge/Study_guides-15%20of%2015-brightgreen?style=flat-square)](#-learning-roadmap--curriculum-status)
[![From-scratch #10](https://img.shields.io/badge/From--scratch_%2310-not_started-lightgrey?style=flat-square)](#week-32--talking-to-llms-properly---from-scratch-10)
[![S8](https://img.shields.io/badge/Ship_S8-not_started-lightgrey?style=flat-square)](#-ship-s8--a-structured-extraction-service-week-34)
[![Gate 8](https://img.shields.io/badge/Gate_8-not_attempted-lightgrey?style=flat-square)](#-gate-8--closed-book-75-minutes)
[![Focus](https://img.shields.io/badge/Focus-async%20%C2%B7%20types%20%C2%B7%20tests%20%C2%B7%20LLM%20APIs-purple?style=flat-square)](#)

**Month 8 of 15 · Weeks 31–35 · 150 hours** · the first month of the **AI engineering** phase. Per week: Theory 4.5 h · Implementation 10 h · Project 10 h · DSA 3 h · Review + keeping current 2.5 h.

---

## 🎯 The Goal, in Simple Words

**AI engineering is mostly software engineering.** The model is one function call; everything around it (handling failures, waiting on many requests at once, validating output, counting cost) is where real systems succeed or fail.

This month I get my Python to production standard, then learn to talk to LLMs the way professionals do: **streaming, structured output, tool calls, retries, caching, and knowing exactly what every request costs.**

In plain words: most "AI apps" that break in production break in **boring** ways: a timeout nobody handled, a rate limit that took the service down, JSON that didn't parse, a bill nobody expected. This month removes all four.

> [!IMPORTANT]
> **Framework-free on purpose.** No LangChain, no provider SDK inside `src/`, no Instructor in from-scratch #10. LangGraph arrives in Month 9, **after** I've built the thing it replaces.

---

## 🔄 The Month at a Glance

```text
  WEEK 31                 WEEK 32  ■ #10               WEEK 33                  WEEK 34  ■ S8 · GATE 8      WEEK 35
  ┌────────────────┐     ┌──────────────────────┐     ┌────────────────────┐   ┌──────────────────────┐   ┌──────────┐
  │ PYTHON THAT    │ ──► │ TALKING TO LLMs      │ ──► │ PROMPTS, TOOLS,    │ ─►│ SHIPPING AN LLM      │ ─►│  BUFFER  │
  │ SURVIVES PROD  │     │ PROPERLY             │     │ CONTEXT, OPEN      │   │ SERVICE              │   │          │
  │ async, mypy,   │     │ tokens, sampling,    │     │ MODELS             │   │ async FastAPI, SSE,  │   │          │
  │ pytest, uv, CI │     │ streaming, retries,  │     │ tool calling,      │   │ cache, cost limit,   │   │          │
  │                │     │ rate limit, cost     │     │ caching, Ollama,   │   │ field-level F1       │   │          │
  │                │     │ → my LLM client      │     │ prompt A vs B + CI │   │                      │   │          │
  └────────────────┘     └──────────────────────┘     └────────────────────┘   └──────────────────────┘   └──────────┘
   Real Python asyncio    Provider API docs            Prompt guide              FastAPI SSE
   asyncio docs · mypy    HTTPX · tiktoken             Ollama · AI Eng Ch 5      Eugene Yan patterns
   pytest · applied-llms  AI Eng Ch 2 · Instructor*    (* = optional)            NeetCode: every week →
```

---

## 🗺 Learning Roadmap & Curriculum Status

Every module folder has a **study guide** (`README.md`): the exact sections to read with deep links, time per step adding up to the card's budget, what to skip, an exercise on my own data or projects, and what the module produces.

| Week | Module | Tag | Primary Source | Core Focus | Budget | Status |
| :-: | :--- | :-: | :--- | :--- | :-: | :-: |
| 31–33 | **[AI Engineering (Chip Huyen)](AI%20Engineering%20%28Chip%20Huyen%2C%20O%27Reilly%2C%202024%29/README.md)** | MUST | O'Reilly 2024 (+ free route) | Ch 1, Ch 2 (sampling), Ch 5 (prompting) | 7 h | 📋 Study guide ready |
| 31 | **[What We've Learned From A Year of Building with LLMs](What%20We%27ve%20Learned%20From%20A%20Year%20of%20Building%20with%20LLMs/README.md)** | MUST | applied-llms.org | Tactical in full, Operational skimmed → 10 practices | 2 h | 📋 Study guide ready |
| 31 | **[Real Python — asyncio walkthrough](Real%20Python%20-%20Python%27s%20asyncio%20A%20Hands-On%20Walkthrough/README.md)** | MUST | Real Python | Event loop, `gather`, queues → timing table | 3 h | 📋 Study guide ready |
| 31–34 | **[Python — asyncio documentation](Python%20-%20asyncio%20documentation/README.md)** | REFERENCE | Python 3.15 docs | `gather`, `Semaphore`, `timeout`, cancellation | — | 📋 Study guide ready |
| 31 | **[mypy — Type hints cheat sheet](mypy%20-%20Type%20hints%20cheat%20sheet/README.md)** | MUST | mypy 2.4 | `mypy --strict` passing in CI | 1.5 h | 📋 Study guide ready |
| 31 | **[pytest — How to use fixtures](pytest%20-%20How%20to%20use%20fixtures/README.md)** | MUST | pytest docs | Fixtures, monkeypatch, parametrize, no real network | 2 h | 📋 Study guide ready |
| 32 | **[HTTPX — Async Support](HTTPX%20-%20Async%20Support/README.md)** | MUST | HTTPX docs | Async client, **streaming**, timeouts, mock transport | 1 h | 📋 Study guide ready |
| 32–33 | **[Your LLM provider's API documentation — pick ONE](Your%20LLM%20provider%27s%20API%20documentation%20-%20pick%20ONE/README.md)** | MUST | OpenAI **or** Claude docs | Raw HTTP: streaming, structured output, tools, errors, caching | 8 h | 📋 Study guide ready |
| 33 | **[Prompt engineering guide (same provider)](Prompt%20engineering%20guide%20%28same%20provider%20you%20chose%29/README.md)** | MUST | OpenAI **or** Claude docs | Techniques → prompt A vs B with a bootstrap CI | 3 h | 📋 Study guide ready |
| 33 | **[Ollama — documentation, and OpenAI compatibility](Ollama%20-%20documentation%2C%20and%20OpenAI%20compatibility/README.md)** | MUST | docs.ollama.com | Local model behind the same interface | 2 h | 📋 Study guide ready |
| 31–34 | **[Patterns for Building LLM-based Systems (Eugene Yan)](Patterns%20for%20Building%20LLM-based%20Systems%20%26%20Products%20%28Eugene%20Yan%29/README.md)** | MUST | eugeneyan.com (2023) | 7 patterns → which month covers each | 2 h | 📋 Study guide ready |
| 34 | **[FastAPI — Server-Sent Events, and StreamingResponse](FastAPI%20-%20Server-Sent%20Events%2C%20and%20StreamingResponse/README.md)** | MUST | FastAPI ≥ 0.135 | S8 streaming endpoint, disconnects, cost limit | 1.5 h | 📋 Study guide ready |
| 32 | **[Instructor — structured outputs library](Instructor%20-%20structured%20outputs%20library/README.md)** | OPTIONAL | useinstructor.com | Compare its retries to mine (after #10 works) | 1 h | 📋 Study guide ready |
| 32 | **[tiktoken](tiktoken/README.md)** | REFERENCE | openai/tiktoken | Estimated vs billed tokens | — | 📋 Study guide ready |
| 31→ | **[NeetCode — roadmap and practice lists](NeetCode%20-%20roadmap%20and%20practice%20lists/README.md)** | MUST (habit) | neetcode.io | 3 problems/week, ~100 by Week 65 | 3 h/wk | 📋 Study guide ready |

**Resources ≈ 34 h across five weeks** (MUST cards add up to 33 h, plus 1 h optional; matches the roadmap header). The DSA habit is scheduled separately (3 h/week).

> [!NOTE]
> **Changes found on 12 Oct 2026:**
> - **OpenAI's docs moved** to `developers.openai.com/api/docs` and **Anthropic's** to `platform.claude.com/docs`.
> - **The newest Claude models reject `temperature`/`top_p`/`top_k` (400 error)**, and prefill is gone from Claude 4.6. OpenAI reasoning models don't take sampling settings either. **The Week 32 temperature experiment runs on the local Ollama model** (or another model that accepts `temperature`).
> - **FastAPI ≥ 0.135 has built-in SSE** (`EventSourceResponse`/`ServerSentEvent`), so there's no need to hand-roll it.
> - The Python docs are now **3.15**, mypy docs **2.4**.
> - **AI Engineering is a paid book:** each chapter is mapped to the author's free chapter summaries and blog posts.
> - **NeetCode's lists render with JavaScript only**, so open them in a browser.
> - **Folder name:** *Real Python — Python's asyncio**:** A Hands-On Walkthrough* drops its colon (Windows can't use `:` in folder names).

---

## 🛠 What This Repo Will Build — week by week

### Week 31 — Python that survives production

*Learn:* **type hints and `mypy --strict`** · dataclasses vs Pydantic · **`async`/`await`**, the event loop, `gather`, semaphores, timeouts, cancellation · `httpx` · **real testing** (fixtures, parametrize, monkeypatch, faking network calls) · `uv` + `ruff` + `mypy` + `pytest`.

- [ ] **A typed, tested Python package:** `uv` project, `ruff`, `mypy --strict` passing, pytest with coverage, GitHub Actions CI (reuse Month 7 Week 29)
- [ ] **An async fetcher:** 200 calls to a fake slow server, sequential vs `gather` + `Semaphore(10)`, both times recorded
- [ ] **Break it on purpose:** one `time.sleep()` inside an async function, then watch everything freeze. Add it to `failure-log.md`.
- [ ] Tests that fake the network: **no test in this repo may call a real API**
- [ ] **Start the DSA habit:** arrays and hashing, then two pointers, 3 problems this week

| Run | Requests | Concurrency | Wall time |
| :--- | :-: | :-: | :-: |
| Sequential | 200 | 1 | |
| `gather` + semaphore | 200 | 10 | |

### Week 32 — Talking to LLMs properly · ■ FROM-SCRATCH #10

*Learn:* tokens and billing · **sampling as mathematics** (temperature divides the logits before the softmax from Week 11; top-p) · request/response shape, stop reasons · **streaming** · **structured outputs, and why you still validate** · **429 / 5xx / timeouts, exponential backoff with jitter**, what to retry and what never to retry · **cost accounting**.

- [ ] **Paper first:** temperature-scaled softmax for a 5-token example; what happens as T → 0 and T → ∞
- [ ] **From-scratch #10 — my own LLM client** using only `httpx`, against ONE provider's raw HTTP API:
  - [ ] async, with streaming
  - [ ] retries with exponential backoff and jitter, only on retryable errors
  - [ ] a **token-bucket rate limiter**
  - [ ] a timeout on every call
  - [ ] a cost tracker that logs tokens and dollars per call
  - [ ] structured output validated with Pydantic, with **one** automatic repair attempt
- [ ] **Tests for every failure path** (fake server: 429, 500, timeout, malformed JSON)
- [ ] **Checked against the official SDK:** same prompt, same parameters, same result shape
- [ ] **Measure temperature:** same prompt 30× at T = 0, 0.7 and 1.2; count distinct answers; plot it *(on a model that accepts `temperature`; see the note above)*

### Week 33 — Prompts, tools, context, and open models

*Learn:* **prompting as engineering** (versioned files, examples, decomposition, output format) · **tool calling** round trip · **prompt caching** · **the context window as a budget** · **open-weights models locally** with Ollama · **provider-agnostic design**.

- [ ] **Tool calling** added to my client: a calculator and a "look up a row in my P1 data" tool, full round trip, tested
- [ ] **An Ollama back end** behind the same interface; one config value switches hosted ↔ local
- [ ] **Prompt A vs B, measured:** 100 labelled examples, **bootstrap CI on the difference** (Month 1 Week 4 bootstrap)
- [ ] Prompt caching measured: same long prefix, 20 calls, cost and latency with and without caching
- [ ] All prompts stored as versioned files, with the version recorded in every logged call

| Prompt | Mean F1 | 95% CI | Δ vs v1 (95% CI) |
| :--- | :-: | :-: | :-: |
| `extract_v1` | | | — |
| `extract_v2` | | | |

### Week 34 — Shipping an LLM service · ■ SHIP S8 · ■ GATE 8

*Learn:* an async FastAPI endpoint that calls an LLM without blocking · **streaming to the user with Server-Sent Events** · timeouts, cancellation on disconnect, a per-request cost limit · caching identical requests · **structured logging** (request ID, prompt version, model, tokens, cost, latency) · **field-level precision, recall, F1** (the Week 12 metrics applied to structured output).

- [ ] Ship S8 (below)
- [ ] Gate 8 (below)

### Week 35 — BUFFER WEEK

Finishing S8 · repeating Week 32 if the from-scratch client is shaky · retaking Gate 8 · or rest. **Do not pre-spend it.**

---

## 📦 Ship S8 — a structured-extraction service (Week 34)

**Turn messy documents into clean, validated data, and prove how accurate it is.** Documents I understand: job adverts, receipts, news articles or government notices, in English or Nepali.

- [ ] A **Pydantic schema** for what I extract
- [ ] **An evaluation set first: 100 documents I labelled myself**, before any prompt tuning
- [ ] **Field-level precision, recall and F1**, implemented from scratch
- [ ] **Two prompts × two models** (one hosted, one local), with confidence intervals
- [ ] **Cost per 1,000 documents** and **p95 latency** for each configuration
- [ ] A FastAPI service with **streaming, logging and a cost limit**, containerised
- [ ] **Error analysis:** which fields fail, and why
- [ ] README to the Month 7 standard, with a **limitations** section

| Configuration | Field F1 (95% CI) | Cost / 1,000 docs | p95 latency |
| :--- | :-: | :-: | :-: |
| Prompt v1 × hosted model | | | |
| Prompt v2 × hosted model | | | |
| Prompt v1 × local model | | | |
| Prompt v2 × local model | | | |

---

## 🚧 Gate 8 — closed book, 75 minutes

- [ ] 1. Write temperature-scaled softmax and explain what temperature 0 does mathematically.
- [ ] 2. Write exponential backoff with jitter and a token-bucket rate limiter in an empty editor, **25 minutes**.
- [ ] 3. Explain what happens when blocking code runs inside an async endpoint, and how you would find it.
- [ ] 4. Explain why structured outputs still need validation, and what you do when validation fails.
- [ ] 5. Given token prices and a described workload, estimate the monthly cost. Show your working.

**Pass = 4 out of 5.** Score: `__ / 5` · Date: `____`

---

## ✅ End of Month 8 — I must have

- [ ] A typed, tested package with CI green and `mypy --strict` passing
- [ ] **From-scratch #10: my own LLM client**, with a test for every failure path
- [ ] The temperature experiment plotted
- [ ] Tool calling and a local Ollama back end behind one interface
- [ ] Prompt A versus B with a bootstrap confidence interval on the difference
- [ ] **S8 shipped:** extraction service, 100-document evaluation set, two prompts × two models, cost and p95 reported
- [ ] **Gate 8 passed**
- [ ] ~12 DSA problems logged
- [ ] 35 lab-notebook entries

> [!WARNING]
> **The trap this month:** reaching for a framework because it is faster. It is faster today and slower forever, because you never learn what it does. **Month 8 is framework-free on purpose.**

---

*Part of my 15-month Data Science → AI Engineering plan. Previous month: [LLM-Applications-and-Production-Practice](https://github.com/Yugalpoudel07/LLM-Applications-and-Production-Practice) · Next month: [LLM-Agents-Tools-and-MCP](https://github.com/Yugalpoudel07/LLM-Agents-Tools-and-MCP).*
