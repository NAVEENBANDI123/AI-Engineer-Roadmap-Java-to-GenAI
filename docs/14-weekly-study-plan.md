# 📅 Weekly Study Plan — 20 hrs/week · Junior SWE · Job-Ready ASAP

> This is the **6-month fast-track** schedule (the recommended path from [Timelines](13-timelines.md)) broken into weekly detail. Goal: become a hireable **AI / GenAI Engineer** as fast as possible while you already hold a Junior SWE job.

[⬅ Back to README](../README.md)

---

## 🕐 How to Spend 20 Hours/Week (template)

| Block | Hours | Activity |
|-------|-------|----------|
| Learn (courses/reading/videos) | 6 | New concepts — *watch at 1.25–1.5×, take notes* |
| **Build (project work)** | 10 | The core. Code daily. Ship weekly. |
| Practice (exercises/DSA/SQL) | 2 | Reinforce + interview prep |
| Reflect & share | 2 | Write notes/blog, push to GitHub, update tracker |

**Daily rhythm (5 days × 4 hrs, or adapt):** 1 hr learn → 2.5 hr build → 0.5 hr review/commit. **Weekend option:** two longer build sessions. Consistency > intensity.

> 🔑 **Rule:** Never spend more than ~30% of a week consuming content. You learn AI engineering by *building and debugging*, not by watching.

---

## 🗓️ Month 1 — Foundations & Setup (Phases 0–1, + Math start)

| Week | Learn | Build / Practice | Milestone |
|------|-------|------------------|-----------|
| 1 | Phase 0: landscape, tools, providers | LLM Hello World CLI; set up journey repo; Ollama running | First cloud + local LLM call ✅ |
| 2 | Python refresh (idioms, typing, async), NumPy | Async LLM batch processor; `ruff`/`mypy` clean | Typed async script ✅ |
| 3 | Pandas + SQL + viz | EDA on a dataset; SQLite logging DB + analytics queries | EDA notebook + SQL report ✅ |
| 4 | DSA-for-AI (arrays, hashmaps, heaps, kNN) + start Math (LinAlg) | kNN cosine-sim from scratch; LeetCode patterns | DataOps Toolkit shipped ✅ |

## 🗓️ Month 2 — Math (parallel) + Machine Learning (Phases 2–3)

| Week | Learn | Build / Practice | Milestone |
|------|-------|------------------|-----------|
| 5 | LinAlg + Calculus intuition (3B1B), Probability | Math-of-ML notebooks; softmax/temperature demo | Math notebooks ✅ |
| 6 | ML workflow, regression/classification, metrics | Linear/Logistic regression from scratch (NumPy) | From-scratch models ✅ |
| 7 | Trees, RF, **XGBoost**, feature eng, validation/leakage | Churn or house-price project; Optuna + MLflow | Tuned tabular model ✅ |
| 8 | Clustering, PCA/UMAP, model selection | End-to-End ML Service (FastAPI + Docker + SHAP) | **Flagship #1: ML service** ✅ |

## 🗓️ Month 3 — Deep Learning + Transformers (Phase 4)

| Week | Learn | Build / Practice | Milestone |
|------|-------|------------------|-----------|
| 9 | NN foundations, backprop, PyTorch basics | MLP from scratch (NumPy) → PyTorch MNIST | Backprop understood ✅ |
| 10 | CNNs, transfer learning, W&B | CIFAR-10 transfer-learning classifier + Gradio demo | Vision classifier ✅ |
| 11 | RNN/LSTM → **Attention/Transformer** (Karpathy) | Implement self-attention + multi-head from scratch | Self-attention from scratch ✅ |
| 12 | Transformer deep dive; Keras crash | Vision/Text Transformer fine-tuner (Lightning + W&B) | **Flagship #2: DL fine-tuner** ✅ |

## 🗓️ Month 4 — Generative AI + Prompt Engineering (Phases 5–6)

| Week | Learn | Build / Practice | Milestone |
|------|-------|------------------|-----------|
| 13 | LLM internals, tokenization, decoding, HF Transformers | Tokenizer + decoding experiments; semantic search engine | Semantic search ✅ |
| 14 | Embeddings, providers (OpenAI/Anthropic/Ollama/vLLM intro), diffusion | Multi-provider chat app + token/cost meter | GenAI Playground ✅ |
| 15 | Prompt techniques, structured output, tool calling | Structured data extractor (Instructor/Pydantic) | Reliable JSON extraction ✅ |
| 16 | Prompt eval (LLM-judge, promptfoo), injection defense | Prompt Engineering Lab (versioned + CI eval) | **Flagship #3: Prompt eval lab** ✅ |

## 🗓️ Month 5 — RAG (Phase 7) — the portfolio centerpiece

| Week | Learn | Build / Practice | Milestone |
|------|-------|------------------|-----------|
| 17 | RAG architecture, loaders, chunking, vector DBs | RAG Project 1: **Chat with PDFs** (cited) | Naive RAG working ✅ |
| 18 | Embeddings choice, hybrid search (BM25+vector, RRF) | RAG Project 2: Docs/KB assistant; RAG Project 3: hybrid+rerank | Hybrid + reranking ✅ |
| 19 | **RAG evaluation** (Ragas/DeepEval), golden sets | RAG Project 4: full eval harness + CI gate | Measured & improved RAG ✅ |
| 20 | Advanced/agentic RAG, GraphRAG, production hardening | RAG Project 5: advanced + access control + observability | **Flagship #4: Production RAG** ✅ |

## 🗓️ Month 6 — Agents + Deployment + Job Hunt (Phases 8 + 11 intro)

| Week | Learn | Build / Practice | Milestone |
|------|-------|------------------|-----------|
| 21 | Agent loop, tool calling, ReAct, **MCP** | Agent Project 1 (ReAct) + Project 2 (MCP toolbox) | Working agent + MCP server ✅ |
| 22 | LangGraph (state, HITL), memory | Agent Project 6 (LangGraph stateful) + memory | Durable agent ✅ |
| 23 | Multi-agent (CrewAI/AutoGen), deployment basics (Docker, vLLM, tracing) | Agent Project 7 or 9 (multi-agent); productionize one app | **Flagship #5: Agent system** ✅ |
| 24 | Interview prep, system design, polish portfolio | Resume + GitHub polish; mock interviews; **apply!** | Portfolio live, applications out ✅ |

---

## 🎯 The 5 Flagship Projects (your interview portfolio)
1. **End-to-End ML Service** (tabular, deployed) — proves classical ML + SWE.
2. **Deep Learning Fine-Tuner** (PyTorch + W&B + demo) — proves DL.
3. **Prompt Engineering Lab** (versioned + evaluated) — proves rigor.
4. **Production RAG System** (hybrid, reranked, evaluated, hardened) — *the* GenAI showpiece.
5. **Agent System** (tools, memory, MCP, multi-agent, traced) — the 2026 hiring magnet.

> Polish 3–5 of these to "production README + demo + tests + eval numbers" quality. Quality of a few > quantity of many.

---

## 🔁 After Month 6 (continue while interviewing)
- **Month 7–8:** Phase 9 (fine-tune a model → model card on HF Hub).
- **Month 9:** Phase 10 (build nano-LLM from scratch — huge differentiator).
- **Month 10–11:** Phase 11 deep (vLLM, full MLOps).
- **Month 12:** Phase 12 (system design + eval platform capstone).

---

## 🧭 Weekly Habits Checklist
- [ ] Commit code at least 5 days this week (green GitHub graph).
- [ ] Ship/advance one project this week.
- [ ] Solve 2–3 DSA/SQL problems (interview upkeep).
- [ ] Write a short note/blog on what I learned (teaching = retention).
- [ ] Update the [Progress Tracker](19-progress-tracking.md).
- [ ] Read one high-signal AI source (The Batch / Latent Space / a paper).

[⬅ Back to README](../README.md) · [Next: 75 Projects ➡](15-projects.md)
