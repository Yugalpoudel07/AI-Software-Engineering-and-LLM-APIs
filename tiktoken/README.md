[🏠 **Main Repository**](../README.md) &nbsp;•&nbsp; [⏮️ **Instructor - structured outputs library**](../Instructor%20-%20structured%20outputs%20library/README.md) &nbsp;•&nbsp; [**Next module: NeetCode - roadmap and practice lists** ⏭️](../NeetCode%20-%20roadmap%20and%20practice%20lists/README.md)

---

# 🔢 tiktoken (Week 32, reference)

### *Count tokens before you send, then check what you were actually billed*

[![Type](https://img.shields.io/badge/Reference-look_up,_don't_read-lightgrey?style=flat-square)](#)
[![Repo](https://img.shields.io/badge/openai%2Ftiktoken-GitHub-181717?style=flat-square)](https://github.com/openai/tiktoken)

> [!NOTE]
> **Roadmap assignment:** use it to estimate token counts in your cost tracker. **Time budget:** none of its own (lookups inside Week 32 build time).
> **What you produce:** token estimates **checked against what the API actually bills**.
>
> 📄 https://github.com/openai/tiktoken · *checked 12 Oct 2026*

> [!IMPORTANT]
> **tiktoken counts tokens for OpenAI models only.** If you chose **Claude** (Track B), use the provider's [token counting](https://platform.claude.com/docs/en/build-with-claude/token-counting) endpoint and the `usage` field instead. For your local Ollama model, use the model's own tokenizer, or just read `usage` from the response.

---

## ✅ Read once (15 min)

- [ ] [README](https://github.com/openai/tiktoken#-tiktoken): `enc = tiktoken.get_encoding("o200k_base")` / `tiktoken.encoding_for_model(...)`, then `len(enc.encode(text))`
- [ ] [What is BPE anyway?](https://github.com/openai/tiktoken#what-is-bpe-anyway): the same algorithm you built from scratch in **Month 6, Week 25**
- [ ] The OpenAI Cookbook notebook [How to count tokens with tiktoken](https://github.com/openai/openai-cookbook/blob/main/examples/How_to_count_tokens_with_tiktoken.ipynb): the section on counting **chat messages** (each message adds a few overhead tokens)

**Skip:** Performance, Extending tiktoken.

## 🧪 Exercise on your own work

For 20 S8 documents, log **estimated input tokens** (tiktoken) next to **billed input tokens** (`usage`). Report the average difference. That gap is the per-message overhead, and your cost tracker should account for it.

## 📦 What this module produces

- [ ] An estimate-vs-billed table (20 rows) in `notes/token-counts.md`
