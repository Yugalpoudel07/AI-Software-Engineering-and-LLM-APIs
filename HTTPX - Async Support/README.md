[🏠 **Main Repository**](../README.md) &nbsp;•&nbsp; [⏮️ **pytest - How to use fixtures**](../pytest%20-%20How%20to%20use%20fixtures/README.md) &nbsp;•&nbsp; [**Next module: Your LLM provider's API documentation - pick ONE** ⏭️](../Your%20LLM%20provider%27s%20API%20documentation%20-%20pick%20ONE/README.md)

---

# 🌐 HTTPX — Async Support (Week 32)

### *The HTTP library your from-scratch LLM client is built on*

[![Time](https://img.shields.io/badge/Time_budget-1_hr-blue?style=flat-square)](#-the-study-path)
[![Docs](https://img.shields.io/badge/HTTPX-async_docs-555?style=flat-square)](https://www.python-httpx.org/async/)

> [!NOTE]
> **Roadmap assignment:** all of the page, especially **"Streaming responses"**. **Skip** Trio support.
> **What you produce:** streaming in your LLM client.
>
> 📄 https://www.python-httpx.org/async/ · *checked 12 Oct 2026*

---

## 🗺 The study path

| Part | Section | Time | Status |
| :-: | :--- | :-: | :-: |
| 1 | Making async requests; opening and closing clients | 15 min | ☐ |
| 2 | ⭐ Streaming responses | 20 min | ☐ |
| 3 | Timeouts (the companion page) | 10 min | ☐ |
| 4 | Explicit transports → mocking in tests | 15 min | ☐ |
| | **Total** | **1 h** | |

---

### Part 1 · 15 min
- [ ] [Making Async requests](https://www.python-httpx.org/async/#making-async-requests)
- [ ] [Making requests](https://www.python-httpx.org/async/#making-requests) and ⭐ [Opening and closing clients](https://www.python-httpx.org/async/#opening-and-closing-clients): **create one `AsyncClient` and reuse it**. A new client per request throws away connection pooling.

### Part 2 — ⭐ Streaming responses · 20 min
- [ ] [Streaming responses](https://www.python-httpx.org/async/#streaming-responses): `async with client.stream("POST", url, json=...) as r:` then `async for line in r.aiter_lines():`. Server-sent events from an LLM API arrive as `data: {...}` lines, and you parse them one by one.

### Part 3 — Timeouts · 10 min
- [ ] 📄 [Timeouts](https://www.python-httpx.org/advanced/timeouts/): the four timeouts (connect, read, write, pool). For streaming, the **read** timeout applies **between chunks**, not to the whole answer.

### Part 4 — Transports for testing · 15 min
- [ ] [Explicit transport instances](https://www.python-httpx.org/async/#explicit-transport-instances), then 📄 [Mock transports](https://www.python-httpx.org/advanced/transports/#mock-transports): `httpx.MockTransport(handler)` lets your tests return 429/500/bad JSON with no server at all.

**Skip:** [Streaming requests](https://www.python-httpx.org/async/#streaming-requests), [Trio](https://www.python-httpx.org/async/#trio), [AnyIO](https://www.python-httpx.org/async/#anyio), [Calling into Python Web Apps](https://www.python-httpx.org/async/#calling-into-python-web-apps).

---

## 🧪 Exercise on your own work

Stream a real answer from your chosen provider with **only httpx**: parse each `data:` line, print text deltas as they arrive, and record **time to first token** and **total time**. Then put the same parser behind a `MockTransport` and test it with a recorded stream.

## 📦 What this module produces

- [ ] `stream()` in your LLM client, with TTFT logged, tested against a recorded stream
