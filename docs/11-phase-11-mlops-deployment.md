# Phase 11 — MLOps & Deployment (LLMOps)

> **Goal:** Take models and AI apps from notebook to **reliable, observable, cost-efficient production**. This is where your software engineering background is your superpower.
> **Time:** ~3 weeks (20 hrs/wk) · **Prerequisite:** Phases 3–8 (something to deploy) + general SWE/DevOps.

[⬅ Phase 10](10-phase-10-custom-models.md) · [Back to README](../README.md) · [Next: Phase 12 ➡](12-phase-12-advanced.md)

---

## 🎯 Learning Objectives
- Serve models and LLM apps via robust APIs and high-throughput engines (**vLLM**).
- Build CI/CD, containerization, and reproducible pipelines for ML/LLM systems.
- Monitor quality, drift, cost, and latency; set up alerting and feedback loops.
- Optimize cost/latency (quantization, caching, routing, batching).

## 📚 Topics to Study

### 1. Serving & Inference
- **API serving**: FastAPI + Uvicorn/Gunicorn; streaming responses (SSE); async + concurrency.
- **LLM inference engines**: **vLLM** (PagedAttention, continuous batching, high throughput), TGI (Hugging Face), TensorRT-LLM, **Ollama** (local/dev), llama.cpp; LMDeploy, SGLang.
- Batching, KV-cache management, multi-LoRA serving, speculative decoding.
- Model gateways/routers: **LiteLLM**, OpenRouter; provider fallback & load balancing.
- Classical model serving: BentoML, KServe, Triton, ONNX Runtime, TorchServe.

### 2. Packaging, CI/CD & IaC
- **Docker** (and Compose) for reproducible images; GPU containers.
- **CI/CD**: GitHub Actions for tests, lint, eval-gates, build, deploy.
- Model/artifact & data **versioning**: MLflow Model Registry, DVC, HF Hub.
- **Kubernetes** basics for scaling (awareness → depth for platform roles); serverless GPU (Modal, RunPod, Replicate, SageMaker, Vertex AI, Bedrock).

### 3. Pipelines & Orchestration
- Training/inference pipelines: **Airflow**, **Prefect**, **Dagster**, Kubeflow, ZenML, Metaflow.
- Feature stores (Feast) — awareness; batch vs streaming inference.
- Reproducibility: config management (Hydra), seeds, experiment tracking (**MLflow**, **W&B**).

### 4. Monitoring & Observability (LLM-specific)
- **LLM tracing**: LangSmith, **Langfuse**, Arize Phoenix, Helicone, OpenLLMetry/OpenTelemetry.
- Track: latency (TTFT, tokens/sec), **cost per request**, token usage, error rates, cache hit rate.
- **Quality monitoring**: online evals, LLM-as-judge in prod, user feedback (thumbs), guardrail hit rate.
- Data/embedding **drift**, model regression detection; classical: Evidently, WhyLabs.
- Logging, dashboards (Grafana/Prometheus), alerting, on-call basics.

### 5. Cost, Latency & Reliability Engineering
- **Caching**: prompt/semantic/response caching; embedding cache; prompt caching (provider).
- **Model routing**: cheap model for easy queries, escalate to strong model when needed.
- Quantization for cheaper inference (Phase 10); right-sizing GPUs; autoscaling.
- Rate limiting, retries with backoff, circuit breakers, timeouts, graceful degradation/fallbacks.
- Load testing (Locust/k6); capacity planning; SLOs/SLAs.

### 6. Security, Privacy & Governance
- Secrets management; PII redaction; data residency; tenant isolation.
- **Guardrails** in prod (NeMo Guardrails, Guardrails AI, Llama Guard); prompt-injection defense.
- Access control, audit logging, responsible AI / compliance basics (EU AI Act awareness).

## 🧠 Detailed Explanation

MLOps/LLMOps is where AI Engineers with real software discipline pull ahead. The hard part of production AI is rarely the model — it's **reliability, observability, and cost**. You'll wrap models in robust APIs, but for self-hosted LLMs you'll reach for **vLLM**, whose continuous batching and PagedAttention give order-of-magnitude throughput gains over naive serving; **Ollama** stays your local/dev companion, and a gateway like **LiteLLM** gives you one interface across providers plus fallbacks.

Three habits define seniority. First, **trace everything**: with Langfuse/LangSmith you can see every prompt, tool call, token, and dollar — without this you're flying blind. Second, **evaluate continuously**: gate deploys on eval scores in CI and run online evals/feedback in prod so regressions are caught, not discovered by users. Third, **engineer cost and latency deliberately**: caching, model routing (cheap-first, escalate), quantization, and right-sized autoscaling routinely cut bills by 50–90%. Wrap it all in Docker + GitHub Actions, version your models/data, and add guardrails and secrets hygiene. Your Java/SWE background means you already understand CI/CD, containers, and on-call — you're mostly learning the *AI-specific* layers on top.

## 🧪 Practice Exercises
1. Serve an open model with vLLM; benchmark tokens/sec and concurrency vs a naive FastAPI loop.
2. Containerize an LLM app with Docker; add a GitHub Actions pipeline (lint, test, eval-gate, build).
3. Add Langfuse tracing to a RAG/agent app; build a cost+latency dashboard.
4. Implement semantic response caching and measure cost/latency savings.
5. Build a model router (cheap→strong escalation) with LiteLLM and measure quality/cost trade-off.
6. Load-test the API with Locust; add retries, timeouts, and a fallback model.

## 🛠️ Mini Projects
- **Self-hosted LLM service** — vLLM behind FastAPI, Dockerized, with streaming + metrics.
- **LLM gateway** — LiteLLM-based router with caching, fallbacks, cost tracking, and a dashboard.
- **CI/CD eval gate** — GitHub Actions that blocks merges if prompt/RAG eval scores regress.

## 🎒 Portfolio Project
**"Production-Grade GenAI Service"** — take a prior project (RAG or agent) and productionize it: Dockerized vLLM or API backend, LiteLLM gateway with caching + fallback, Langfuse tracing, an eval gate in CI/CD, monitoring dashboard (cost/latency/quality), autoscaling config, and a load test report. Document SLOs, cost per 1k requests, and trade-offs. This is the artifact that gets MLOps/Platform interviews.

---

## 📦 Recommended Resources

### Free Courses
- **DeepLearning.AI short courses** (free): *LLMOps*, *Automated Testing for LLMOps*, *Efficiently Serving LLMs*.
- **Made With ML (Goku Mohandas)** — free MLOps course (design → develop → deploy → iterate).
- **Full Stack Deep Learning** (free lectures); **MLOps Zoomcamp** (DataTalksClub, free).
- **vLLM / Langfuse / BentoML** docs & tutorials.

### Paid Courses
- **MLOps specializations** (Coursera/Udacity); **Maven** LLMOps cohorts.

### Books
- *Designing Machine Learning Systems* — Chip Huyen (**the** MLOps book).
- *AI Engineering* — Chip Huyen (2025; production LLM systems — highly recommended).
- *LLM Engineer's Handbook* — Iusztin & Labonne; *Machine Learning Engineering* — Andriy Burkov.

### YouTube Channels
- **MLOps.community**, **DataTalksClub**, **Made With ML**, **The AI Engineer / AI Engineer Summit talks**.

### Documentation
- [vLLM](https://docs.vllm.ai), [Ollama](https://github.com/ollama/ollama), [LiteLLM](https://docs.litellm.ai), [Langfuse](https://langfuse.com/docs), [LangSmith](https://docs.smith.langchain.com), [BentoML](https://docs.bentoml.com), [MLflow](https://mlflow.org/docs/latest/index.html), [Modal](https://modal.com/docs), [Docker](https://docs.docker.com).

### GitHub Repositories
- [vllm-project/vllm](https://github.com/vllm-project/vllm), [BerriAI/litellm](https://github.com/BerriAI/litellm), [langfuse/langfuse](https://github.com/langfuse/langfuse), [GokuMohandas/Made-With-ML](https://github.com/GokuMohandas/Made-With-ML), [bentoml/BentoML](https://github.com/bentoml/BentoML), [huggingface/text-generation-inference](https://github.com/huggingface/text-generation-inference).

---

## 🏁 Phase 11 Milestone
> You can serve LLMs at high throughput (vLLM), containerize + CI/CD an AI app with eval gates, trace and monitor cost/latency/quality, and cut cost via caching/routing/quantization. ✅

[⬅ Phase 10](10-phase-10-custom-models.md) · [Back to README](../README.md) · [Next: Phase 12 ➡](12-phase-12-advanced.md)
