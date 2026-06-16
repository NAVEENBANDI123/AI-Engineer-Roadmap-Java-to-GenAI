# Phase 0 — Prerequisites

> **Goal:** Set up your environment, mindset, and mental model of the AI landscape so the next 12 phases are friction-free.
> **Time:** ~1 week (20 hrs) · **Prerequisite:** None (you're a Junior SWE — you already have 80% of this).

[⬅ Back to README](../README.md) · [Next: Phase 1 ➡](01-phase-1-programming-foundations.md)

---

## 🎯 Learning Objectives
- Build a reliable local + cloud dev environment for AI work.
- Understand the **map of AI**: AI ⊃ ML ⊃ DL ⊃ GenAI ⊃ LLMs, and where "AI Engineer" sits.
- Get your first LLM API call working **today** (motivation matters).
- Adopt the habits (Git, notebooks, reproducibility) that prevent pain later.

## 📚 Topics to Study
1. **The AI landscape & terminology** — AI vs ML vs DL vs GenAI; model vs API vs framework; training vs inference; tokens, context window, embeddings.
2. **Roles** — AI Engineer vs ML Engineer vs Data Scientist vs MLOps vs Research Scientist (see [Job Roadmaps](16-job-roadmaps.md)).
3. **Dev environment** — Python via `pyenv`/`uv`, virtual environments, VS Code / Cursor, Jupyter, Git/GitHub.
4. **Command line & Linux basics** — shell navigation, pipes, env vars, `ssh`, `tmux`.
5. **Cloud & compute basics** — what a GPU is, CPU vs GPU vs TPU, when you need one, Google Colab / Kaggle free GPUs.
6. **API keys & secrets hygiene** — `.env`, never commit keys, billing limits.

## 🧠 Detailed Explanation

**The mental map.** Think of concentric circles. *Artificial Intelligence* is the broad goal of machines doing "smart" things. *Machine Learning* is the subset where systems learn patterns from data instead of being explicitly programmed. *Deep Learning* is ML using multi-layer neural networks. *Generative AI* is deep learning that **produces** new content (text, images, audio, code). *Large Language Models* (LLMs) are the generative text/reasoning engines (GPT, Claude, Llama, Gemini) you'll spend most of your career using.

**Where the AI Engineer sits.** An **AI Engineer** in 2026 mostly *builds applications and systems on top of models* — RAG, agents, pipelines, evals, deployment — rather than training giant models from scratch. That's great news for you: your software engineering skills transfer directly. You'll still learn the internals (Phases 3–4, 9–10) because understanding the engine makes you a far better driver and is required for senior roles.

**Training vs inference.** *Training* = teaching a model (expensive, GPU-heavy, occasional). *Inference* = using a trained model to get answers (what your app does constantly). Most AI Engineering is inference-time work: prompting, retrieval, orchestration, serving, and cost/latency optimization.

**Tokens & context.** LLMs read/write **tokens** (≈ ¾ of a word). The **context window** is how many tokens the model can consider at once. Cost and latency scale with tokens. Internalizing this early saves you money and debugging time.

## ✅ Prerequisites Checklist (set-up)
- [ ] Install Python 3.11+ (use `uv` or `pyenv`).
- [ ] Create a GitHub account + set up SSH keys (you likely have this).
- [ ] Install VS Code (or Cursor) + Python + Jupyter extensions.
- [ ] Create accounts: OpenAI, Anthropic, Hugging Face, Google Colab, Kaggle.
- [ ] Install [Ollama](https://ollama.com) and run `ollama run llama3.2` to confirm a local LLM works.
- [ ] Create a `.env` workflow with `python-dotenv`; add `.env` to `.gitignore`.

## 🧪 Practice Exercises
1. Make your first API call to OpenAI and Anthropic; print the response and the token usage.
2. Run a local model with Ollama and compare its answer to the API models.
3. Write a tiny script that loads a key from `.env` and refuses to run if it's missing.
4. Set up a fresh repo, commit a "hello AI" notebook, push to GitHub.

## 🛠️ Mini Project
**"LLM Hello World" CLI** — a Python CLI that takes a prompt and routes it to OpenAI, Anthropic, *or* a local Ollama model based on a `--provider` flag, and prints latency + token usage. (This becomes the seed for your model-router project in Phase 11.)

## 🎒 Portfolio Project
Start your **`ai-engineering-journey`** repo: a public learning log with a `notebooks/` folder, a `projects/` folder, and a README that you'll update every phase. Recruiters love seeing the journey.

---

## 📦 Recommended Resources

### Free Courses
- **Elements of AI** (University of Helsinki) — gentle, conceptual overview of the field.
- **Google "Introduction to Generative AI"** (Google Cloud Skills Boost) — free intro path.
- **Hugging Face "AI Agents" & "LLM" courses** (free) — bookmark for later phases.

### Paid Courses
- **DeepLearning.AI "AI For Everyone"** (Andrew Ng, Coursera) — best non-technical framing of the field.

### Books
- *Co-Intelligence* — Ethan Mollick (how to think about working with AI).
- *The Coming Wave* — Mustafa Suleyman (landscape & implications).

### YouTube Channels
- **3Blue1Brown** (intuition for math/NN later), **Andrej Karpathy**, **Two Minute Papers**, **Fireship** (fast landscape updates).

### Documentation
- [OpenAI docs](https://platform.openai.com/docs), [Anthropic docs](https://docs.anthropic.com), [Hugging Face docs](https://huggingface.co/docs), [Ollama docs](https://github.com/ollama/ollama).

### GitHub Repositories
- [ollama/ollama](https://github.com/ollama/ollama) — run local LLMs.
- [openai/openai-cookbook](https://github.com/openai/openai-cookbook) — practical recipes.
- [anthropics/anthropic-cookbook](https://github.com/anthropics/anthropic-cookbook).

---

## 🏁 Phase 0 Milestone
> You can call cloud + local LLMs from Python, manage secrets safely, and you can explain in two sentences what an AI Engineer does. ✅

[⬅ Back to README](../README.md) · [Next: Phase 1 ➡](01-phase-1-programming-foundations.md)
