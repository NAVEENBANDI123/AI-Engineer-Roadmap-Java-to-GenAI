# Phase 5 — Generative AI

> **Goal:** Understand how modern generative models (especially LLMs) work, and become productive with the **Hugging Face** ecosystem, embeddings, and the major model providers.
> **Time:** ~3 weeks (20 hrs/wk) · **Prerequisite:** Phase 4 (Transformers). *Fast-trackers can enter here with strong Python and revisit DL theory later.*

[⬅ Phase 4](04-phase-4-deep-learning.md) · [Back to README](../README.md) · [Next: Phase 6 ➡](06-phase-6-prompt-engineering.md)

---

## 🎯 Learning Objectives
- Explain how LLMs are built (pretraining → instruction tuning → alignment) and how they generate text.
- Use Hugging Face Transformers to load, run, and pipeline open models.
- Understand and use **embeddings**, tokenization, and decoding parameters.
- Work fluently with OpenAI, Anthropic, and local LLMs (Ollama/vLLM).
- Understand image/audio generation (diffusion) at a working level.

## 📚 Topics to Study

### 1. How LLMs Work
- The Transformer recap; **decoder-only** models (GPT family) vs encoder/encoder-decoder.
- **Tokenization** — BPE, WordPiece, SentencePiece; vocab; why token count = cost.
- Pretraining (next-token prediction) → **instruction tuning** (SFT) → **alignment** (RLHF/DPO — deep dive in Phase 9).
- **Decoding/sampling**: temperature, top-k, top-p (nucleus), repetition penalty, max tokens, stop sequences.
- Context windows, attention costs, **KV cache**; long-context techniques.
- **Reasoning models** & test-time compute (2026 trend); when to use them.
- Emergent abilities, hallucination (why it happens), scaling laws (intuition).

### 2. Embeddings (foundation for RAG & search)
- What embeddings are; semantic similarity; cosine distance.
- Text embedding models (OpenAI `text-embedding-3`, open models like BGE, E5, Nomic, Jina).
- Sentence-Transformers; pooling; dimensionality; normalization.
- Multimodal embeddings (CLIP) — text+image in one space.

### 3. The Hugging Face Ecosystem
- **Transformers** — `pipeline`, `AutoModel`, `AutoTokenizer`, generation config.
- **Datasets** — loading/streaming/processing data.
- **Hub** — finding models/datasets, model cards, licenses (Apache/MIT/Llama license nuances).
- **Accelerate**, **Tokenizers**; intro to **PEFT** (Phase 9).
- Spaces & **Gradio** for demos.

### 4. Model Providers & Access
- **OpenAI APIs** (Responses/Chat, embeddings, structured outputs, function/tool calling, vision).
- **Anthropic APIs** (Messages API, tool use, long context, prompt caching, Claude models).
- Google Gemini, Mistral, Cohere — landscape awareness.
- **Local LLMs**: **Ollama** (easy local), **vLLM** (high-throughput serving) — open models (Llama, Qwen, Mistral, Gemma, DeepSeek, Phi).
- Open vs closed trade-offs: cost, privacy, control, capability.

### 5. Other Generative Modalities (working knowledge)
- **Diffusion models** — image generation (Stable Diffusion, FLUX); how denoising works conceptually; Hugging Face **`diffusers`**.
- Text-to-speech / speech-to-text (Whisper); music/audio gen — awareness level.
- Multimodal LLMs (vision + text) and their app patterns.

## 🧠 Detailed Explanation

A modern LLM is a decoder-only Transformer trained to predict the next token over a colossal corpus, then *instruction-tuned* and *aligned* so it follows requests helpfully and safely. At inference it converts your prompt into tokens, runs them through attention layers, and emits a probability distribution over the next token; **decoding parameters** (temperature/top-p) control how that distribution is sampled. Understanding this demystifies "creativity," determinism, and hallucination, and tells you exactly which knobs to turn for reliability.

**Embeddings** are the other pillar of applied GenAI: they map text (or images) into vectors where semantic similarity becomes geometric closeness. This is the engine of semantic search, RAG (Phase 7), clustering, deduplication, and recommendation. You'll choose embedding models by quality (MTEB leaderboard), dimensionality, cost, and whether they run locally.

The **Hugging Face** ecosystem is your toolbox for open models; the **provider APIs** (OpenAI, Anthropic) are your toolbox for frontier capability. A strong 2026 AI Engineer is fluent in both and can justify open-vs-closed and local-vs-API trade-offs on cost, latency, privacy, and capability. Diffusion/multimodal knowledge rounds you out for product work.

## 🧪 Practice Exercises
1. Tokenize the same sentence with 3 tokenizers; compare token counts and explain cost impact.
2. Generate text with an open model at temperatures 0/0.7/1.5; analyze the differences.
3. Embed 100 sentences; build a from-scratch semantic search with cosine similarity; visualize with UMAP.
4. Use Anthropic + OpenAI structured outputs to extract JSON reliably from messy text.
5. Run the same prompt on a cloud model and a local Ollama model; compare quality/latency/cost.
6. Generate an image with `diffusers` and caption it with a multimodal model.

## 🛠️ Mini Projects
- **Semantic search engine** over a document set (embeddings + cosine top-k) — the precursor to RAG.
- **Multi-provider chat app** with a provider switch (OpenAI/Anthropic/Ollama) and token/cost meter.
- **Image generation studio** — Gradio UI over `diffusers` with prompt presets.

## 🎒 Portfolio Project
**"GenAI Playground"** — a Streamlit/Gradio app that unifies: chat across providers (OpenAI/Anthropic/local), text embeddings + semantic search, image generation, and a live token/cost dashboard. Document model choices and trade-offs. This showcases breadth across the GenAI stack.

---

## 📦 Recommended Resources

### Free Courses
- **Hugging Face — "LLM Course" / "NLP Course"** (free, excellent, hands-on).
- **DeepLearning.AI Short Courses** (free): *Building Systems with the ChatGPT API*, *How Diffusion Models Work*, *Open Source Models with Hugging Face*.
- **Andrej Karpathy — "Intro to LLMs" / "Deep Dive into LLMs"** (YouTube).
- **Cohere LLM University** (free).

### Paid Courses
- **"Generative AI with LLMs"** — DeepLearning.AI + AWS (Coursera).
- **Maven / cohort courses** on applied LLMs (e.g., Hamel Husain & Jeremy Howard's eval-focused courses).

### Books
- *Hands-On Large Language Models* — Jay Alammar & Maarten Grootendorst (2024, highly practical).
- *Natural Language Processing with Transformers* — Tunstall, von Werra, Wolf (HF authors).
- *Build a Large Language Model (From Scratch)* — Sebastian Raschka (bridges to Phase 10).

### YouTube Channels
- **Andrej Karpathy**, **Jay Alammar** ("Illustrated Transformer"), **Sebastian Raschka**, **Sam Witteveen**, **AI Jason**, **Umar Jamil** (paper implementations).

### Documentation
- [Hugging Face Transformers](https://huggingface.co/docs/transformers), [Datasets](https://huggingface.co/docs/datasets), [diffusers](https://huggingface.co/docs/diffusers), [Sentence-Transformers](https://www.sbert.net), [OpenAI](https://platform.openai.com/docs), [Anthropic](https://docs.anthropic.com), [MTEB leaderboard](https://huggingface.co/spaces/mteb/leaderboard).

### GitHub Repositories
- [huggingface/transformers](https://github.com/huggingface/transformers), [UKPLab/sentence-transformers](https://github.com/UKPLab/sentence-transformers), [huggingface/diffusers](https://github.com/huggingface/diffusers), [rasbt/LLMs-from-scratch](https://github.com/rasbt/LLMs-from-scratch), [jalammar/illustrated-transformer](https://jalammar.github.io/illustrated-transformer/).

---

## 🏁 Phase 5 Milestone
> You can explain how an LLM generates text, use embeddings for semantic search, run open + closed + local models, get reliable structured output, and generate images — all demonstrated in a shipped GenAI app. ✅

[⬅ Phase 4](04-phase-4-deep-learning.md) · [Back to README](../README.md) · [Next: Phase 6 ➡](06-phase-6-prompt-engineering.md)
