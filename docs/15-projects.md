# 🛠️ The 75-Project Roadmap (25 Beginner · 25 Intermediate · 25 Advanced)

> Projects are how you learn and how you get hired. Build a steady stream; **polish 5–8 into flagship portfolio pieces** (README + demo + tests + eval numbers). Push everything to GitHub.

[⬅ Back to README](../README.md)

**Legend — Skills:** `PY`=Python · `ML`=Machine Learning · `DL`=Deep Learning · `LLM`=LLM/GenAI · `RAG`=Retrieval · `AGT`=Agents · `FT`=Fine-tuning · `OPS`=MLOps/Deploy · `EVAL`=Evaluation

---

## 🟢 25 Beginner Projects (Phases 0–6)

| # | Project | Skills | What you learn |
|---|---------|--------|----------------|
| 1 | Multi-provider "Hello LLM" CLI (OpenAI/Anthropic/Ollama) | PY, LLM | API basics, secrets, token/cost |
| 2 | Data-cleaning + EDA notebook on a Kaggle dataset | PY, ML | Pandas, visualization |
| 3 | SQLite LLM-usage logger + analytics queries | PY | SQL, logging cost/latency |
| 4 | Async LLM batch processor (CSV in → results out) | PY, LLM | asyncio, rate limiting |
| 5 | Linear & logistic regression **from scratch** (NumPy) | PY, ML | Gradients, training loop |
| 6 | Titanic / house-price ML model (scikit-learn pipeline) | ML | End-to-end ML, no leakage |
| 7 | Spam / sentiment classifier (TF-IDF + sklearn) | ML | Text features, metrics |
| 8 | Customer segmentation (k-Means + PCA viz) | ML | Clustering, dimensionality reduction |
| 9 | MNIST digit classifier (PyTorch) | DL | NN training basics |
| 10 | Image classifier with transfer learning + Gradio demo | DL | Fine-tuning, deployment demo |
| 11 | Self-attention implemented from scratch (notebook) | DL | Transformer internals |
| 12 | Semantic search over 100 documents (embeddings + cosine) | LLM | Embeddings, similarity |
| 13 | Multi-provider chatbot with streaming + cost meter | LLM | Chat API, streaming |
| 14 | Structured data extractor (text → Pydantic JSON) | LLM | Structured output |
| 15 | Resume / job-description matcher (embeddings) | LLM | Semantic similarity app |
| 16 | Text summarizer with map-reduce over long docs | LLM | Chunking, prompt chaining |
| 17 | Few-shot vs CoT accuracy comparison harness | LLM, EVAL | Prompt techniques + measurement |
| 18 | Image generator studio (diffusers + Gradio) | LLM | Diffusion basics |
| 19 | Whisper-based audio transcriber + summarizer | LLM | Speech-to-text pipeline |
| 20 | "Chat with one PDF" (basic RAG) | RAG | Loader → chunk → embed → answer |
| 21 | FastAPI wrapper around an ML model + Docker | PY, OPS | Serving, containerization |
| 22 | Prompt template manager with versioning | LLM | Prompt-as-code |
| 23 | LLM-as-judge mini evaluator (promptfoo) | EVAL | Quality scoring |
| 24 | Personal flashcard generator from notes (LLM) | LLM | Practical LLM app |
| 25 | GitHub README generator from a repo | LLM | Context + generation |

## 🟡 25 Intermediate Projects (Phases 5–9)

| # | Project | Skills | What you learn |
|---|---------|--------|----------------|
| 26 | Production "Chat with your docs" RAG (citations, "I don't know") | RAG | Grounded, cited RAG |
| 27 | Hybrid search engine (BM25 + vector + RRF) | RAG | Fusion retrieval |
| 28 | RAG with cross-encoder reranking + before/after eval | RAG, EVAL | Two-stage retrieval |
| 29 | Ragas/DeepEval evaluation harness + CI gate | RAG, EVAL | Eval-driven development |
| 30 | Multi-PDF research assistant with metadata filters | RAG | Metadata, access control |
| 31 | Website/docs RAG chatbot (scheduled re-indexing) | RAG, OPS | Incremental ingestion |
| 32 | ReAct research agent (web search + calculator tools) | AGT | Tool calling, ReAct |
| 33 | Custom **MCP server** exposing your tools + a host client | AGT | MCP protocol |
| 34 | Text-to-SQL data-analyst agent (validation + charts) | AGT | Tool validation |
| 35 | LangGraph stateful agent with human-in-the-loop node | AGT | State machine, HITL |
| 36 | CrewAI content team (researcher→writer→editor) | AGT | Multi-agent roles |
| 37 | AutoGen group chat problem solver (planner+coder+critic) | AGT | Conversational multi-agent |
| 38 | Customer-support agent (RAG tool + actions + handoff) | AGT, RAG | Agentic RAG |
| 39 | Long-term memory chatbot (vector memory across sessions) | AGT, LLM | Memory systems |
| 40 | XGBoost model + Optuna + MLflow tracking + SHAP | ML, OPS | Tuning + experiment tracking |
| 41 | Recommender system (collaborative + embedding-based) | ML, LLM | Embeddings for recsys |
| 42 | Image captioning / VQA with a multimodal model | DL, LLM | Multimodal app |
| 43 | Fine-tune a small model with **QLoRA** (domain task) | FT | PEFT, TRL |
| 44 | **DPO** style-alignment of a small model | FT | Preference alignment |
| 45 | Synthetic dataset generator + cleaner for fine-tuning | FT, LLM | Data curation |
| 46 | Multilingual translation + quality eval app | LLM, EVAL | Eval at scale |
| 47 | Voice assistant (STT → LLM → TTS) pipeline | LLM | Real-time pipeline |
| 48 | Code review assistant (diff in → structured feedback) | LLM | Structured analysis |
| 49 | LLM gateway with caching + fallback + cost dashboard (LiteLLM) | OPS, LLM | Routing, caching |
| 50 | GraphRAG over a knowledge graph (entities + relations) | RAG | Graph retrieval |

## 🔴 25 Advanced Projects (Phases 8–12)

| # | Project | Skills | What you learn |
|---|---------|--------|----------------|
| 51 | Multi-agent "company" (supervisor + specialist workers) | AGT | Orchestrator–workers at scale |
| 52 | Coding agent that edits a repo + runs tests in a sandbox | AGT, OPS | Sandboxed autonomous coding |
| 53 | Production agent platform (tracing, evals, spend limits, async queue) | AGT, OPS, EVAL | Reliable agents in prod |
| 54 | Browser/computer-use agent for web automation | AGT | Action grounding, safety |
| 55 | Advanced agentic RAG (multi-hop, routing, multimodal sources) | RAG, AGT | Complex retrieval orchestration |
| 56 | **Build a small LLM (nano-LLM) from scratch + train it** | DL | Transformer + training loop |
| 57 | Build a BPE tokenizer from scratch | DL | Tokenization internals |
| 58 | Knowledge distillation: shrink a teacher into a fast student | FT, DL | Compression |
| 59 | Quantize + serve a model (GGUF/AWQ) and benchmark | OPS, DL | Quantization trade-offs |
| 60 | Self-hosted high-throughput inference with **vLLM** | OPS | Continuous batching, scaling |
| 61 | Multi-LoRA serving (swap adapters at inference) | FT, OPS | Adapter serving |
| 62 | RLHF/GRPO experiment on a small model (reward + policy) | FT | Alignment / RL for LLMs |
| 63 | Full LLMOps pipeline (CI/CD + eval gate + registry + deploy) | OPS, EVAL | End-to-end automation |
| 64 | Eval platform (offline + online + dashboards) reusable across apps | EVAL, OPS | Eval-driven org tooling |
| 65 | Red-team report: attack your own agent/RAG + ship mitigations | EVAL, AGT | Security / OWASP LLM |
| 66 | Guardrails layer (injection defense, PII redaction, moderation) | OPS | Safety engineering |
| 67 | Multi-tenant RAG SaaS (isolation, billing, access control) | RAG, OPS | Productization |
| 68 | Real-time/voice agent with low-latency streaming | AGT, OPS | Latency engineering |
| 69 | Domain expert: fine-tune + RAG hybrid + eval vs baselines | FT, RAG, EVAL | Combined production pattern |
| 70 | Recommendation/personalization engine with embeddings at scale | ML, OPS | Vector search at scale |
| 71 | Document-understanding pipeline (layout, tables, OCR → structured) | RAG, LLM | Hard data extraction |
| 72 | Autonomous research/report-writing multi-agent system | AGT | Long-horizon planning |
| 73 | Cost-optimization router (model selection by difficulty) + savings report | OPS, LLM | FinOps for AI |
| 74 | Distributed fine-tuning (multi-GPU, FSDP/DeepSpeed) | FT, OPS | Scaling training |
| 75 | **Capstone "AI Platform"**: RAG + agents + gateway + evals + monitoring + IaC, fully deployed | ALL | Staff-level integration |

---

## 🧭 Project Selection Strategy
- **Beginner:** do ~12–15 of the 25; speed matters, breadth over polish.
- **Intermediate:** do ~10–12; start polishing 2–3 into flagships (especially RAG #26–29 and Agents #32–38).
- **Advanced:** do 5–8; **#56 (nano-LLM), #53/#75 (production agent/platform), #69 (FT+RAG hybrid)** are the strongest senior signals.
- For each flagship, ship: clear README (problem, architecture diagram, decisions, **eval numbers**, trade-offs), live demo or video, tests, and clean code.

## 🌟 Project → Role Mapping
| Target Role | Must-build projects |
|-------------|--------------------|
| AI / Applied AI Engineer | 26–29, 32–38, 49, 53 |
| Generative AI Engineer | 26–31, 43–45, 53, 67 |
| LLM Engineer | 43, 44, 56, 58–62, 69 |
| AI Product Engineer | 26, 31, 38, 47, 67, 73 |
| MLOps / Platform | 49, 53, 60, 63, 64, 74, 75 |

[⬅ Back to README](../README.md) · [Next: Job Roadmaps ➡](16-job-roadmaps.md)
