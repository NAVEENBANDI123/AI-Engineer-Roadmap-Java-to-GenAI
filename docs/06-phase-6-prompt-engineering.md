# Phase 6 — Prompt Engineering

> **Goal:** Get reliable, structured, evaluable behavior out of LLMs — the day-to-day craft of an applied AI Engineer. Move beyond "tips" to *engineering* prompts you can test and version.
> **Time:** ~1–2 weeks (20 hrs/wk) · **Prerequisite:** Phase 5 (how LLMs decode/generate).

[⬅ Phase 5](05-phase-5-generative-ai.md) · [Back to README](../README.md) · [Next: Phase 7 ➡](07-phase-7-rag.md)

---

## 🎯 Learning Objectives
- Design prompts that are reliable, structured, and cheap.
- Use the core techniques (zero/few-shot, CoT, role, decomposition) deliberately.
- Enforce **structured output** (JSON/schema) and **tool/function calling**.
- Treat prompts as code: version, test, and **evaluate** them.

## 📚 Topics to Study

### 1. Fundamentals
- Anatomy of a prompt: **system / developer / user** roles; instructions, context, examples, output format.
- Zero-shot, **few-shot** (in-context learning), and when each helps.
- **Chain-of-Thought (CoT)** & step-by-step reasoning; "think then answer."
- Role/persona prompting; setting constraints and refusing patterns.
- Specificity, delimiters, and ordering effects; positional sensitivity.

### 2. Advanced Techniques
- **Self-consistency** (sample multiple, vote), **ReAct** (reason+act → bridges to agents), **Reflexion**/self-critique.
- **Prompt chaining** & task decomposition; map-reduce over long inputs.
- **Few-shot example selection** (static vs dynamic/retrieved).
- **Meta-prompting** & prompt optimization (DSPy auto-optimization — 2026 trend).
- Reasoning-model prompting (less hand-holding; let it reason) vs standard models.

### 3. Reliability & Production Craft
- **Structured outputs**: JSON mode, JSON Schema / Pydantic, OpenAI structured outputs, Anthropic tool-use for structure, **Instructor** / **Outlines** for guaranteed schemas.
- **Function/tool calling** schemas (bridge to Phase 8 agents).
- Guardrails: input/output validation, refusal handling, jailbreak resistance, **prompt-injection** awareness.
- **Prompt caching** (Anthropic/OpenAI) and cost/latency optimization.
- Determinism (temperature=0), idempotency, and graceful fallback/retries.
- **Versioning & templating** (Jinja, LangChain prompts, prompt registries).

### 4. Prompt Evaluation (critical, often skipped)
- Building a **golden dataset** of inputs/expected behaviors.
- **LLM-as-a-judge**, rubric scoring, pairwise comparison.
- Regression testing prompts in CI; tracking quality over model/prompt versions.
- Tools: **promptfoo**, LangSmith, OpenAI Evals (deepened in Phase 12).

## 🧠 Detailed Explanation

Prompt engineering in 2026 is *applied reliability engineering*, not clever phrasing. The job is to make a stochastic system behave predictably enough for production. The highest-leverage moves are: (1) **be explicit** about role, task, constraints, and output format; (2) **show, don't tell** with well-chosen few-shot examples; (3) **force structure** with JSON Schema/Pydantic so downstream code can trust the output; and (4) **evaluate** with a golden set so you can change models or prompts without silently regressing.

Two ideas matter disproportionately. First, **structured outputs + tool calling** turn LLMs from chatbots into reliable software components — this is the foundation of RAG (Phase 7) and agents (Phase 8). Second, **prompt-injection and jailbreak awareness**: any text you feed a model (retrieved docs, tool results, user input) can contain adversarial instructions — never blindly trust model output or let it execute privileged actions without guardrails. Finally, with **reasoning models**, over-engineered CoT prompts can *hurt*; learn to prompt them differently (state the goal, give context, let them think).

## 🧪 Practice Exercises
1. Take a flaky free-text task and convert it to a Pydantic-schema structured output that parses 100% of the time.
2. Compare zero-shot vs few-shot vs CoT on a reasoning task; measure accuracy on 20 examples.
3. Implement self-consistency (sample 5, majority vote) and measure the lift.
4. Build a function-calling prompt that picks the right tool for a query.
5. Write a prompt-injection test set and harden a summarizer against it.
6. Create a 30-example golden set and an LLM-as-judge eval; run it with `promptfoo`.

## 🛠️ Mini Projects
- **Structured data extractor** — messy emails/PDFs → validated JSON with Instructor/Outlines.
- **Prompt eval harness** — config-driven `promptfoo` suite comparing 3 prompts × 3 models with cost/latency/quality.

## 🎒 Portfolio Project
**"Prompt Engineering Lab"** — a small framework that stores versioned prompt templates, runs them against a golden dataset across multiple providers, scores with LLM-as-judge + rule-based checks, and outputs a comparison report (quality/cost/latency). Treat prompts like code with CI. This signals senior-level rigor.

---

## 📦 Recommended Resources

### Free Courses
- **DeepLearning.AI — "ChatGPT Prompt Engineering for Developers"** (free, Andrew Ng + OpenAI).
- **Anthropic "Prompt Engineering" interactive tutorial** (free, in their cookbook/docs).
- **Learn Prompting** (learnprompting.org, free) and **promptingguide.ai** (DAIR.AI).
- **OpenAI & Anthropic prompting guides** (official docs).

### Paid Courses
- **DeepLearning.AI short courses** on function calling, structured outputs, evals.
- **Maven cohort courses** on LLM evals/prompting (Hamel Husain, Shreya Shankar).

### Books
- *Prompt Engineering for Generative AI* — James Phoenix & Mike Taylor (O'Reilly).
- *Hands-On Large Language Models* — Alammar & Grootendorst (prompting chapters).

### YouTube Channels
- **DeepLearning.AI**, **Sam Witteveen**, **AI Jason**, **Matt Wolfe** (landscape), **All About AI**.

### Documentation
- [OpenAI Prompting/Structured outputs](https://platform.openai.com/docs/guides/structured-outputs), [Anthropic prompt engineering](https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/overview), [promptingguide.ai](https://www.promptingguide.ai), [Instructor](https://python.useinstructor.com), [Outlines](https://dottxt-ai.github.io/outlines/), [promptfoo](https://www.promptfoo.dev), [DSPy](https://dspy.ai).

### GitHub Repositories
- [dair-ai/Prompt-Engineering-Guide](https://github.com/dair-ai/Prompt-Engineering-Guide), [anthropics/anthropic-cookbook](https://github.com/anthropics/anthropic-cookbook), [openai/openai-cookbook](https://github.com/openai/openai-cookbook), [jxnl/instructor](https://github.com/jxnl/instructor), [stanfordnlp/dspy](https://github.com/stanfordnlp/dspy), [promptfoo/promptfoo](https://github.com/promptfoo/promptfoo).

---

## 🏁 Phase 6 Milestone
> You can force reliable structured output, choose techniques deliberately, defend against prompt injection, and evaluate prompts against a golden set in CI. ✅

[⬅ Phase 5](05-phase-5-generative-ai.md) · [Back to README](../README.md) · [Next: Phase 7 ➡](07-phase-7-rag.md)
