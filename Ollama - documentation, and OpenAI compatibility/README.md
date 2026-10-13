[🏠 **Main Repository**](../README.md) &nbsp;•&nbsp; [⏮️ **Prompt engineering guide (same provider you chose)**](../Prompt%20engineering%20guide%20%28same%20provider%20you%20chose%29/README.md) &nbsp;•&nbsp; [**Next module: Patterns for Building LLM-based Systems & Products (Eugene Yan)** ⏭️](../Patterns%20for%20Building%20LLM-based%20Systems%20%26%20Products%20%28Eugene%20Yan%29/README.md)

---

# 🦙 Ollama — documentation, and OpenAI compatibility (Week 33)

### *A local open-weights model behind the same interface as your hosted one*

[![Time](https://img.shields.io/badge/Time_budget-2_hrs-blue?style=flat-square)](#-the-study-path)
[![Docs](https://img.shields.io/badge/docs.ollama.com-checked_12_Oct_2026-555?style=flat-square)](https://docs.ollama.com/)

> [!NOTE]
> **Roadmap assignment:** Quickstart, the API introduction, and the OpenAI compatibility page. **Skip:** Modelfile customisation for now.
> **What you produce:** a **local back end** for your client, switched on by **one config value**.
>
> 📄 [Docs home](https://docs.ollama.com/) · [Quickstart](https://docs.ollama.com/quickstart) · [API introduction](https://docs.ollama.com/api/introduction) · [OpenAI compatibility](https://docs.ollama.com/api/openai-compatibility)

> [!TIP]
> **Pick a small model your laptop can run** (a 1–4B instruct model, e.g. a small Qwen, Llama or Gemma). Check its licence on its model page. It is also your safe model for the **Week 32 temperature experiment**, because it accepts `temperature`.

---

## 🗺 The study path

| Part | Page | Time | Status |
| :-: | :--- | :-: | :-: |
| 1 | Quickstart: install, run a model locally | 25 min | ☐ |
| 2 | API introduction and the chat endpoint | 20 min | ☐ |
| 3 | ⭐ OpenAI compatibility | 30 min | ☐ |
| 4 | Capabilities: streaming, structured outputs, tool calling | 25 min | ☐ |
| 5 | Wire it into your client | 20 min | ☐ |
| | **Total** | **2 h** | |

---

### Part 1 — Quickstart · 25 min
📄 https://docs.ollama.com/quickstart
- [ ] *Get started* → ⭐ *Run a model locally*. **Skip** *Connect a desktop app*, *Use a coding agent*, and the cloud API-key steps under *Build an application*.

### Part 2 — API introduction · 20 min
- [ ] 📄 [API introduction](https://docs.ollama.com/api/introduction): base URL `http://localhost:11434`
- [ ] 📄 [Chat endpoint](https://docs.ollama.com/api/chat): the native `/api/chat` request and response

### Part 3 — ⭐ OpenAI compatibility · 30 min
📄 https://docs.ollama.com/api/openai-compatibility
- [ ] [Local server usage](https://docs.ollama.com/api/openai-compatibility#local-server-usage) → [Simple `/v1/chat/completions` example](https://docs.ollama.com/api/openai-compatibility#simple-v1chatcompletions-example)
- [ ] [Endpoints](https://docs.ollama.com/api/openai-compatibility#endpoints) → [`/v1/chat/completions`](https://docs.ollama.com/api/openai-compatibility#v1chatcompletions): note which fields are supported. Streaming, JSON mode, `response_format` and tools are; **logprobs are not**. (`/v1/responses` exists but is **stateless only**.)
- [ ] [Models](https://docs.ollama.com/api/openai-compatibility#models): [Setting the local context size](https://docs.ollama.com/api/openai-compatibility#setting-the-local-context-size). The default context is small, so long documents get **silently truncated** unless you raise it.

### Part 4 — Capabilities · 25 min
- [ ] 📄 [Streaming](https://docs.ollama.com/capabilities/streaming)
- [ ] 📄 [Structured outputs](https://docs.ollama.com/capabilities/structured-outputs): pass a JSON schema (from your Pydantic model)
- [ ] 📄 [Tool calling](https://docs.ollama.com/capabilities/tool-calling)

**Skip:** thinking, embeddings, vision, the FAQ, Modelfiles, the cloud/hosted offering.

### Part 5 — Into your client · 20 min *(Week 33 build task 2)*
- [ ] Add an `ollama` back end to your client's provider interface
- [ ] `config.yaml`: `provider: ollama | openai | anthropic`, so **one value** switches it
- [ ] Run your Week 32 tests against both back ends

---

## 🧪 Exercise on your own work

S8 needs "two prompts × two models (one hosted, one local)". Run your best extraction prompt on the local model and record **F1, cost (≈ $0 plus your electricity) and p95 latency** next to the hosted model. Is the local model good enough for any field?

## 📦 What this module produces

- [ ] A local back end selected by one config value
- [ ] The hosted vs local row pair in your S8 results table
