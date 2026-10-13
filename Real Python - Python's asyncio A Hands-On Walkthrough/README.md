[🏠 **Main Repository**](../README.md) &nbsp;•&nbsp; [⏮️ **What We've Learned From A Year of Building with LLMs**](../What%20We%27ve%20Learned%20From%20A%20Year%20of%20Building%20with%20LLMs/README.md) &nbsp;•&nbsp; [**Next module: Python - asyncio documentation** ⏭️](../Python%20-%20asyncio%20documentation/README.md)

---

# ⚡ Real Python — Python's asyncio: A Hands-On Walkthrough (Week 31)

### *The event loop, coroutines, `gather`, and the patterns you'll use for every LLM call*

[![Time](https://img.shields.io/badge/Time_budget-3_hrs-blue?style=flat-square)](#-the-study-path)
[![Source](https://img.shields.io/badge/Real_Python-free_tutorial-1f6fb2?style=flat-square)](https://realpython.com/async-io-python/)

> [!NOTE]
> **Roadmap assignment:** "A First Look at Async I/O", "Async I/O in Python With asyncio", and "Common Async I/O Programming Patterns". **Skip** the historical sections.
> **What you produce:** your **sequential versus concurrent timing comparison** (Week 31 build task 2).
>
> 📄 https://realpython.com/async-io-python/ · *checked 12 Oct 2026*

> [!NOTE]
> **Folder name:** the card's title has a colon (*Python's asyncio**:** A Hands-On Walkthrough*). Windows doesn't allow `:` in folder names, so it was dropped.

> [!TIP]
> The page estimates 39 minutes of reading. The rest of the 3 hours is **typing and running every example** yourself, then the timing exercise.

---

## 🗺 The study path

| Part | Section | Time | Status |
| :-: | :--- | :-: | :-: |
| 1 | A First Look at Async I/O | 20 min | ☐ |
| 2 | ⭐ Async I/O in Python With asyncio | 50 min | ☐ |
| 3 | ⭐ Common Async I/O Programming Patterns | 45 min | ☐ |
| 4 | Other features: async `with`, async iterators, exceptions | 25 min | ☐ |
| 5 | The timing exercise | 40 min | ☐ |
| | **Total** | **3 h** | |

---

### Part 1 — A First Look at Async I/O · 20 min
- [ ] [Async I/O Explained](https://realpython.com/async-io-python/#async-io-explained): concurrency is not parallelism. One thread, many waits.
- [ ] [Async I/O Isn't Simple](https://realpython.com/async-io-python/#async-io-isnt-simple)

### Part 2 — ⭐ Async I/O in Python With asyncio · 50 min
- [ ] [Coroutines and Coroutine Functions](https://realpython.com/async-io-python/#coroutines-and-coroutine-functions)
- [ ] [The `async` and `await` Keywords](https://realpython.com/async-io-python/#the-async-and-await-keywords): an `async def` function does nothing until awaited
- [ ] ⭐ [The Async I/O Event Loop](https://realpython.com/async-io-python/#the-async-io-event-loop): **why one blocking call (e.g. `time.sleep`) freezes every other request**
- [ ] [The `asyncio` REPL](https://realpython.com/async-io-python/#the-asyncio-repl): `python -m asyncio`, handy for experiments

### Part 3 — ⭐ Common Async I/O Programming Patterns · 45 min
- [ ] [Coroutine Chaining](https://realpython.com/async-io-python/#coroutine-chaining): call → parse → validate, one after another, many documents at once
- [ ] ⭐ [Coroutine and Queue Integration](https://realpython.com/async-io-python/#coroutine-and-queue-integration): producer/consumer with `asyncio.Queue`. Your Month 10 evaluation runner will use this shape.

### Part 4 — Other features · 25 min
- [ ] [Async `with` Statements](https://realpython.com/async-io-python/#async-with-statements): `async with httpx.AsyncClient() as client:`
- [ ] [Async Iterators, Loops, and Comprehensions](https://realpython.com/async-io-python/#async-iterators-loops-and-comprehensions): `async for chunk in stream:` is how token streaming looks
- [ ] [Async Exception Handling](https://realpython.com/async-io-python/#async-exception-handling): what `gather` does when one task fails
- [ ] [When to Use Async I/O](https://realpython.com/async-io-python/#when-to-use-async-io)

**Skip:** [Other `asyncio` Tools](https://realpython.com/async-io-python/#other-asyncio-tools) on first read (you'll meet `Semaphore` and `timeout` in the [asyncio docs](../Python%20-%20asyncio%20documentation/README.md)), [Libraries Supporting Async I/O](https://realpython.com/async-io-python/#libraries-supporting-async-io) and the FAQ.

### Part 5 — The timing exercise · 40 min *(Week 31 build task 2)*
- [ ] Write a tiny FastAPI server with one endpoint that does `await asyncio.sleep(1)` (your fake slow LLM)
- [ ] Call it **200 times sequentially** with `httpx` → record the time
- [ ] Call it 200 times with `asyncio.gather` and `asyncio.Semaphore(10)` → record the time
- [ ] **Break it on purpose:** replace `await asyncio.sleep(1)` with `time.sleep(1)` in the server and run the concurrent version again. Write what you saw in `failure-log.md`.

| Run | Requests | Concurrency | Wall time |
| :--- | :-: | :-: | :-: |
| Sequential | 200 | 1 | |
| `gather` + semaphore | 200 | 10 | |
| `gather` + semaphore, server uses `time.sleep` | 200 | 10 | |

---

## 📦 What this module produces

- [ ] The three-row timing table above, in `notes/async-timing.md`
- [ ] A `failure-log.md` entry for the blocking-call bug
