# 💼 Job-Focused Roadmaps (5 Roles)

> The "AI Engineer" title spans several real jobs. Below: what each role actually does, the skills/phases that matter most, the projects to show, and how to position your Java/SWE background.

[⬅ Back to README](../README.md)

---

## Role Comparison at a Glance

| Role | Core question they answer | Heaviest phases | Math depth | Hiring demand 2026 |
|------|---------------------------|-----------------|-----------|--------------------|
| **AI Engineer** | "Build AI features into products" | 5–8, 11 | Medium | Very high |
| **Generative AI Engineer** | "Build LLM/GenAI apps (RAG/agents)" | 5–8 | Low–Medium | Very high |
| **LLM Engineer** | "Adapt/serve/train LLMs" | 9–11 | High | High |
| **Applied AI Engineer** | "ML + LLM solutions to business problems" | 3–8, 11 | Medium–High | High |
| **AI Product Engineer** | "Ship AI products users love" | 5–8 + product | Low | High |

> Titles vary wildly by company. Read the **JD**, not the title. Most postings are a blend.

---

## 1) 🤖 AI Engineer
**What you do:** Integrate models (mostly via APIs) into applications — RAG, agents, pipelines — and own reliability/cost. Closest to your current SWE skill set.

- **Priority phases:** 1 → 5 → 6 → 7 → 8 → 11 (then backfill 2–4).
- **Top skills:** Python, LLM APIs (OpenAI/Anthropic), RAG, agents/tool-calling, prompt eval, FastAPI, Docker, vector DBs, tracing/observability, cost/latency optimization.
- **Show these projects:** Production RAG (#26–29), agents (#32–38), LLM gateway (#49), production agent platform (#53).
- **SWE-background leverage:** API design, testing, CI/CD, system design — emphasize these; they're rarer than people think.
- **Interview focus:** GenAI fundamentals, RAG/agent design, system design, coding (Python), evals.

## 2) ✨ Generative AI Engineer
**What you do:** Specialize in LLM/GenAI application building — RAG, prompting, agents, sometimes light fine-tuning. The fastest on-ramp for you.

- **Priority phases:** 1 → 5 → 6 → 7 → 8 (light 9, 11).
- **Top skills:** Prompt engineering + structured output, RAG (hybrid/rerank/eval), agents (LangGraph/MCP/CrewAI), embeddings/vector DBs, LangChain/LlamaIndex, evaluation (Ragas/DeepEval), Hugging Face.
- **Show these projects:** All 5 RAG projects, several agent projects, prompt eval lab, a fine-tuned model.
- **Interview focus:** Deep RAG + agent design, prompting reliability, eval, trade-offs (RAG vs FT), hallucination handling.

## 3) 🧠 LLM Engineer
**What you do:** Work close to the model — fine-tuning, alignment, distillation, quantization, high-throughput serving, sometimes training. The deepest, most technical track.

- **Priority phases:** 2 → 3 → 4 → 5 → 9 → 10 → 11 (strong math + DL required).
- **Top skills:** PyTorch, Transformers internals, LoRA/QLoRA/DPO/RLHF, data curation, distillation, quantization (GGUF/AWQ/GPTQ), vLLM/TGI serving, distributed training (FSDP/DeepSpeed), GPU/cost math.
- **Show these projects:** nano-LLM from scratch (#56), QLoRA + DPO (#43–44), distillation/quantization (#58–59), multi-LoRA + vLLM serving (#60–61), RLHF/GRPO (#62).
- **Interview focus:** DL/transformer internals, fine-tuning trade-offs, training/serving systems, math, paper discussion.

## 4) 🛠️ Applied AI Engineer
**What you do:** Solve concrete business problems with the *right* tool — classical ML for tabular, LLMs for language, end-to-end ownership. Very broad.

- **Priority phases:** 1 → 2 → 3 → 4 → 5 → 7 → 8 → 11.
- **Top skills:** Strong ML (XGBoost, validation, feature eng) **plus** GenAI/RAG/agents, data pipelines, deployment, evaluation, stakeholder framing.
- **Show these projects:** End-to-end ML service (#6/#40), production RAG, an agent, a fine-tune — breadth is the point.
- **Interview focus:** ML fundamentals + GenAI, problem framing, metrics, system design, "when would you NOT use an LLM?"

## 5) 📦 AI Product Engineer
**What you do:** Build AI-powered product features end-to-end (often full-stack), obsess over UX, latency, and user value; close to product/design.

- **Priority phases:** 1 → 5 → 6 → 7 → 8 + product/UX + light 11.
- **Top skills:** GenAI app building, prompt/RAG/agents, **full-stack** (FastAPI + a frontend like Next.js/Streamlit), streaming UX, evals tied to product metrics, fast iteration, cost awareness.
- **Show these projects:** Polished end-user apps — docs assistant (#31), support agent (#38), voice assistant (#47), multi-tenant RAG SaaS (#67).
- **Interview focus:** Product sense, GenAI app design, UX/latency trade-offs, shipping speed, demos.

---

## 🧩 Skill Matrix (depth needed per role)

| Skill | AI Eng | GenAI Eng | LLM Eng | Applied AI | AI Product |
|-------|:------:|:---------:|:-------:|:----------:|:----------:|
| Python / SWE | ●●● | ●●● | ●●● | ●●● | ●●● |
| Math / DL theory | ●● | ● | ●●● | ●●● | ● |
| Classical ML | ●● | ● | ●● | ●●● | ● |
| Prompt engineering | ●●● | ●●● | ●● | ●● | ●●● |
| RAG | ●●● | ●●● | ●● | ●●● | ●●● |
| Agents / MCP | ●●● | ●●● | ●● | ●● | ●●● |
| Fine-tuning | ● | ●● | ●●● | ●● | ● |
| Model internals/training | ● | ● | ●●● | ●● | ○ |
| MLOps / serving | ●●● | ●● | ●●● | ●● | ●● |
| Evaluation | ●●● | ●●● | ●●● | ●●● | ●● |
| Full-stack / UX | ●● | ●● | ○ | ● | ●●● |

*●●● = deep · ●● = solid · ● = working · ○ = awareness*

---

## 🚀 Positioning Your Java/SWE Background
- **Lead with engineering strengths:** "I bring production software discipline (testing, CI/CD, system design, on-call) to AI systems" — many AI hires lack this.
- **Bridge narrative:** "Java/SWE → built X GenAI projects → here's a production RAG/agent I shipped with evals and monitoring."
- **Target hybrid roles first** (AI Engineer / GenAI Engineer / AI Product Engineer) — they value your SWE background most and need the least net-new math.
- **Contribute to OSS** (LangChain, vLLM, HF) to signal credibility fast.

[⬅ Back to README](../README.md) · [Next: 80/20 Skills, Mistakes & Interview ➡](17-skills-mistakes-interview.md)
