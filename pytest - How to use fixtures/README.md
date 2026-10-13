[🏠 **Main Repository**](../README.md) &nbsp;•&nbsp; [⏮️ **mypy - Type hints cheat sheet**](../mypy%20-%20Type%20hints%20cheat%20sheet/README.md) &nbsp;•&nbsp; [**Next module: HTTPX - Async Support** ⏭️](../HTTPX%20-%20Async%20Support/README.md)

---

# 🧪 pytest — How to use fixtures (+ monkeypatch, parametrize) (Week 31)

### *Short test suites that never touch a real API*

[![Time](https://img.shields.io/badge/Time_budget-2_hrs-blue?style=flat-square)](#-the-study-path)
[![Docs](https://img.shields.io/badge/pytest-stable_docs-0A9EDC?style=flat-square)](https://docs.pytest.org/en/stable/how-to/fixtures.html)

> [!NOTE]
> **Roadmap assignment:** fixtures, then the **monkeypatch** and **parametrize** how-to pages in the same section. **Skip** plugin writing.
> **What you produce:** tests for every failure path of your LLM client, with **no real network calls**.
>
> 📄 [Fixtures](https://docs.pytest.org/en/stable/how-to/fixtures.html) · [Monkeypatch](https://docs.pytest.org/en/stable/how-to/monkeypatch.html) · [Parametrize](https://docs.pytest.org/en/stable/how-to/parametrize.html) · *checked 12 Oct 2026 (pytest 9.x)*

---

## 🗺 The study path

| Part | Page | Time | Status |
| :-: | :--- | :-: | :-: |
| 1 | ⭐ Fixtures — requesting, scope, teardown | 50 min | ☐ |
| 2 | Fixtures — factories and parametrized fixtures | 15 min | ☐ |
| 3 | ⭐ Monkeypatch | 25 min | ☐ |
| 4 | Parametrize | 15 min | ☐ |
| 5 | A fake LLM server fixture | 15 min | ☐ |
| | **Total** | **2 h** | |

---

### Part 1 — ⭐ Fixtures · 50 min
📄 https://docs.pytest.org/en/stable/how-to/fixtures.html
- [ ] ["Requesting" fixtures](https://docs.pytest.org/en/stable/how-to/fixtures.html#requesting-fixtures): [Quick example](https://docs.pytest.org/en/stable/how-to/fixtures.html#quick-example), [Fixtures can request other fixtures](https://docs.pytest.org/en/stable/how-to/fixtures.html#fixtures-can-request-other-fixtures), [return values are cached](https://docs.pytest.org/en/stable/how-to/fixtures.html#fixtures-can-be-requested-more-than-once-per-test-return-values-are-cached)
- [ ] [Autouse fixtures](https://docs.pytest.org/en/stable/how-to/fixtures.html#autouse-fixtures-fixtures-you-don-t-have-to-request): use one to **block all real network access** in tests
- [ ] [Fixture scopes](https://docs.pytest.org/en/stable/how-to/fixtures.html#fixture-scopes): `function` vs `module` vs `session`
- [ ] ⭐ [`yield` fixtures (recommended)](https://docs.pytest.org/en/stable/how-to/fixtures.html#yield-fixtures-recommended) and [Safe teardowns](https://docs.pytest.org/en/stable/how-to/fixtures.html#safe-teardowns): start a fake server, yield its URL, shut it down

### Part 2 · 15 min
- [ ] [Factories as fixtures](https://docs.pytest.org/en/stable/how-to/fixtures.html#factories-as-fixtures): e.g. `make_response(status=429, retry_after=2)`
- [ ] [Parametrizing fixtures](https://docs.pytest.org/en/stable/how-to/fixtures.html#parametrizing-fixtures)

**Skip:** markers passing data to fixtures, automatic grouping, overriding fixtures on various levels, using fixtures from other projects.

### Part 3 — ⭐ Monkeypatch · 25 min
📄 https://docs.pytest.org/en/stable/how-to/monkeypatch.html
- [ ] [Monkeypatching functions](https://docs.pytest.org/en/stable/how-to/monkeypatch.html#monkeypatching-functions): replace `asyncio.sleep` so backoff tests run instantly
- [ ] [Monkeypatching returned objects: building mock classes](https://docs.pytest.org/en/stable/how-to/monkeypatch.html#monkeypatching-returned-objects-building-mock-classes)
- [ ] ⭐ [Global patch example: preventing "requests" from remote operations](https://docs.pytest.org/en/stable/how-to/monkeypatch.html#global-patch-example-preventing-requests-from-remote-operations): do the same for `httpx`
- [ ] [Monkeypatching environment variables](https://docs.pytest.org/en/stable/how-to/monkeypatch.html#monkeypatching-environment-variables): fake API keys in tests

### Part 4 — Parametrize · 15 min
📄 https://docs.pytest.org/en/stable/how-to/parametrize.html
- [ ] [`@pytest.mark.parametrize`: parametrizing test functions](https://docs.pytest.org/en/stable/how-to/parametrize.html#pytest-mark-parametrize-parametrizing-test-functions): one test, many failure cases

**Skip:** `pytest_generate_tests` and the "More examples" page.

### Part 5 — A fake LLM server · 15 min
- [ ] Write a `fake_llm` fixture (a small FastAPI app on a random port, or an `httpx.MockTransport`) that you can tell to return **200, 429 with `retry-after`, 500, a timeout, or malformed JSON**.

---

## 🧪 Exercise on your own work (Week 32 build task 3)

One parametrized test that covers every failure path of your LLM client:

```python
@pytest.mark.parametrize("scenario, expected", [
    ("ok", "returns text"),
    ("429_then_ok", "retries once, then returns text"),
    ("500_x3", "raises after max retries"),
    ("400", "raises immediately, no retry"),
    ("timeout", "raises TimeoutError"),
    ("bad_json", "one repair attempt, then validation error"),
])
```

## 📦 What this module produces

- [ ] A test suite for the LLM client with **zero** real network calls (an autouse fixture enforces it)
