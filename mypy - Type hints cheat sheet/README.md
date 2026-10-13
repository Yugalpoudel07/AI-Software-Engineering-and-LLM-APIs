[🏠 **Main Repository**](../README.md) &nbsp;•&nbsp; [⏮️ **Python - asyncio documentation**](../Python%20-%20asyncio%20documentation/README.md) &nbsp;•&nbsp; [**Next module: pytest - How to use fixtures** ⏭️](../pytest%20-%20How%20to%20use%20fixtures/README.md)

---

# 🏷 mypy — Type hints cheat sheet (Week 31)

### *One page that covers 90% of the type hints you will write, then `mypy --strict` passing*

[![Time](https://img.shields.io/badge/Time_budget-1.5_hrs-blue?style=flat-square)](#-the-study-path)
[![Version](https://img.shields.io/badge/mypy-2.4-2a6db2?style=flat-square)](https://mypy.readthedocs.io/en/stable/cheat_sheet_py3.html)

> [!NOTE]
> **Roadmap assignment:** all of it. **What you produce:** `mypy --strict` passing on your Month 8 package.
>
> 📄 https://mypy.readthedocs.io/en/stable/cheat_sheet_py3.html · *checked 12 Oct 2026 (mypy 2.4 docs)*

---

## 🗺 The study path

| Part | Section | Time | Status |
| :-: | :--- | :-: | :-: |
| 1 | Variables, built-in types, functions | 25 min | ☐ |
| 2 | Classes, duck types, forward references | 20 min | ☐ |
| 3 | When things are complicated; decorators; ⭐ coroutines | 15 min | ☐ |
| 4 | `mypy --strict` on your package | 30 min | ☐ |
| | **Total** | **1 h 30** | |

---

### Part 1 · 25 min
- [ ] [Variables](https://mypy.readthedocs.io/en/stable/cheat_sheet_py3.html#variables)
- [ ] [Useful built-in types](https://mypy.readthedocs.io/en/stable/cheat_sheet_py3.html#useful-built-in-types): `list[str]`, `dict[str, int]`, `X | None`
- [ ] [Functions](https://mypy.readthedocs.io/en/stable/cheat_sheet_py3.html#functions)

### Part 2 · 20 min
- [ ] [Classes](https://mypy.readthedocs.io/en/stable/cheat_sheet_py3.html#classes)
- [ ] [Standard "duck types"](https://mypy.readthedocs.io/en/stable/cheat_sheet_py3.html#standard-duck-types): accept `Iterable[str]`/`Mapping`, return concrete types
- [ ] [Forward references](https://mypy.readthedocs.io/en/stable/cheat_sheet_py3.html#forward-references)

### Part 3 · 15 min
- [ ] [When you're puzzled or when things are complicated](https://mypy.readthedocs.io/en/stable/cheat_sheet_py3.html#when-you-re-puzzled-or-when-things-are-complicated): `reveal_type`, `cast`, `# type: ignore[code]` (always with a code)
- [ ] [Decorators](https://mypy.readthedocs.io/en/stable/cheat_sheet_py3.html#decorators)
- [ ] ⭐ [Coroutines and asyncio](https://mypy.readthedocs.io/en/stable/cheat_sheet_py3.html#coroutines-and-asyncio): how to type `async def` and async generators (your token stream is an `AsyncIterator[str]`)

### Part 4 — On your package · 30 min
- [ ] Add to `pyproject.toml`:
  ```toml
  [tool.mypy]
  strict = true
  ```
- [ ] Run `uv run mypy src/` and fix every error **without** `Any` where a real type exists
- [ ] Add the mypy step to the GitHub Actions workflow you built in Month 7 (Week 29)

---

## 📦 What this module produces

- [ ] `mypy --strict` green on the Month 8 package, enforced in CI
