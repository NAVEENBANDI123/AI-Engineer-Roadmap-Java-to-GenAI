# Phase 10 — Building Custom AI Models (LLM from Scratch)

> **Goal:** Demystify the model itself — build a small GPT from scratch, understand tokenization, pre-training, distillation, and quantization, and reason about GPU/cost for training.
> **Time:** ~3 weeks (20 hrs/wk) · **Prerequisite:** Phase 4 (Transformers/PyTorch) + Phase 9 (training mechanics).

[⬅ Phase 9](09-phase-9-fine-tuning.md) · [Back to README](../README.md) · [Next: Phase 11 ➡](11-phase-11-mlops-deployment.md)

---

## 🎯 Learning Objectives
- Implement the **Transformer / GPT** architecture from scratch in PyTorch.
- Understand tokenization (BPE) by building one.
- Run a small **pre-training** loop and understand scaling/compute trade-offs.
- Apply **distillation** and **quantization** to shrink/speed up models.
- Estimate **GPU requirements and cost** for training/inference.

## 📚 Topics to Study

### 1. Transformer Architecture (from scratch)
- Token + positional embeddings (learned, sinusoidal, **RoPE**); embedding tables.
- **Self-attention** → scaled dot-product → **multi-head attention**; causal masking.
- Feed-forward blocks, residual connections, **LayerNorm/RMSNorm**, pre-norm vs post-norm.
- The decoder-only (GPT) stack; output projection / LM head; weight tying.
- Modern components: **GQA/MQA** (efficient attention), **SwiGLU**, KV cache, **MoE** (mixture of experts — awareness), long-context tricks.

### 2. Tokenization (build one)
- Character vs word vs **subword**; **Byte-Pair Encoding (BPE)**, WordPiece, SentencePiece, byte-level BPE.
- Vocabulary size trade-offs; special tokens; chat templates.
- Build a BPE tokenizer (à la Karpathy's `minbpe`).

### 3. Pre-training
- Data pipeline: corpus collection, cleaning, dedup, tokenization, sharding, packing.
- Objective: next-token prediction, cross-entropy loss; teacher forcing.
- Training loop: batching, gradient accumulation, mixed precision, gradient clipping, LR warmup + cosine decay, checkpointing.
- **Scaling laws** (Chinch'lla-style compute/data/params trade-off) — intuition.
- Distributed training (awareness): data/tensor/pipeline parallelism, FSDP/DeepSpeed/ZeRO.

### 4. Model Compression
- **Knowledge distillation** — train a small "student" to mimic a large "teacher" (logits/features).
- **Quantization** — FP16/BF16 → INT8/INT4; PTQ vs QAT; **GPTQ, AWQ, GGUF/llama.cpp, bitsandbytes**; trade-offs.
- **Pruning** & sparsity (awareness); speculative decoding (inference speedup).

### 5. Training Pipelines, GPU & Cost
- GPU memory math: params + gradients + optimizer states + activations; why training needs ~4–6× the model size in VRAM (Adam).
- Picking hardware: consumer (RTX 4090/3090), cloud (A100/H100/L4), TPUs; renting (Lambda, RunPod, Vast, Modal, Colab/Kaggle).
- **Cost estimation**: GPU-hours × hourly rate; tokens × $/token for inference; when training is *not* worth it.
- Reproducibility: seeds, configs, experiment tracking, checkpoints.

## 🧠 Detailed Explanation

You will likely never pre-train a frontier model — but building a **small GPT from scratch** is the single best way to truly understand everything you use. Following **Karpathy's "Let's build GPT" / nanoGPT** (and Raschka's *Build an LLM from Scratch*), you'll implement embeddings, multi-head causal self-attention, transformer blocks, and a training loop, then train a tiny model on a small corpus (e.g., TinyShakespeare or a small subset). Suddenly attention, KV cache, sampling, and loss curves stop being magic.

**Tokenization** is the unglamorous foundation: building a BPE tokenizer reveals why token counts (and thus cost/latency) behave the way they do, and why models stumble on spelling/arithmetic. **Compression** is where custom-model knowledge pays off in production: **quantization** (GGUF/AWQ/GPTQ) lets you run capable models on cheap hardware, and **distillation** lets you ship a small fast model that mimics a big one — both are core 2026 cost-engineering skills. Finally, being able to do **GPU memory math and cost estimation** ("can this fine-tune fit on a 24GB card? what will this inference workload cost per month?") is a concrete senior differentiator that connects directly to MLOps (Phase 11).

## 🛠️ Build a Small LLM From Scratch (capstone)
**"nano-LLM"** — implement, in PyTorch, from first principles:
1. A **BPE tokenizer** (your own `minbpe`-style).
2. A **GPT** model (embeddings, multi-head causal attention, MLP blocks, RMSNorm, RoPE optional).
3. A **pre-training loop** (mixed precision, LR schedule, checkpointing, W&B logging) on a small corpus.
4. **Sampling/generation** with temperature/top-k/top-p.
5. (Stretch) **Quantize** it to run faster, or **distill** a smaller version; write up loss curves, samples, GPU usage, and cost.

Ship it with a README and notebook walkthrough. This is one of the most impressive portfolio pieces a self-taught AI Engineer can have.

## 🧪 Practice Exercises
1. Implement scaled dot-product attention + multi-head attention from scratch; unit-test shapes.
2. Build a byte-level BPE tokenizer; compare vocab sizes and token counts to a real tokenizer.
3. Train nanoGPT on TinyShakespeare; plot the loss curve; generate samples.
4. Quantize a small model to 4-bit (GGUF/AWQ) and benchmark speed + quality vs FP16.
5. Distill a small student from a larger teacher on a narrow task; compare accuracy/size.
6. Do the GPU memory math for fine-tuning a 7B model with Adam vs QLoRA; verify empirically.

---

## 📦 Recommended Resources

### Free Courses
- **Andrej Karpathy — "Let's build GPT from scratch"** & **"Let's build the GPT Tokenizer"** & **"Neural Networks: Zero to Hero"** (YouTube). *The* resource for this phase.
- **Sebastian Raschka — "Build an LLM from Scratch"** (free GitHub repo + videos).
- **Hugging Face** transformer/tokenizer docs & courses.

### Paid Courses
- **"Build a Large Language Model (From Scratch)"** — Sebastian Raschka (Manning, book + course).
- **Maven** "Train your own LLM" style cohorts.

### Books
- *Build a Large Language Model (From Scratch)* — Sebastian Raschka (**the** book for this phase).
- *Deep Learning* — Goodfellow et al. (theory reference).
- *The Annotated Transformer* (Harvard NLP, free) — paper-to-code walkthrough.

### YouTube Channels
- **Andrej Karpathy**, **Sebastian Raschka**, **Umar Jamil** (LLaMA/transformer from scratch), **StatQuest** (transformer intuition).

### Documentation
- [nanoGPT](https://github.com/karpathy/nanoGPT), [minbpe](https://github.com/karpathy/minbpe), [The Annotated Transformer](https://nlp.seas.harvard.edu/annotated-transformer/), [llama.cpp](https://github.com/ggml-org/llama.cpp), [AutoGPTQ](https://github.com/AutoGPTQ/AutoGPTQ), ["Attention Is All You Need"](https://arxiv.org/abs/1706.03762).

### GitHub Repositories
- [karpathy/nanoGPT](https://github.com/karpathy/nanoGPT), [karpathy/minbpe](https://github.com/karpathy/minbpe), [karpathy/build-nanogpt](https://github.com/karpathy/build-nanogpt), [rasbt/LLMs-from-scratch](https://github.com/rasbt/LLMs-from-scratch), [meta-llama/llama-models](https://github.com/meta-llama/llama-models).

---

## 🏁 Phase 10 Milestone
> You built a working GPT + BPE tokenizer from scratch, trained it, can quantize/distill models, and can estimate GPU/VRAM/cost for training and inference. ✅

[⬅ Phase 9](09-phase-9-fine-tuning.md) · [Back to README](../README.md) · [Next: Phase 11 ➡](11-phase-11-mlops-deployment.md)
