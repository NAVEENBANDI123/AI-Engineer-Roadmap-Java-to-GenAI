# Phase 7 — RAG Systems (Retrieval-Augmented Generation)

> **Goal:** Build **production-grade** RAG: not a toy "embed-and-retrieve" demo, but a hybrid, reranked, evaluated, monitored pipeline. RAG is the single highest-demand applied GenAI skill in 2026.
> **Time:** ~3 weeks (20 hrs/wk) · **Prerequisite:** Phase 5 (embeddings) + Phase 6 (prompting/structured output).

[⬅ Phase 6](06-phase-6-prompt-engineering.md) · [Back to README](../README.md) · [Next: Phase 8 ➡](08-phase-8-agentic-ai.md)

---

## 🎯 Learning Objectives
- Explain RAG architecture end-to-end and *why* each component exists.
- Make informed choices on chunking, embeddings, retrieval, and reranking.
- **Evaluate** RAG quality rigorously (retrieval + generation metrics).
- Apply production best practices: caching, metadata filtering, security, monitoring.
- Use **LangChain**, **LlamaIndex**, and vector databases fluently.

---

## 🏛️ RAG Architecture (the full picture)

```
            ┌───────────────────────── INGESTION / INDEXING (offline) ─────────────────────────┐
            │                                                                                   │
 Raw docs → Loaders → Cleaning → CHUNKING → EMBEDDING model → Vector store (+ metadata, +keyword index)
 (PDF, web,                       (split into          (text→vectors)        (e.g. pgvector / Qdrant)
  DB, APIs)                        passages)                                                     │
            └───────────────────────────────────────────────────────────────────────────────────┘

            ┌───────────────────────── QUERY / SERVING (online) ──────────────────────────────┐
            │                                                                                  │
 User query → (Query transform: rewrite / HyDE / multi-query) → RETRIEVAL (vector + keyword =  │
              HYBRID) → top-N candidates → RERANKER (cross-encoder) → top-K → Build PROMPT      │
              (context + citations) → LLM → Answer + sources → GUARDRAILS → User                │
                                                  │                                             │
                                                  └──────────── EVALUATION & LOGGING ───────────┘
```

**Why RAG?** LLMs have frozen knowledge and hallucinate. RAG injects *relevant, fresh, private* context at query time so answers are grounded and citable — without retraining the model. It's the cheapest, fastest way to make an LLM an expert on *your* data.

---

## 📚 Topics to Study

### 1. Indexing (the offline pipeline)
- **Document loaders**: PDF (`pypdf`, `unstructured`, `PyMuPDF`), HTML/web, Office docs, Markdown, code, databases, APIs.
- Parsing hard formats: tables, scanned PDFs (OCR), images, layout-aware parsing.
- Cleaning & normalization; deduplication; metadata extraction (source, date, section, page).
- **Index types**: dense (vector), sparse (BM25/keyword), hybrid; **knowledge-graph** indexes; summary/hierarchical indexes (LlamaIndex).

### 2. Chunking Strategies (huge quality lever)
| Strategy | When to use |
|----------|-------------|
| Fixed-size (tokens/chars) + overlap | Simple baseline |
| Recursive character splitting | Respects natural boundaries (default for prose) |
| **Semantic chunking** | Split on meaning shifts; better coherence |
| Document-structure aware (headings, Markdown, code) | Structured docs/code |
| **Sentence-window / parent-document** | Retrieve small, return larger context |
| Proposition / atomic-fact chunking | High-precision QA |
- Choosing **chunk size & overlap**; the precision/recall trade-off; storing parent links.

### 3. Embeddings for Retrieval
- Choosing a model via **MTEB** (BGE, E5, Nomic, Jina, OpenAI `text-embedding-3`, Voyage, Cohere).
- Dimensionality, max sequence length, normalization, **domain fit**, cost, local vs API.
- **Matryoshka** embeddings (truncatable dims), multilingual, **multi-vector (ColBERT)** late interaction.
- Embedding fine-tuning for your domain (advanced; ties to Phase 9).

### 4. Vector Databases
- Concepts: ANN search, **HNSW** vs IVF/PQ, recall vs latency, filtering, hybrid search support.
- Options: **pgvector** (Postgres), **Qdrant**, **Weaviate**, **Milvus**, **Chroma** (local/dev), **Pinecone** (managed), **FAISS** (library), Elasticsearch/OpenSearch, Redis.
- Metadata filtering, namespaces/collections, upserts, scaling, cost.
- Choosing one: start with pgvector or Qdrant/Chroma; know the trade-offs.

### 5. Retrieval Methods
- Dense (semantic) vs sparse (**BM25/keyword**) vs **hybrid** (fusion, e.g. RRF).
- **Query transformations**: query rewriting, **HyDE** (hypothetical doc embeddings), multi-query, step-back, sub-question decomposition.
- Metadata/self-query filtering; recursive & hierarchical retrieval; auto-merging.
- **Agentic / multi-hop retrieval** (bridges to Phase 8); GraphRAG.

### 6. Reranking
- **Cross-encoder rerankers** (Cohere Rerank, BGE-reranker, Jina, Voyage) vs bi-encoder retrieval.
- Two-stage retrieve-then-rerank; why it dramatically boosts precision.
- Maximal Marginal Relevance (MMR) for diversity; cost/latency of reranking.

### 7. Generation & Context Assembly
- Prompt templates with citations; context ordering ("lost in the middle"); context-window budgeting.
- Handling no/low-confidence retrieval (say "I don't know"); answer grounding & citation enforcement.
- Streaming answers; structured RAG output.

### 8. RAG Evaluation (separates pros from amateurs)
- **Retrieval metrics**: hit rate, MRR, NDCG, context precision/recall.
- **Generation metrics**: faithfulness/groundedness, answer relevance, correctness vs ground truth.
- **Frameworks**: **Ragas**, **TruLens**, **DeepEval**, LlamaIndex evals, LangSmith.
- Building a synthetic + human golden Q/A set; the "RAG triad" (context relevance, groundedness, answer relevance).

### 9. Production Best Practices
- **Caching** (embeddings, retrieval, LLM responses); incremental/streaming ingestion & re-indexing.
- **Metadata & access control / multi-tenancy** (don't leak other users' docs!); PII handling.
- **Security**: prompt injection via retrieved content, data poisoning, citation verification.
- Observability: log queries, retrieved chunks, scores, latency, cost; trace with LangSmith/Phoenix.
- Latency/cost optimization: smaller models for routing, hybrid pre-filtering, async; **fallbacks**.
- Continuous evaluation in CI; feedback loops; handling stale data.

## 🧠 Detailed Explanation

Naive RAG (chunk → embed → top-k → stuff into prompt) is easy to demo and *terrible* in production. Real systems fail at retrieval, not generation: if the right chunk never gets retrieved, no LLM can save you. That's why 2026 RAG is really **"context engineering"** — and why this phase emphasizes **chunking, hybrid retrieval, query transformation, and reranking** far more than the LLM call itself.

The professional workflow is: build a baseline, then **measure** with Ragas/DeepEval on a golden Q/A set, then improve the *weakest measured component*. Usually that means adding hybrid search (BM25 + vector with RRF fusion), a cross-encoder **reranker**, better chunking (semantic or parent-document), and query rewriting/HyDE. Then you harden it: metadata access control, caching, injection defenses, observability, and fallbacks for low-confidence retrieval. The ability to *diagnose which stage is failing and fix it with evidence* is exactly what senior RAG roles pay for.

**LangChain** and **LlamaIndex** are the two dominant frameworks: LlamaIndex is data/retrieval-centric and superb for RAG; LangChain is broader orchestration. Learn both, but understand the primitives well enough to build RAG without a framework — interviewers love candidates who can.

---

## 🛠️ Build 5 Real-World RAG Projects

| # | Project | Skills Demonstrated | Stretch Goals |
|---|---------|---------------------|---------------|
| **1** | **"Chat with your PDFs"** — Q&A over a folder of PDFs with citations | Loaders, chunking, embeddings, vector store, cited generation, Streamlit UI | Multi-PDF, page-level citations, "I don't know" handling |
| **2** | **Documentation/Knowledge-Base Assistant** — RAG over a product's docs/website | Web/Markdown ingestion, incremental re-indexing, hybrid search | Slack/Discord bot front-end; freshness via scheduled re-index |
| **3** | **Hybrid Search + Reranking Engine** over a large corpus (e.g., Wikipedia subset or arXiv) | BM25 + dense fusion (RRF), cross-encoder reranking, metadata filters | Compare recall/latency vs naive; benchmark dashboard |
| **4** | **Evaluated Enterprise RAG** — same corpus, but with a full Ragas/DeepEval harness and CI | Golden Q/A set, RAG triad metrics, regression testing, experiment comparison | Auto-tune chunk size/top-k via eval scores |
| **5** | **Advanced/Agentic RAG** — multi-hop questions, GraphRAG or SQL+vector routing, multimodal (tables/images) | Query decomposition, routing, agentic retrieval, structured + unstructured sources | Production hardening: caching, access control, observability, cost dashboard |

> Ship each with a README documenting architecture choices, eval numbers, and trade-offs. These five projects alone can anchor an "Applied GenAI / RAG Engineer" portfolio.

## 🧪 Practice Exercises
1. Build naive RAG, measure it with Ragas, then add reranking and re-measure the lift.
2. Compare 3 chunking strategies on the same corpus by retrieval hit-rate.
3. Implement RRF hybrid fusion of BM25 + vector results from scratch.
4. Add metadata access control so users only retrieve their own documents.
5. Inject an adversarial instruction into a document and harden the pipeline against it.

---

## 📦 Recommended Resources

### Free Courses
- **DeepLearning.AI short courses** (free): *Building & Evaluating Advanced RAG* (with LlamaIndex/TruLens), *Preprocessing Unstructured Data for LLM Apps*, *Knowledge Graphs for RAG*, *Building Applications with Vector Databases*.
- **LangChain & LlamaIndex official tutorials**; **Pinecone Learning Center**; **Qdrant/Weaviate** tutorials.
- **freeCodeCamp** RAG/LangChain full courses (YouTube).

### Paid Courses
- **Maven: "Mastering RAG"** and applied LLM cohorts.
- **Udemy** LangChain/LlamaIndex RAG project courses.

### Books
- *Hands-On Large Language Models* — Alammar & Grootendorst (RAG chapters).
- *LLM Engineer's Handbook* — Iusztin & Labonne (RAG + production).
- *Building LLMs for Production* — Bouchard & Peng (Towards AI).

### YouTube Channels
- **LlamaIndex**, **LangChain**, **Greg Kamradt** (chunking/retrieval deep dives), **Sam Witteveen**, **Prompt Engineering** (channel), **Underfitted**.

### Documentation
- [LangChain RAG](https://python.langchain.com/docs/tutorials/rag/), [LlamaIndex](https://docs.llamaindex.ai), [Ragas](https://docs.ragas.io), [DeepEval](https://docs.confident-ai.com), [Qdrant](https://qdrant.tech/documentation/), [Weaviate](https://weaviate.io/developers/weaviate), [pgvector](https://github.com/pgvector/pgvector), [Chroma](https://docs.trychroma.com), [Cohere Rerank](https://docs.cohere.com/docs/rerank-overview).

### GitHub Repositories
- [langchain-ai/langchain](https://github.com/langchain-ai/langchain), [run-llama/llama_index](https://github.com/run-llama/llama_index), [explodinggradients/ragas](https://github.com/explodinggradients/ragas), [pgvector/pgvector](https://github.com/pgvector/pgvector), [qdrant/qdrant](https://github.com/qdrant/qdrant), [NirDiamant/RAG_Techniques](https://github.com/NirDiamant/RAG_Techniques) *(excellent catalog of advanced RAG patterns)*.

---

## 🏁 Phase 7 Milestone
> You can build a hybrid, reranked RAG pipeline, prove its quality with Ragas/DeepEval on a golden set, harden it for production (access control, caching, injection defense, observability), and explain every architectural choice. ✅

[⬅ Phase 6](06-phase-6-prompt-engineering.md) · [Back to README](../README.md) · [Next: Phase 8 ➡](08-phase-8-agentic-ai.md)
