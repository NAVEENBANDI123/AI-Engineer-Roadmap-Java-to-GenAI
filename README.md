<div align="center">

# 🚀 AI Engineer Roadmap: From Java/Software Engineer to GenAI Expert

### A Complete, Industry-Level Roadmap from Beginner to Advanced AI Engineer

**Updated for 2026 AI Engineering Trends**

![Status](https://img.shields.io/badge/Status-Living%20Document-brightgreen)
![Level](https://img.shields.io/badge/Level-Beginner%20to%20Advanced-blue)
![Focus](https://img.shields.io/badge/Focus-Industry%20%26%20Job%20Ready-orange)
![Year](https://img.shields.io/badge/Updated-2026-purple)

*Built for a Junior Software Engineer who wants to become job-ready in AI as fast as possible (20 hrs/week).*

</div>

---

> **How to use this repository**
>
> This is a **living curriculum**, not a reading list. Each phase has objectives, topics, explanations, curated resources (free + paid + books + YouTube + docs + GitHub), exercises, and projects. Work top-to-bottom, **build while you learn**, and track your progress using the [Progress Tracking](docs/19-progress-tracking.md) tables.
>
> **Golden rule:** *Ship a project at the end of every phase.* Theory without shipped artifacts will not get you hired.

---

## 📑 Table of Contents

### Part I — Orientation
- [How to Use This Roadmap](#-how-to-use-this-roadmap)
- [The Big Picture (Learning Path Diagram)](#-the-big-picture--learning-path-diagram)
- [The 12-Phase Overview](#-the-12-phase-overview)
- [What Makes 2026 Different](#-what-makes-2026-different)

### Part II — The Phases (detailed docs)
| # | Phase | Doc |
|---|-------|-----|
| 0 | Prerequisites | [docs/00-phase-0-prerequisites.md](docs/00-phase-0-prerequisites.md) |
| 1 | Programming Foundations (Python + DSA + SQL) | [docs/01-phase-1-programming-foundations.md](docs/01-phase-1-programming-foundations.md) |
| 2 | Mathematics for AI | [docs/02-phase-2-mathematics.md](docs/02-phase-2-mathematics.md) |
| 3 | Machine Learning | [docs/03-phase-3-machine-learning.md](docs/03-phase-3-machine-learning.md) |
| 4 | Deep Learning (PyTorch + TensorFlow) | [docs/04-phase-4-deep-learning.md](docs/04-phase-4-deep-learning.md) |
| 5 | Generative AI | [docs/05-phase-5-generative-ai.md](docs/05-phase-5-generative-ai.md) |
| 6 | Prompt Engineering | [docs/06-phase-6-prompt-engineering.md](docs/06-phase-6-prompt-engineering.md) |
| 7 | RAG Systems | [docs/07-phase-7-rag.md](docs/07-phase-7-rag.md) |
| 8 | Agentic AI & Multi-Agent Systems | [docs/08-phase-8-agentic-ai.md](docs/08-phase-8-agentic-ai.md) |
| 9 | Fine-Tuning LLMs (LoRA/QLoRA/RLHF) | [docs/09-phase-9-fine-tuning.md](docs/09-phase-9-fine-tuning.md) |
| 10 | Building Custom Models (LLM from scratch) | [docs/10-phase-10-custom-models.md](docs/10-phase-10-custom-models.md) |
| 11 | MLOps & Deployment | [docs/11-phase-11-mlops-deployment.md](docs/11-phase-11-mlops-deployment.md) |
| 12 | Advanced AI Engineering & System Design | [docs/12-phase-12-advanced.md](docs/12-phase-12-advanced.md) |

### Part III — Plans, Projects & Career
| Topic | Doc |
|-------|-----|
| ⏱️ Realistic Timelines (3 / 6 / 12 / 18 / 24 months) | [docs/13-timelines.md](docs/13-timelines.md) |
| 📅 Weekly Study Plan (20 hrs/week, Junior SWE) | [docs/14-weekly-study-plan.md](docs/14-weekly-study-plan.md) |
| 🛠️ 75 Projects (25 Beginner / 25 Intermediate / 25 Advanced) | [docs/15-projects.md](docs/15-projects.md) |
| 💼 Job-Focused Roadmaps (5 roles) | [docs/16-job-roadmaps.md](docs/16-job-roadmaps.md) |
| 🎯 80/20 Skills, Common Mistakes, Interview Prep | [docs/17-skills-mistakes-interview.md](docs/17-skills-mistakes-interview.md) |
| 🏆 Certifications & Portfolio Strategy | [docs/18-certifications-portfolio.md](docs/18-certifications-portfolio.md) |
| ✅ Progress Tracking, Checklists & Milestones | [docs/19-progress-tracking.md](docs/19-progress-tracking.md) |
| 📚 Master Resource Library | [docs/20-resources.md](docs/20-resources.md) |

---

## 🧭 How to Use This Roadmap

1. **You are a Junior Software Engineer** — you already know how to code, use Git, debug, and read docs. That is a *huge* head start. This roadmap leverages it.
2. **Pick a timeline** from [Timelines](docs/13-timelines.md). The recommended fast track is **6 months to job-ready** at 20 hrs/week.
3. **Follow the [Weekly Study Plan](docs/14-weekly-study-plan.md)** — it sequences phases for the fastest path to employability.
4. **Build relentlessly.** Every phase ends with a portfolio project. Push everything to GitHub.
5. **Track progress** with the checklists in [docs/19-progress-tracking.md](docs/19-progress-tracking.md).

> ⚡ **The fastest path to an AI Engineering job in 2026 is NOT mastering math first.** It's becoming dangerous with LLM APIs, RAG, and agents quickly, *then* backfilling fundamentals. This roadmap is sequenced for that reality (see [80/20 Skills](docs/17-skills-mistakes-interview.md)).

---

## 🗺️ The Big Picture — Learning Path Diagram

```
                          ┌───────────────────────────────────────────────┐
                          │   PHASE 0: PREREQUISITES (mindset, tools, git)  │
                          └───────────────────────┬───────────────────────┘
                                                  │
                  ┌───────────────────────────────┼───────────────────────────────┐
                  ▼                                ▼                                ▼
        ┌──────────────────┐          ┌──────────────────────┐         ┌────────────────────┐
        │ PHASE 1          │          │ PHASE 2              │         │  (parallel track)  │
        │ Programming      │          │ Mathematics for AI   │         │  Start using LLM   │
        │ Python+DSA+SQL   │          │ LinAlg/Calc/Stats/Prob│        │  APIs from week 1  │
        └────────┬─────────┘          └───────────┬──────────┘         └─────────┬──────────┘
                 └──────────────┬─────────────────┘                              │
                                ▼                                                │
                    ┌────────────────────────┐                                  │
                    │ PHASE 3: MACHINE        │                                  │
                    │ LEARNING (scikit-learn) │                                  │
                    └───────────┬────────────┘                                  │
                                ▼                                                │
                    ┌────────────────────────┐                                  │
                    │ PHASE 4: DEEP LEARNING  │                                  │
                    │ PyTorch / TensorFlow    │                                  │
                    └───────────┬────────────┘                                  │
                                ▼                                                │
                    ┌────────────────────────┐                                  │
                    │ PHASE 5: GENERATIVE AI  │◄─────────────────────────────────┘
                    │ Transformers / LLMs     │
                    └───────────┬────────────┘
                                ▼
        ┌───────────────────────────────────────────────────────────┐
        │  THE APPLIED GENAI CORE (highest job demand in 2026)        │
        │                                                             │
        │  PHASE 6 Prompt Eng → PHASE 7 RAG → PHASE 8 Agentic AI      │
        └───────────────────────────────┬───────────────────────────┘
                                         ▼
        ┌───────────────────────────────────────────────────────────┐
        │  THE MODEL BUILDER TRACK (deep specialization)              │
        │                                                             │
        │  PHASE 9 Fine-Tuning → PHASE 10 Custom Models from Scratch  │
        └───────────────────────────────┬───────────────────────────┘
                                         ▼
        ┌───────────────────────────────────────────────────────────┐
        │  PHASE 11 MLOps & Deployment → PHASE 12 Advanced System     │
        │  Design (scaling, cost, eval, safety, agents in prod)       │
        └───────────────────────────────────────────────────────────┘

   ════════════════════════════════════════════════════════════════════════
   PORTFOLIO grows continuously │ Beginner → Intermediate → Advanced projects
   ════════════════════════════════════════════════════════════════════════
```

### Dependency Cheat Sheet
- **Phases 1 & 2** can run in parallel. Don't let math block you.
- **You can start Phases 5–7 (GenAI/Prompting/RAG) with Python alone** — you don't need deep ML theory to build great RAG apps. This is the fast track to job-readiness.
- **Phases 9 & 10** (fine-tuning, building models) require Phase 4 (Deep Learning) and Phase 2 (Math).
- **Phase 11 (MLOps)** leverages your existing software engineering skills the most.

---

## 🔭 The 12-Phase Overview

| Phase | Theme | Core Outcome | Est. Time (20h/wk) |
|-------|-------|--------------|--------------------|
| 0 | Prerequisites | Environment, mindset, Git, Linux, the AI landscape | 1 week |
| 1 | Programming Foundations | Python mastery, DSA-for-AI, SQL | 3–4 weeks |
| 2 | Mathematics for AI | LinAlg, Calculus, Probability, Statistics | 3–4 weeks (parallel) |
| 3 | Machine Learning | Classical ML, scikit-learn, end-to-end pipelines | 4 weeks |
| 4 | Deep Learning | Neural nets, PyTorch, TensorFlow, CNN/RNN/Transformers | 5 weeks |
| 5 | Generative AI | Transformers deep dive, LLMs, embeddings, diffusion | 3 weeks |
| 6 | Prompt Engineering | Reliable prompting, structured output, eval | 1–2 weeks |
| 7 | RAG Systems | Production retrieval pipelines, vector DBs, eval | 3 weeks |
| 8 | Agentic AI | Single/multi-agent, tools, memory, MCP, LangGraph | 4 weeks |
| 9 | Fine-Tuning | LoRA, QLoRA, RLHF/DPO, dataset curation | 3 weeks |
| 10 | Custom Models | Tokenization, pre-training, build a small LLM | 3 weeks |
| 11 | MLOps & Deployment | Serving, vLLM, monitoring, CI/CD, cost | 3 weeks |
| 12 | Advanced Engineering | System design, scaling, safety, evals at scale | Ongoing |

---

## 🌟 What Makes 2026 Different

The AI engineering landscape in 2026 is defined by a few dominant shifts. This roadmap is built around them:

1. **Agents went to production.** "Chatbot demos" are commoditized. Companies hire for **reliable agentic systems** — planning, tool use, memory, and **MCP (Model Context Protocol)** as the standard integration layer.
2. **RAG matured into "context engineering."** Naive RAG is table stakes. Hybrid search, reranking, structured retrieval, and rigorous **evaluation** separate juniors from seniors.
3. **Open models are competitive.** Llama, Qwen, Mistral, DeepSeek, Gemma and others mean **local LLMs (Ollama)** and **efficient serving (vLLM)** are core skills, not niche ones.
4. **Reasoning models & test-time compute** changed prompting and cost trade-offs.
5. **Evals are the new unit tests.** Knowing LLM-as-judge, golden datasets, and frameworks (Ragas, DeepEval, OpenAI Evals, LangSmith) is a hiring differentiator.
6. **Fine-tuning got cheap** via LoRA/QLoRA — small specialized models beat giant general ones for many production tasks.
7. **Cost & latency engineering** (quantization, caching, routing, distillation) is now a first-class concern.

> See each phase doc for the specific 2026 tools and how they map to the trend above.

---

## 🎓 Recommended Starting Point by Goal

| Your Goal | Start Here | Then |
|-----------|-----------|------|
| Job-ready ASAP (you can already code) | Phase 0 → Phase 1 (Python refresh) → **Phase 5–8 fast track** | Backfill Phases 2–4 |
| Deep ML/Research foundation | Phase 0 → 1 → 2 → 3 → 4 | 5–12 in order |
| LLM/GenAI specialist | Phase 0 → 1 → 5 → 6 → 7 → 8 → 9 | 10–12 |
| MLOps / Platform focus | Phase 0 → 1 → 3 → 4 → 11 | 7, 8, 12 |

---

<div align="center">

### ⭐ Star this repo, fork it, and turn the checklists into your personal AI Engineering journal.

**Next step:** Open [docs/00-phase-0-prerequisites.md](docs/00-phase-0-prerequisites.md) and begin.

</div>
