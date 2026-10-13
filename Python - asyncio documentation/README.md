[🏠 **Main Repository**](../README.md) &nbsp;•&nbsp; [⏮️ **Real Python - Python's asyncio A Hands-On Walkthrough**](../Real%20Python%20-%20Python%27s%20asyncio%20A%20Hands-On%20Walkthrough/README.md) &nbsp;•&nbsp; [**Next module: mypy - Type hints cheat sheet** ⏭️](../mypy%20-%20Type%20hints%20cheat%20sheet/README.md)

---

# 📚 Python — asyncio documentation (Weeks 31–34, reference)

### *The four functions you'll actually look up: `gather`, `Semaphore`, `timeout`, cancellation*

[![Type](https://img.shields.io/badge/Reference-look_up,_don't_read-lightgrey?style=flat-square)](#)
[![Version](https://img.shields.io/badge/docs-Python_3.15-3776AB?style=flat-square)](https://docs.python.org/3/library/asyncio.html)

> [!NOTE]
> **Roadmap assignment:** look up `asyncio.gather`, `asyncio.Semaphore`, `asyncio.timeout` and task cancellation **as you need them**. **Skip** reading it front to back. **Time budget:** none of its own; lookups happen inside your build hours.
>
> 📄 https://docs.python.org/3/library/asyncio.html · *checked 12 Oct 2026; the live docs are now Python 3.15. Everything below works from Python 3.11.*

---

## 🔎 The lookup table

| When you are building… | Look up | Link |
| :--- | :--- | :--- |
| Week 31 fetcher: run 200 calls at once | `asyncio.gather` | [Running tasks concurrently](https://docs.python.org/3/library/asyncio-task.html#running-tasks-concurrently) · [`asyncio.gather`](https://docs.python.org/3/library/asyncio-task.html#asyncio.gather) |
| Week 31: but only 10 at a time | `asyncio.Semaphore` | [Semaphore](https://docs.python.org/3/library/asyncio-sync.html#semaphore) |
| Week 32 client: a timeout on every call | `asyncio.timeout` | [Timeouts](https://docs.python.org/3/library/asyncio-task.html#timeouts) · [`asyncio.timeout`](https://docs.python.org/3/library/asyncio-task.html#asyncio.timeout) |
| Week 34: user closes the browser mid-stream | cancellation | [Task cancellation](https://docs.python.org/3/library/asyncio-task.html#task-cancellation) |
| A safer `gather` (one failure cancels the rest) | `TaskGroup` | [Task groups](https://docs.python.org/3/library/asyncio-task.html#task-groups) |
| You *must* call a blocking library | `asyncio.to_thread` | [Running in threads](https://docs.python.org/3/library/asyncio-task.html#running-in-threads) |
| A shared token-bucket rate limiter | `asyncio.Lock` | [Lock](https://docs.python.org/3/library/asyncio-sync.html#lock) |

## ✅ Read once (20 min, inside Week 31)

- [ ] [Coroutines](https://docs.python.org/3/library/asyncio-task.html#coroutines) and [Awaitables](https://docs.python.org/3/library/asyncio-task.html#awaitables)
- [ ] [Creating tasks](https://docs.python.org/3/library/asyncio-task.html#creating-tasks): **keep a reference to tasks you create**, or they can be garbage-collected mid-run
- [ ] The note at the top of [Synchronization Primitives](https://docs.python.org/3/library/asyncio-sync.html#synchronization-primitives): these primitives take **no timeout argument**; wrap them in `asyncio.timeout()` instead

**Skip:** eager task factory, scheduling from other threads, introspection, the low-level event-loop and transport pages.

## 🧪 Exercise on your own work

In your Week 32 LLM client, use **`asyncio.timeout`** (not a hand-written timer) for every call, and a **`TaskGroup`** in the test that fires 50 requests at the fake server. Write one test that cancels a streaming request halfway and checks the client closes the connection cleanly.

## 📦 What this module produces

- [ ] Timeouts, a semaphore and cancellation handled correctly in your LLM client, each with a test
