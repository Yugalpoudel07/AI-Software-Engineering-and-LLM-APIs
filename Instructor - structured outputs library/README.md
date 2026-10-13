[🏠 **Main Repository**](../README.md) &nbsp;•&nbsp; [⏮️ **FastAPI - Server-Sent Events, and StreamingResponse**](../FastAPI%20-%20Server-Sent%20Events%2C%20and%20StreamingResponse/README.md) &nbsp;•&nbsp; [**Next module: tiktoken** ⏭️](../tiktoken/README.md)

---

# 🧱 Instructor — structured outputs library (Week 32, optional)

### *Read it **after** you've built your own validation-and-retry, then compare*

[![Time](https://img.shields.io/badge/Time_budget-1_hr-blue?style=flat-square)](#-the-study-path)
[![Tag](https://img.shields.io/badge/OPTIONAL-only_with_spare_capacity-lightgrey?style=flat-square)](#)

> [!NOTE]
> **Roadmap assignment:** the getting-started page. **Skip:** everything else.
> **What you produce:** a note comparing **its retry approach to yours**.
>
> 📄 https://python.useinstructor.com/ · *checked 12 Oct 2026*

> [!WARNING]
> **Do not use Instructor inside from-scratch #10.** The point of Week 32 is building validation and repair yourself. Read this only when your own version passes its tests.

---

## 🗺 The study path

| Part | Page | Time | Status |
| :-: | :--- | :-: | :-: |
| 1 | Home: what it is, quick start | 15 min | ☐ |
| 2 | Getting started | 20 min | ☐ |
| 3 | ⭐ Validation and reasking, and retrying | 15 min | ☐ |
| 4 | The comparison note | 10 min | ☐ |
| | **Total** | **1 h** | |

---

- [ ] **Part 1:** [What is Instructor?](https://python.useinstructor.com/#what-is-instructor) → [Quick Start](https://python.useinstructor.com/#quick-start) → [Complex Schemas & Validation](https://python.useinstructor.com/#complex-schemas-validation)
- [ ] **Part 2:** 📄 [Getting started](https://python.useinstructor.com/getting-started/)
- [ ] **Part 3:** 📄 [Validation and reasking](https://python.useinstructor.com/concepts/reask_validation/): it sends the **validation error back to the model** and asks again. Then 📄 [Retrying](https://python.useinstructor.com/concepts/retrying/).
- [ ] **Part 4:** `notes/instructor-vs-mine.md`: how many retries does each do? What does each send back to the model? What happens on the last failure?

**Skip:** provider pages, hooks, templating, streaming partials, every integration page.

## 📦 What this module produces

- [ ] `notes/instructor-vs-mine.md`
