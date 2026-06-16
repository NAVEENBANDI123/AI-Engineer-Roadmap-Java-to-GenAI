# 🎯 80/20 Skills · Common Mistakes · Interview Prep

[⬅ Back to README](../README.md)

---

## ⚡ The 80/20 Rule — The 20% of Skills That Yield 80% of Results

If you optimize purely for **getting hired as an AI/GenAI Engineer in 2026**, these are the highest-leverage skills. Master these *first and deeply*; everything else is supporting cast.

### The Vital Few (do these exceptionally well)
1. **Python fluency + APIs (FastAPI, async, Pydantic).** Everything runs on this.
2. **LLM API mastery** — OpenAI + Anthropic, structured outputs, **tool/function calling**, streaming, cost.
3. **RAG done right** — chunking, embeddings, **hybrid + reranking**, and especially **evaluation**.
4. **Agents** — tool calling, the ReAct loop, memory, **MCP**, and one orchestration framework (LangGraph).
5. **Evaluation** — golden sets, LLM-as-judge, Ragas/DeepEval, eval-driven development. *This is the #1 underrated differentiator.*
6. **Prompt engineering for reliability** — structured output, injection defense.
7. **Deployment basics** — Docker, serving (vLLM/API), tracing (Langfuse/LangSmith), cost/latency optimization.
8. **Building & shipping projects** — a strong, documented portfolio beats certificates.

### The Trivial Many (important, but don't let them block you early)
- Deep proofs in linear algebra/calculus, training huge models from scratch, exotic RL math, every framework, Kaggle grandmaster status, memorizing all of classical ML.

> **Strategic takeaway:** Get *dangerous* with #1–8 in ~6 months, land the role, then deepen fundamentals (math, DL, from-scratch models) on the job and via Phases 9–12. Reverse the order only if you target research/LLM-Engineer roles.

### 80/20 by Tool
| Learn deeply (high ROI) | Learn enough to use | Awareness only |
|-------------------------|---------------------|----------------|
| Python, FastAPI, Pydantic | TensorFlow/Keras | Exotic architectures (Mamba/MoE internals) |
| OpenAI + Anthropic APIs | CrewAI/AutoGen | Distributed training internals (early) |
| LangChain/LlamaIndex + a vector DB | Diffusion models | TPU/Triton kernels |
| LangGraph + MCP | RLHF/PPO math | Research-grade RL |
| Embeddings + RAG + reranking | LoRA/QLoRA | Pre-training at scale |
| Ragas/DeepEval + LLM-as-judge | Quantization | — |
| Docker + vLLM + tracing | Kubernetes | — |

---

## ❌ Common Mistakes (and how to avoid them)

### Learning mistakes
1. **Tutorial hell / no building.** *Fix:* ≤30% consuming, ≥70% building. Ship weekly.
2. **Math-first paralysis.** *Fix:* Learn math intuition just-in-time; don't gate GenAI on calculus.
3. **Chasing every new model/framework.** *Fix:* Master primitives; tools change, fundamentals don't.
4. **Watching, not implementing.** *Fix:* Reproduce from scratch (attention, RAG, an agent loop).
5. **No portfolio / private repos.** *Fix:* Public GitHub, documented READMEs, demos.

### Engineering mistakes
6. **Naive RAG and stopping there.** *Fix:* Hybrid + rerank + **evaluate**; fix the measured weak stage.
7. **No evaluation ("vibe-checking" demos).** *Fix:* Golden set + LLM-judge + CI gates from day one.
8. **Trusting LLM output blindly.** *Fix:* Validate structured output, defend against prompt injection, verify citations.
9. **Reaching for fine-tuning too early.** *Fix:* Prompt → RAG → *then* fine-tune; FT is for behavior/format, not facts.
10. **Over-engineering agents.** *Fix:* Prefer deterministic workflows; add autonomy only where needed; add guardrails/limits.
11. **Ignoring cost/latency.** *Fix:* Track tokens/$/latency; cache; route cheap→strong; quantize.
12. **No observability.** *Fix:* Trace every call/tool/token (Langfuse/LangSmith) — you can't fix what you can't see.
13. **Data leakage in ML.** *Fix:* Fit preprocessing only on train; use scikit-learn Pipelines.
14. **Security as an afterthought.** *Fix:* OWASP LLM Top 10, least-privilege tools, HITL for high-stakes actions.

### Career mistakes
15. **Waiting until "ready" to apply.** *Fix:* Apply ~1 month early; interviews teach you.
16. **Collecting certificates over projects.** *Fix:* Projects first; certs are a tiebreaker.
17. **Hiding your SWE background.** *Fix:* It's an asset — production discipline is rare in AI hires.

---

## 🧗 Interview Preparation Roadmap

AI Engineering interviews typically have **5 pillars**. Prepare each deliberately.

### 1. Coding (Python)
- DSA at LeetCode Easy/Medium level: arrays, strings, hashmaps, two-pointers, heaps (top-k), graphs/BFS-DFS.
- AI-flavored: implement cosine-similarity kNN, a tokenizer, batching, a retrieval function.
- *Prep:* NeetCode 150 patterns + 1–2 problems/day for 4 weeks.

### 2. ML / DL Fundamentals
- Bias/variance, regularization, metrics, overfitting; gradient descent, backprop, attention/transformers.
- "Explain how an LLM generates text." "What is cross-entropy?" "How does self-attention work?"
- *Prep:* Be able to whiteboard the transformer and the training loop.

### 3. GenAI / LLM Applied
- RAG architecture & failure modes; chunking/reranking/eval; agents/tools/MCP; prompting reliability; hallucination; fine-tune vs RAG vs prompt.
- *Prep:* Be able to design and critique a RAG/agent system out loud.

### 4. AI System Design (often the deciding round)
- Use the framework from [Phase 12](12-phase-12-advanced.md): Requirements → Constraints → Data → Approach → Retrieval/Memory → Orchestration → Serving → **Eval** → Monitoring → Cost → Iterate.
- Practice prompts: "Design a customer-support copilot," "Design a RAG platform for 10M docs," "Design a coding agent," "Design content moderation at scale."
- *Prep:* Do 8–10 mock designs; always cover eval, cost, latency, safety, and failure handling.

### 5. Project Deep-Dive / Behavioral
- Expect: "Walk me through your hardest project." Know your flagships cold — architecture, trade-offs, **eval numbers**, what failed and how you fixed it.
- Behavioral: ownership, collaboration, learning speed, dealing with ambiguity (STAR format).

### 4-Week Interview Sprint
| Week | Focus |
|------|-------|
| 1 | Coding patterns (NeetCode) + ML fundamentals review |
| 2 | GenAI/RAG/agents Q&A + re-read your project READMEs |
| 3 | System design mocks (5–6) + eval/cost/safety drills |
| 4 | Full mock interviews, behavioral STAR stories, company research |

### Sample Questions to Drill
- *Applied:* "Your RAG returns irrelevant chunks — how do you debug it?" "How do you evaluate a RAG system?" "When would you fine-tune vs use RAG?" "How do you stop prompt injection?"
- *Systems:* "How do you cut LLM inference cost by 70%?" "How do you serve a 70B model efficiently?" "Design memory for a long-running agent."
- *Fundamentals:* "Derive/explain attention." "Why does temperature change outputs?" "What's catastrophic forgetting?"

[⬅ Back to README](../README.md) · [Next: Certifications & Portfolio ➡](18-certifications-portfolio.md)
