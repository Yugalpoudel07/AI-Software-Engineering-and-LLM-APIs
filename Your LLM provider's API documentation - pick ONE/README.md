[🏠 **Main Repository**](../README.md) &nbsp;•&nbsp; [⏮️ **HTTPX - Async Support**](../HTTPX%20-%20Async%20Support/README.md) &nbsp;•&nbsp; [**Next module: Prompt engineering guide (same provider you chose)** ⏭️](../Prompt%20engineering%20guide%20%28same%20provider%20you%20chose%29/README.md)

---

# 🔌 Your LLM provider's API documentation — pick ONE (Weeks 32–33)

### *Learn one provider deeply. Two tracks below: OpenAI or Anthropic (Claude). Do one, not both.*

[![Time](https://img.shields.io/badge/Time_budget-8_hrs-blue?style=flat-square)](#-the-study-path)
[![OpenAI](https://img.shields.io/badge/Track_A-OpenAI-412991?style=flat-square)](https://developers.openai.com/api/docs)
[![Claude](https://img.shields.io/badge/Track_B-Claude-D97757?style=flat-square)](https://platform.claude.com/docs/en/intro)

> [!NOTE]
> **Roadmap assignment:** text generation / messages · streaming · structured outputs · tool (function) calling · prompt caching · rate limits and error codes · token counting. **Skip:** images, audio, batch APIs, fine-tuning APIs, admin APIs.
> **What you produce:** your **from-scratch LLM client (from-scratch #10)**, built against the **raw HTTP API** these pages describe. Read the SDK examples, then do the same calls with `httpx`.

> [!IMPORTANT]
> **Both doc sites moved in 2026 (checked 12 Oct 2026):** OpenAI `platform.openai.com/docs` → **`developers.openai.com/api/docs`**; Anthropic `docs.claude.com` → **`platform.claude.com/docs`**. Old links redirect, but use the new ones.

> [!WARNING]
> **The Week 32 temperature experiment needs a model that accepts `temperature`.** On the newest Claude models (4.7 and later), `temperature`, `top_p` and `top_k` return a **400 error**, and **prefill** is not supported from Claude 4.6. OpenAI's reasoning models also ignore or reject sampling settings. Run the temperature experiment on a model that allows it: your **local Ollama model** works (see the [Ollama module](../Ollama%20-%20documentation%2C%20and%20OpenAI%20compatibility/README.md)), or an older or non-reasoning hosted model. Write down which model you used.

---

## 🗺 The study path

| Part | Topic | Week | Time | Status |
| :-: | :--- | :-: | :-: | :-: |
| 1 | The raw request: auth, messages, response shape | 32 | 1 h 15 | ☐ |
| 2 | ⭐ Streaming | 32 | 1 h | ☐ |
| 3 | ⭐ Errors and rate limits (retries, backoff, `retry-after`) | 32 | 1 h 15 | ☐ |
| 4 | Token counting and cost | 32 | 45 min | ☐ |
| 5 | ⭐ Structured outputs | 32 | 1 h 15 | ☐ |
| 6 | ⭐ Tool (function) calling | 33 | 1 h 30 | ☐ |
| 7 | Prompt caching | 33 | 1 h | ☐ |
| | **Total** | | **8 h** | |

---

## 🅰️ Track A — OpenAI

| Part | Read | Focus |
| :-: | :--- | :--- |
| 1 | [API Overview](https://developers.openai.com/api/reference/overview/) (auth: `Authorization: Bearer …`) → [Text generation](https://developers.openai.com/api/docs/guides/text): [Choosing models and APIs](https://developers.openai.com/api/docs/guides/text#choosing-models-and-apis), [Message roles and instruction following](https://developers.openai.com/api/docs/guides/text#message-roles-and-instruction-following) → [Responses: create (reference)](https://developers.openai.com/api/reference/resources/responses/methods/create) → [Conversation state](https://developers.openai.com/api/docs/guides/conversation-state) | Responses API vs Chat Completions: pick **one**. Ollama speaks Chat Completions, so that makes the local back end easier. |
| 2 | [Streaming API responses](https://developers.openai.com/api/docs/guides/streaming-responses): *Enable streaming*, *Read the responses* | The event types you must parse with `aiter_lines()` |
| 3 | [Error codes](https://developers.openai.com/api/docs/guides/error-codes) → [Rate limits](https://developers.openai.com/api/docs/guides/rate-limits): *How do these rate limits work?*, *Rate limits in headers*, *Error mitigation → Retrying with exponential backoff* | Which codes to retry (429, 5xx) and which never (400, 401, 403, 404) |
| 4 | [Counting tokens](https://developers.openai.com/api/docs/guides/token-counting) + the `usage` field in every response, plus the [tiktoken module](../tiktoken/README.md) | Cost = input × input price + output × output price |
| 5 | [Structured model outputs](https://developers.openai.com/api/docs/guides/structured-outputs): *Getting a structured response*, *Structured Outputs vs JSON mode*, *When to use … via function calling vs via response_format* | Strict JSON schema; **refusals** are a separate field |
| 6 | [Function calling](https://developers.openai.com/api/docs/guides/function-calling): *How it works*, *Function tool example*, *Defining functions*, *Handling function calls* | The full round trip: call → run → send result back |
| 7 | [Prompt caching](https://developers.openai.com/api/docs/guides/prompt-caching): *How caching works*, *Cache lifetime*, *How to optimize prompt caching* | Automatic; long, unchanged prefix **first** (min. 1,024 tokens on current models) |

## 🅱️ Track B — Anthropic (Claude)

| Part | Read | Focus |
| :-: | :--- | :--- |
| 1 | [Intro to Claude](https://platform.claude.com/docs/en/intro) → [Using the Messages API](https://platform.claude.com/docs/en/build-with-claude/working-with-messages): *Basic request and response*, *Multiple conversational turns* → [Messages API reference](https://platform.claude.com/docs/en/api/messages) | Stateless: resend the whole history. Headers `x-api-key` and `anthropic-version`; check the current version string on the API pages. |
| 2 | [Streaming messages](https://platform.claude.com/docs/en/build-with-claude/streaming): [Event types](https://platform.claude.com/docs/en/build-with-claude/streaming#event-types), [Content block delta types](https://platform.claude.com/docs/en/build-with-claude/streaming#content-block-delta-types), ⭐ [Basic streaming request](https://platform.claude.com/docs/en/build-with-claude/streaming#basic-streaming-request) (the raw HTTP stream), [Error recovery](https://platform.claude.com/docs/en/build-with-claude/streaming#error-recovery) | `message_start` → `content_block_delta`… → `message_delta` (usage) → `message_stop`; `ping` anywhere; errors can arrive **inside** the stream |
| 3 | [Errors](https://platform.claude.com/docs/en/api/errors): *HTTP errors*, *Error shapes*, *Request ID* → [Rate limits](https://platform.claude.com/docs/en/api/rate-limits): *Rate limits*, ⭐ *Response headers* | Retry 429 (honour `retry-after`), 500, 529 overloaded. **A spend-cap 429 has no `retry-after`, so don't retry it.** Never retry 400/401/403/404/413. |
| 4 | [Token counting](https://platform.claude.com/docs/en/build-with-claude/token-counting) + `usage` in every response | Count before sending; check cost after |
| 5 | [Structured outputs](https://platform.claude.com/docs/en/build-with-claude/structured-outputs): *How it works*, *Using a raw JSON schema*, *Data extraction*, *JSON Schema limitations*, ⭐ *Invalid outputs* (refusal, `max_tokens`) | Even with structured outputs, `max_tokens` can cut the JSON short. Validate. |
| 6 | [Tool use overview](https://platform.claude.com/docs/en/agents-and-tools/tool-use/overview) → [How tool use works](https://platform.claude.com/docs/en/agents-and-tools/tool-use/how-tool-use-works): [The tool-use contract](https://platform.claude.com/docs/en/agents-and-tools/tool-use/how-tool-use-works#the-tool-use-contract), ⭐ [The agentic loop (client tools)](https://platform.claude.com/docs/en/agents-and-tools/tool-use/how-tool-use-works#the-agentic-loop-client-tools), [When to use tools](https://platform.claude.com/docs/en/agents-and-tools/tool-use/how-tool-use-works#when-to-use-tools-and-when-not-to) | Loop on `stop_reason == "tool_use"`. This *is* Month 9's from-scratch #11, in miniature. |
| 7 | [Prompt caching](https://platform.claude.com/docs/en/build-with-claude/prompt-caching): *How prompt caching works*, *Pricing*, *Automatic caching*, *Explicit cache breakpoints*, *Best practices*, *Troubleshooting* | Cache reads are billed far below normal input; writes cost a little more |

**Skip (both tracks):** vision, audio, files, batch, fine-tuning, admin and agent-platform products, server-side tools (web search etc.).

---

## 🧪 Exercise on your own work — from-scratch #10 (Week 32)

Build the client against the **raw HTTP API** with `httpx` only (no provider SDK in `src/`):

- [ ] `async def complete(messages, *, schema=None, tools=None) -> Result` and `async def stream(...) -> AsyncIterator[str]`
- [ ] Retries with exponential backoff **and jitter**, only on retryable codes; honour `retry-after`
- [ ] A token-bucket rate limiter shared across concurrent calls
- [ ] A timeout on every call
- [ ] A cost tracker: model, input tokens, output tokens, $ per call, written to a JSONL log
- [ ] Structured output parsed with Pydantic, with **one** automatic repair attempt on validation failure
- [ ] **Check it against the official SDK:** same prompt and parameters, same result shape

## 📦 What this module produces

- [ ] From-scratch #10: your LLM client, with a test for every failure path ([pytest module](../pytest%20-%20How%20to%20use%20fixtures/README.md))
- [ ] Tool calling added in Week 33 (a calculator and a "look up a row in my P1 data" tool)
- [ ] A prompt-caching measurement: 20 calls with a long shared prefix, cost and latency with and without caching
