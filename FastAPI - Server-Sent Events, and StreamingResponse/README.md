[🏠 **Main Repository**](../README.md) &nbsp;•&nbsp; [⏮️ **Patterns for Building LLM-based Systems & Products (Eugene Yan)**](../Patterns%20for%20Building%20LLM-based%20Systems%20%26%20Products%20%28Eugene%20Yan%29/README.md) &nbsp;•&nbsp; [**Next module: Instructor - structured outputs library** ⏭️](../Instructor%20-%20structured%20outputs%20library/README.md)

---

# 📡 FastAPI — Server-Sent Events, and StreamingResponse (Week 34)

### *Streaming tokens to the user from the framework you already know (Month 6)*

[![Time](https://img.shields.io/badge/Time_budget-1.5_hrs-blue?style=flat-square)](#-the-study-path)
[![Version](https://img.shields.io/badge/FastAPI-%E2%89%A50.135-009688?style=flat-square)](https://fastapi.tiangolo.com/tutorial/server-sent-events/)

> [!NOTE]
> **Roadmap assignment:** the SSE tutorial and the StreamingResponse section. **Skip:** file and HTML responses.
> **What you produce:** the **streaming endpoint in S8**.
>
> 📄 [Server-Sent Events (SSE)](https://fastapi.tiangolo.com/tutorial/server-sent-events/) · [Custom Response → StreamingResponse](https://fastapi.tiangolo.com/advanced/custom-response/#streamingresponse) · *checked 12 Oct 2026*

> [!IMPORTANT]
> **New since Month 6:** FastAPI now has **built-in SSE support** (`EventSourceResponse` / `ServerSentEvent`), added in **FastAPI 0.135.0**. Older tutorials hand-roll SSE on top of `StreamingResponse`. Upgrade first: `uv add "fastapi>=0.135"`.

---

## 🗺 The study path

| Part | Section | Time | Status |
| :-: | :--- | :-: | :-: |
| 1 | ⭐ The SSE tutorial | 45 min | ☐ |
| 2 | StreamingResponse, and when to use it instead | 15 min | ☐ |
| 3 | Disconnects and per-request cost limits | 30 min | ☐ |
| | **Total** | **1 h 30** | |

---

### Part 1 — ⭐ Server-Sent Events · 45 min
📄 https://fastapi.tiangolo.com/tutorial/server-sent-events/
- [ ] [What are Server-Sent Events?](https://fastapi.tiangolo.com/tutorial/server-sent-events/#what-are-server-sent-events)
- [ ] ⭐ [Stream SSE with FastAPI](https://fastapi.tiangolo.com/tutorial/server-sent-events/#stream-sse-with-fastapi): an `async` generator that `yield`s each token. Note [Non-async path operation functions](https://fastapi.tiangolo.com/tutorial/server-sent-events/#non-async-path-operation-functions): **use async**, because your LLM client is async.
- [ ] [`ServerSentEvent`](https://fastapi.tiangolo.com/tutorial/server-sent-events/#serversentevent): send `event: token`, then `event: done` with the final validated JSON and usage
- [ ] [Raw Data](https://fastapi.tiangolo.com/tutorial/server-sent-events/#raw-data)
- [ ] [SSE with POST](https://fastapi.tiangolo.com/tutorial/server-sent-events/#sse-with-post): your extraction endpoint receives a document, so it is a POST
- [ ] [Resuming with `Last-Event-ID`](https://fastapi.tiangolo.com/tutorial/server-sent-events/#resuming-with-last-event-id) and [Technical Details](https://fastapi.tiangolo.com/tutorial/server-sent-events/#technical-details): skim

### Part 2 — StreamingResponse · 15 min
📄 https://fastapi.tiangolo.com/advanced/custom-response/#streamingresponse
- [ ] `StreamingResponse` with an async generator, and why the page now points most people to [Stream Data](https://fastapi.tiangolo.com/advanced/stream-data/) or SSE instead. Use SSE for tokens to a browser; plain streaming for raw bytes.

**Skip:** HTMLResponse, FileResponse, ORJSON, custom response classes.

### Part 3 — Disconnects and limits · 30 min *(Week 34 "What you learn")*
- [ ] When the client disconnects, your generator is cancelled. Wrap the LLM stream so the **upstream request is closed too** (see [Task cancellation](../Python%20-%20asyncio%20documentation/README.md)). Otherwise you keep paying for tokens nobody reads.
- [ ] Add a **per-request cost limit**: stop the stream and send `event: error` if the running token cost passes the limit
- [ ] Log one structured line per request: request ID, prompt version, model, tokens in/out, cost, latency, TTFT

---

## 🧪 Exercise on your own work (S8)

`POST /extract/stream`: accepts a document, streams progress, ends with an `event: done` whose data is the **validated Pydantic object**. Test it with `httpx` streaming in pytest, including a test that **disconnects mid-stream** and checks the upstream call was cancelled.

## 📦 What this module produces

- [ ] The S8 streaming endpoint, with disconnect handling, a cost limit and structured logs
