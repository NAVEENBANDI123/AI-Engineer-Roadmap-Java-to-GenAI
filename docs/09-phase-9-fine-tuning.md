# Phase 9 — Fine-Tuning LLMs (LoRA / QLoRA / RLHF / DPO)

> **Goal:** Adapt open models to your task/domain efficiently and correctly — including when *not* to fine-tune. Master parameter-efficient fine-tuning and preference alignment.
> **Time:** ~3 weeks (20 hrs/wk) · **Prerequisite:** Phase 4 (DL/PyTorch), Phase 5 (HF/LLMs), Phase 2 (loss/gradients intuition).

[⬅ Phase 8](08-phase-8-agentic-ai.md) · [Back to README](../README.md) · [Next: Phase 10 ➡](10-phase-10-custom-models.md)

---

## 🎯 Learning Objectives
- Decide correctly between **prompting → RAG → fine-tuning** (the decision tree).
- Curate datasets and run **SFT**, **LoRA**, and **QLoRA** fine-tunes on consumer/cloud GPUs.
- Understand **alignment**: RLHF, **DPO**, and newer preference methods.
- Evaluate fine-tuned models and avoid catastrophic forgetting/overfitting.

## 📚 Topics to Study

### 1. When to Fine-Tune (decision framework)
- **Prompting** fixes *instructions*. **RAG** fixes *knowledge*. **Fine-tuning** fixes *behavior/format/style/skill*.
- Cost/benefit: fine-tune for tone, structured output reliability, narrow tasks, latency/cost (smaller specialized model), domain language — *not* usually to "add facts" (use RAG).
- Combine: RAG + a small fine-tuned model is a common 2026 production pattern.

### 2. Data Curation (the real bottleneck)
- Instruction/response formats; chat templates; quality > quantity.
- Building datasets: synthetic data generation (distill from a strong model), cleaning, dedup, decontamination, formatting.
- Train/val/test splits; data licensing & PII; balancing.

### 3. Supervised Fine-Tuning (SFT)
- Full fine-tuning vs **parameter-efficient (PEFT)**.
- **LoRA** — low-rank adapters; rank `r`, `alpha`, target modules, dropout; tiny trainable %.
- **QLoRA** — 4-bit (NF4) quantized base + LoRA → fine-tune big models on a single consumer GPU.
- Training mechanics: learning rate, epochs, batch size, gradient accumulation, packing, masking, mixed precision.
- Tools: Hugging Face **PEFT + TRL (`SFTTrainer`)**, **Unsloth** (2× faster), **Axolotl** (config-driven), **bitsandbytes**.

### 4. Preference Alignment
- **RLHF** pipeline: SFT → reward model → **PPO** optimization (concept + why it's finicky).
- **DPO** (Direct Preference Optimization) — simpler, no separate reward model; the practical default.
- Newer methods: ORPO, KTO, SimPO, **RLAIF** (AI feedback), GRPO (reasoning/RL).
- Preference dataset construction (chosen vs rejected pairs).

### 5. Reinforcement Learning (foundations + RL for LLMs)
- RL basics: agent, environment, state, action, reward, policy, value function.
- Q-learning, policy gradients, **PPO** (intuition) — enough to understand RLHF/GRPO.
- RL for reasoning models (verifiable rewards), tool-use RL (2026 frontier — awareness level).

### 6. Evaluation & Pitfalls
- Held-out eval, task benchmarks, LLM-as-judge, A/B vs base model.
- **Catastrophic forgetting**, overfitting, reward hacking, eval contamination.
- Merging adapters, serving LoRA adapters (ties to Phase 11 / vLLM multi-LoRA).

## 🧠 Detailed Explanation

The most valuable skill here is **judgment**: most teams reach for fine-tuning too early. The decision tree is — try better *prompts* first, add *RAG* for knowledge, and only fine-tune when you need a consistent *behavior, format, style, or skill* that prompting can't reliably produce, or when you want a small cheap model to match a big one on a narrow task. Fine-tuning to "teach facts" usually disappoints; RAG is cheaper and stays fresh.

Once you do fine-tune, **data quality dominates everything**. A few thousand clean, well-formatted, on-task examples beat a noisy huge set. **LoRA/QLoRA** make this accessible: QLoRA loads the base model in 4-bit and trains tiny low-rank adapters, so you can fine-tune a 7B–14B model on a single free Colab/Kaggle or a modest cloud GPU. **TRL + PEFT** (and **Unsloth/Axolotl**) are the standard toolchain.

**Alignment** is how raw models become helpful/harmless. RLHF (SFT → reward model → PPO) is powerful but operationally tricky; **DPO** achieves much of the benefit by directly optimizing on preference pairs without a separate reward model and unstable RL loop — it's the pragmatic default, with ORPO/KTO/SimPO as variants. Understanding RL fundamentals (policy, reward, PPO, and newer GRPO for reasoning) lets you read the frontier and debug alignment behavior. Always evaluate against the base model and watch for **catastrophic forgetting** and **reward hacking**.

## 🧪 Practice Exercises
1. Build the decision tree on 5 real tasks: label each prompting/RAG/fine-tune and justify.
2. Curate a 1–3k example instruction dataset (incl. synthetic generation + cleaning).
3. QLoRA fine-tune a small open model (e.g., Llama/Qwen/Gemma) on Colab with TRL `SFTTrainer`.
4. Run a **DPO** fine-tune on a preference dataset; compare outputs to the SFT model.
5. Evaluate base vs fine-tuned with LLM-as-judge on a held-out set; report wins/losses.
6. Merge a LoRA adapter and run inference; then serve the adapter separately.

## 🛠️ Mini Projects
- **Domain assistant fine-tune** — QLoRA a small model on your domain (legal/medical/code/customer-support tone); compare to base + RAG.
- **Structured-output specialist** — fine-tune a small model to emit a strict JSON schema reliably and cheaply.
- **DPO style-alignment** — align a model to a specific writing style/persona via preference pairs.

## 🎒 Portfolio Project
**"Fine-Tuning Pipeline + Model Card"** — end-to-end: dataset curation (with synthetic data), QLoRA SFT, optional DPO, rigorous eval vs base (LLM-judge + task metrics), adapter publishing to Hugging Face Hub with a proper **model card** (data, method, eval, limitations, intended use). Bonus: serve it via vLLM (Phase 11). This is a standout LLM-Engineer portfolio piece.

---

## 📦 Recommended Resources

### Free Courses
- **DeepLearning.AI short courses** (free): *Finetuning Large Language Models* (Lamini), *Reinforcement Learning from Human Feedback*.
- **Hugging Face — fine-tuning & TRL guides**; **Unsloth notebooks** (free, Colab-ready).
- **Maxime Labonne — LLM Course** (free GitHub course; excellent fine-tuning notebooks).

### Paid Courses
- **Maven** fine-tuning/LLM cohorts (Hamel Husain, Dan Becker — applied fine-tuning + evals).
- **Udemy** LoRA/QLoRA hands-on courses.

### Books
- *LLM Engineer's Handbook* — Iusztin & Labonne (fine-tuning + LLMOps).
- *Hands-On Large Language Models* — Alammar & Grootendorst (fine-tuning chapters).
- *Natural Language Processing with Transformers* (HF authors).

### YouTube Channels
- **Sebastian Raschka**, **Maxime Labonne**, **Trelis Research**, **Unsloth**, **Umar Jamil** (LoRA/DPO/RLHF from scratch), **Sam Witteveen**.

### Documentation
- [HF PEFT](https://huggingface.co/docs/peft), [TRL](https://huggingface.co/docs/trl), [bitsandbytes](https://huggingface.co/docs/bitsandbytes), [Unsloth](https://docs.unsloth.ai), [Axolotl](https://docs.axolotl.ai), [QLoRA paper](https://arxiv.org/abs/2305.14314), [DPO paper](https://arxiv.org/abs/2305.18290).

### GitHub Repositories
- [huggingface/peft](https://github.com/huggingface/peft), [huggingface/trl](https://github.com/huggingface/trl), [unslothai/unsloth](https://github.com/unslothai/unsloth), [axolotl-ai-cloud/axolotl](https://github.com/axolotl-ai-cloud/axolotl), [mlabonne/llm-course](https://github.com/mlabonne/llm-course).

---

## 🏁 Phase 9 Milestone
> You can decide when to fine-tune, curate a dataset, run QLoRA SFT + DPO on a budget GPU, evaluate vs base, and publish a properly documented adapter/model card. ✅

[⬅ Phase 8](08-phase-8-agentic-ai.md) · [Back to README](../README.md) · [Next: Phase 10 ➡](10-phase-10-custom-models.md)
