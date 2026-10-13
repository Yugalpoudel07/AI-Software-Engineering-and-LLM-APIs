[🏠 **Main Repository**](../README.md) &nbsp;•&nbsp; [**Next module: What We've Learned From A Year of Building with LLMs** ⏭️](../What%20We%27ve%20Learned%20From%20A%20Year%20of%20Building%20with%20LLMs/README.md)

---

# 📘 AI Engineering — Chip Huyen (Weeks 31–33)

### *Chapters 1, 2 and 5 — with a free route for every chapter if you don't have the book yet*

[![Time](https://img.shields.io/badge/Time_budget-7_hrs-blue?style=flat-square)](#-the-study-path)
[![Type](https://img.shields.io/badge/Paid_book-O'Reilly_2024-orange?style=flat-square)](https://www.oreilly.com/library/view/ai-engineering/9781098166298/)
[![Used in](https://img.shields.io/badge/Backbone_book-Months_8–13-purple?style=flat-square)](#)

> [!NOTE]
> **Roadmap assignment:** Chapter 1 (building on foundation models), Chapter 2 (understanding foundation models: **read the sampling section closely**), Chapter 5 (prompt engineering). **Skip** everything else this month; each later chapter is assigned in its own month (Ch 6 → Month 9, Ch 3–4 → Month 10, Ch 7–8 → Month 11, Ch 9 → Month 12, Ch 10 → Month 13).
> **What you produce:** one page of notes per chapter, and your Week 32 temperature experiment checked against Chapter 2's explanation.

> [!TIP]
> **No book yet?** Every part below has a **free route**: the author's own chapter summaries in her public [`aie-book`](https://github.com/chiphuyen/aie-book) repo, plus her blog posts that the chapters grew out of (the *Agents* post even says it is adapted from the book). The free route covers the ideas, not every page. If you buy the book later, read the chapter and compare it with your notes.
>
> 📄 [Book page (O'Reilly)](https://www.oreilly.com/library/view/ai-engineering/9781098166298/) · 📄 [Full table of contents](https://github.com/chiphuyen/aie-book/blob/main/ToC.md) · 📄 [Chapter summaries](https://github.com/chiphuyen/aie-book/blob/main/chapter-summaries.md) · *checked 12 Oct 2026*

---

## 🗺 The study path

| Part | Chapter | When | Time | Status |
| :-: | :--- | :-: | :-: | :-: |
| 1 | Ch 1 — Introduction to Building AI Applications with Foundation Models | Week 31 | 1 h 50 | ☐ |
| 2 | ⭐ Ch 2 — Understanding Foundation Models (sampling!) | Week 32 | 2 h 20 | ☐ |
| 3 | ⭐ Ch 5 — Prompt Engineering | Week 33 | 2 h 20 | ☐ |
| 4 | Three one-page notes | Weeks 31–33 | 30 min | ☐ |
| | **Total** | | **7 h** | |

---

### Part 1 — Chapter 1: building on foundation models · 1 h 50

| Route | What to read | Time |
| :--- | :--- | :-: |
| 📕 Book | Chapter 1 in full | 1 h 40 |
| 🆓 Free | 1. [Chapter 1 summary](https://github.com/chiphuyen/aie-book/blob/main/chapter-summaries.md#chapter-1-introduction-to-building-ai-applications-with-foundation-models) (10 min) → 2. [Building LLM applications for production](https://huyenchip.com/2023/04/11/llm-engineering.html): [Part I. Challenges of productionizing prompt engineering](https://huyenchip.com/2023/04/11/llm-engineering.html#prompt_engineering_challenges) and [Part 2. Task composability](https://huyenchip.com/2023/04/11/llm-engineering.html#part_2_task_composability) (50 min) → 3. [Common pitfalls when building generative AI applications](https://huyenchip.com/2025/01/16/ai-engineering-pitfalls.html) — all six pitfalls (30 min) | 1 h 30 |

- [ ] Read one route
- [ ] Answer in your notes: **what is different about AI engineering versus ML engineering?** (hint: you adapt models instead of training them, evaluation becomes the hard part, and the interface is language). · 10 min

**Skip (free route):** Part 3 "Promising use cases" of the 2023 post. It is dated.

---

### Part 2 — ⭐ Chapter 2: understanding foundation models · 2 h 20

The roadmap says *read the sampling section closely*. It is the theory behind your Week 32 temperature experiment.

| Route | What to read | Time |
| :--- | :--- | :-: |
| 📕 Book | Chapter 2: skim training data, modelling and post-training (45 min); **read Sampling slowly, with a pen** (1 h) | 1 h 45 |
| 🆓 Free | 1. [Chapter 2 summary](https://github.com/chiphuyen/aie-book/blob/main/chapter-summaries.md#chapter-2-understanding-foundation-models) (10 min) → 2. ⭐ [Generation configurations: temperature, top-k, top-p, and test time compute](https://huyenchip.com/2024/01/16/sampling.html), which is the sampling section's origin: [Sampling](https://huyenchip.com/2024/01/16/sampling.html#sampling) → [Temperature](https://huyenchip.com/2024/01/16/sampling.html#temperature) → [Top-k](https://huyenchip.com/2024/01/16/sampling.html#top_k) → [Top-p](https://huyenchip.com/2024/01/16/sampling.html#top_p) → [Stopping condition](https://huyenchip.com/2024/01/16/sampling.html#stopping_condition) (55 min) → 3. [Test Time Compute](https://huyenchip.com/2024/01/16/sampling.html#test_time_compute) (20 min) → 4. [Structured Outputs](https://huyenchip.com/2024/01/16/sampling.html#structured_outputs) and [Constraint sampling](https://huyenchip.com/2024/01/16/sampling.html#constraint_sampling) (20 min) | 1 h 45 |

- [ ] Read one route
- [ ] **Paper check (35 min):** write softmax with temperature, `p_i = exp(z_i / T) / Σ exp(z_j / T)`, for the logits `[2.0, 1.0, 0.5, 0.0, -1.0]` at T = 0.5, 1 and 2, by hand or calculator. What happens as T → 0 and T → ∞? Then compare with what your Week 32 experiment (30 calls each at T = 0, 0.7, 1.2) actually showed.

> [!IMPORTANT]
> **Why this matters for S8:** structured output is a sampling-time trick (constrained decoding), but it is not a guarantee about the *content*. The schema can be valid while the field values are wrong. That is why the roadmap says *still validate with Pydantic* and *still measure field-level F1*.

---

### Part 3 — ⭐ Chapter 5: prompt engineering · 2 h 20

| Route | What to read | Time |
| :--- | :--- | :-: |
| 📕 Book | Chapter 5: intro and in-context learning (30 min); best practices (1 h 10); prompt attacks and defences (30 min) | 2 h 10 |
| 🆓 Free | 1. [Chapter 5 summary](https://github.com/chiphuyen/aie-book/blob/main/chapter-summaries.md#chapter-5-prompt-engineering) (10 min) → 2. Lilian Weng, [Prompt Engineering](https://lilianweng.github.io/posts/2023-03-15-prompt-engineering/): [Basic Prompting](https://lilianweng.github.io/posts/2023-03-15-prompt-engineering/#basic-prompting) incl. [Tips for Example Selection](https://lilianweng.github.io/posts/2023-03-15-prompt-engineering/#tips-for-example-selection) and [Ordering](https://lilianweng.github.io/posts/2023-03-15-prompt-engineering/#tips-for-example-ordering), [Instruction Prompting](https://lilianweng.github.io/posts/2023-03-15-prompt-engineering/#instruction-prompting), [Self-Consistency Sampling](https://lilianweng.github.io/posts/2023-03-15-prompt-engineering/#self-consistency-sampling), [Chain-of-Thought](https://lilianweng.github.io/posts/2023-03-15-prompt-engineering/#chain-of-thought-cot) (1 h) → 3. Real company prompts from the book: [Real-world use case prompts](https://github.com/chiphuyen/aie-book/blob/main/prompt-examples.md#real-world-use-case-prompts), especially Grab (data entity classification) and Pinterest (text-to-SQL) — close to S8 and S9 (40 min) → 4. Prompt attacks: read [Building A Generative AI Platform — Step 2. Put in Guardrails](https://huyenchip.com/2024/07/25/genai-platform.html#step_2_put_in_guardrails) (20 min) | 2 h 10 |

- [ ] Read one route
- [ ] Pick **one real prompt** from `prompt-examples.md` and rewrite it for your S8 extraction task. Save it as `prompts/extract_v1.md`: it is your first versioned prompt file (Week 33 build task 5). · 10 min

**Skip (free route):** Lilian Weng's Automatic Prompt Design and Augmented Language Models sections (agents come in Month 9). Prompt attacks in depth come in Month 10.

---

### Part 4 — Notes · 30 min

- [ ] `notes/ch01.md`, `notes/ch02.md`, `notes/ch05.md`: **one page each**, in your own words, closed book first, then check.

---

## 🧪 Exercise on your own work

Your **S8 extraction task** is the exercise. After Part 3, write down three prompt changes you expect to help (e.g. add 2 examples, put the schema last, ask for `null` when a field is missing). In Week 33, test each on your 100 labelled documents and keep only the ones whose improvement is **outside the bootstrap confidence interval**.

## 📦 What this module produces

- [ ] Three one-page chapter notes
- [ ] The temperature paper calculation, compared with your Week 32 experiment
- [ ] `prompts/extract_v1.md`: your first versioned prompt
