# Phase 12 — Advanced AI Engineering & System Design

> **Goal:** Operate at senior level — design large-scale AI systems, run evaluation at scale, and own safety, reliability, and cost across the lifecycle. This phase never really "ends."
> **Time:** Ongoing · **Prerequisite:** Phases 5–11.

[⬅ Phase 11](11-phase-11-mlops-deployment.md) · [Back to README](../README.md)

---

## 🎯 Learning Objectives
- Design end-to-end AI systems against real constraints (scale, latency, cost, accuracy, safety).
- Build **evaluation at scale** — the backbone of trustworthy AI products.
- Reason about safety, security, and responsible AI in production.
- Make build-vs-buy, model-selection, and architecture trade-offs like a senior/staff engineer.

## 📚 Topics to Study

### 1. AI System Design (interview + real work)
- A repeatable framework: **Requirements → Constraints → Data → Model/approach → Retrieval/Memory → Orchestration → Serving → Eval → Monitoring → Cost → Iteration.**
- Latency/throughput/cost budgets; caching layers; async pipelines; queue-based architectures.
- Choosing components: API vs self-host, RAG vs fine-tune vs agent, sync vs batch, mono vs multi-model.
- Designing for failure: fallbacks, degradation, idempotency, retries, rate limits, multi-region.
- Case studies: design a support copilot, a RAG knowledge platform, a coding agent, a content-moderation system, a multi-tenant LLM platform.

### 2. Evaluation at Scale (the senior superpower)
- Eval taxonomy: unit/component evals, end-to-end, **LLM-as-judge**, human eval, A/B & online evals.
- Golden datasets, synthetic eval generation, **eval-driven development**, regression suites in CI.
- Agent **trajectory evaluation**; RAG triad; rubric & pairwise scoring; calibration of judges.
- Frameworks: **Ragas, DeepEval, OpenAI Evals, LangSmith, Promptfoo, Phoenix, Braintrust, Inspect (AISI)**.
- Benchmarks & their limits; contamination; building *your own* domain benchmark.

### 3. Scaling & Performance
- Distributed inference/training; multi-GPU; sharding; horizontal scaling & autoscaling.
- Throughput engineering: batching, KV-cache, quantization, speculative decoding, disaggregated serving.
- Multi-model orchestration, routing, and cost optimization at fleet scale.
- Long-context, memory systems, and **context engineering** at scale.

### 4. Safety, Security & Responsible AI
- Threat model: **prompt injection** (direct/indirect), jailbreaks, data exfiltration, **excessive agency**, supply-chain, model/data poisoning — see **OWASP Top 10 for LLM Applications**.
- Guardrails (input/output), content moderation, PII handling, red-teaming.
- Alignment, hallucination mitigation, citations/groundedness, refusal calibration.
- Governance: model cards, audit trails, compliance (EU AI Act, SOC2 awareness), bias/fairness, privacy.

### 5. Frontier Awareness (stay current — 2026+)
- Reasoning models & test-time compute; tool-use RL; agentic benchmarks.
- Multimodal & "omni" models; real-time/voice agents; computer/browser use.
- Long/infinite context, memory architectures; on-device/edge LLMs.
- Efficient architectures (MoE, state-space/Mamba, linear attention) — awareness.
- Open vs closed model trajectory; cost curves; standards like **MCP** and agent interop (A2A).

### 6. Engineering Leadership & Craft
- Build-vs-buy analysis; vendor/model risk; cost modeling & FinOps for AI.
- Writing design docs/RFCs; tech specs; communicating trade-offs to non-experts.
- Mentoring, code review for AI systems, incident reviews, on-call for AI services.

## 🧠 Detailed Explanation

Senior AI Engineering is the art of **trade-offs under constraints**. Anyone can wire an LLM to an API; the value is in choosing the *right* approach for the latency/cost/accuracy/safety budget, and proving it works with **evaluation**. In 2026, eval is the defining competency: teams that practice **eval-driven development** (define success metrics, build golden + synthetic datasets, gate changes on scores, monitor online) ship reliable AI; teams that "vibe-check" demos ship outages. Learn to build domain-specific benchmarks and to evaluate *agent trajectories*, not just final answers.

Equally, **safety and security move from afterthought to architecture**. The OWASP LLM Top 10 (prompt injection, excessive agency, sensitive-data leakage, etc.) should shape your designs from day one — especially for agents that can take actions. Combine guardrails, least-privilege tools, human-in-the-loop for high-stakes actions, and red-teaming. Finally, **stay current deliberately**: the field moves monthly, so cultivate a small set of high-signal sources (papers, a few newsletters/podcasts, key labs' blogs) and a habit of building a small thing with each major release. Depth in fundamentals (Phases 2–4, 10) is what lets you absorb new advances quickly instead of chasing hype.

## 🛠️ Capstone-Level Projects
- **AI System Design portfolio** — write 5 design docs (support copilot, RAG platform, coding agent, moderation system, multi-tenant LLM platform) with diagrams, trade-offs, cost models, and eval plans.
- **Eval platform** — a reusable harness combining offline (Ragas/DeepEval), CI gates, and online evals with dashboards for any LLM app you build.
- **Red-team report** — attack one of your own agents/RAG apps (injection, exfiltration, excessive agency), document findings, and ship mitigations.

## 🎒 Portfolio Project
**"AI Platform"** — integrate prior work into one cohesive, documented system: a multi-tenant API serving RAG + agents, with a model gateway/router, full tracing + online evals, guardrails, CI/CD eval gates, autoscaling, and a public design doc + cost analysis + eval results. This is a staff-level signal that consolidates Phases 5–12.

---

## 📦 Recommended Resources

### Free Courses / Talks
- **AI Engineer Summit / World's Fair talks** (YouTube) — current best practices from practitioners.
- **DeepLearning.AI short courses**: *Evaluating & Debugging GenAI*, *Quality & Safety for LLM Apps*, *Red Teaming LLM Applications*.
- **OWASP GenAI/LLM Top 10** (free), **Anthropic & OpenAI safety/eval cookbooks**.

### Paid Courses
- **Maven**: applied evals (Hamel Husain, Shreya Shankar) and AI system design cohorts.

### Books
- *AI Engineering* — Chip Huyen (2025) — *the* book for this phase.
- *Designing Machine Learning Systems* — Chip Huyen.
- *Designing Data-Intensive Applications* — Martin Kleppmann (system design foundations).

### YouTube / Newsletters / Podcasts (stay current)
- **Latent Space** (podcast + newsletter), **The Batch** (DeepLearning.AI), **Sebastian Raschka's Ahead of AI**, **Lilian Weng's blog**, **Chip Huyen's blog**, **Simon Willison's blog**, **The AI Engineer** channel.

### Documentation
- [OWASP Top 10 for LLM Apps](https://genai.owasp.org), [OpenAI Evals](https://github.com/openai/evals), [DeepEval](https://docs.confident-ai.com), [Ragas](https://docs.ragas.io), [Inspect (UK AISI)](https://inspect.aisi.org.uk), [Braintrust](https://www.braintrust.dev/docs), [Arize Phoenix](https://docs.arize.com/phoenix).

### GitHub Repositories
- [openai/evals](https://github.com/openai/evals), [confident-ai/deepeval](https://github.com/confident-ai/deepeval), [UKGovernmentBEIS/inspect_ai](https://github.com/UKGovernmentBEIS/inspect_ai), [Arize-ai/phoenix](https://github.com/Arize-ai/phoenix), [ray-project/ray](https://github.com/ray-project/ray).

---

## 🏁 Phase 12 Milestone
> You can design, evaluate, secure, scale, and cost-optimize an end-to-end AI system, defend it against the OWASP LLM threats, and articulate every trade-off in a design doc — i.e., you operate as a senior AI Engineer. ✅

[⬅ Phase 11](11-phase-11-mlops-deployment.md) · [Back to README](../README.md)
