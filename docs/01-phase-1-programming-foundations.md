# Phase 1 — Programming Foundations (Python + DSA + SQL)

> **Goal:** Reach professional fluency in Python for AI, know the DSA that actually matters for AI work, and write the SQL an AI Engineer needs.
> **Time:** ~3–4 weeks (20 hrs/wk) · **Prerequisite:** Phase 0. You already program (Java) — this is *transfer + Pythonic idioms + the data stack*.

[⬅ Phase 0](00-phase-0-prerequisites.md) · [Back to README](../README.md) · [Next: Phase 2 ➡](02-phase-2-mathematics.md)

---

## 🎯 Learning Objectives
- Write clean, idiomatic, typed Python and the scientific stack (NumPy, Pandas).
- Know the **subset** of data structures & algorithms that appear in AI engineering and interviews.
- Query and shape data with SQL for analytics and feature building.
- Master the tooling: virtualenvs, packaging, testing, linting, async, and APIs.

---

## 🐍 The Python Roadmap (for AI)

### 1. Core Python (fast for a Java dev)
- Types, f-strings, slicing, comprehensions (list/dict/set/generator).
- Functions, `*args/**kwargs`, default args pitfalls, lambdas.
- **Pythonic idioms**: truthiness, EAFP vs LBYL, context managers (`with`), enumerate/zip.
- OOP in Python: `dataclasses`, `@property`, dunder methods, `Enum`.
- **Type hints** + `mypy`/`pyright` (your Java background makes this natural and valued).
- Errors & exceptions, logging (not `print`), the `pathlib` way.

### 2. Intermediate Python
- Iterators, generators, `yield`, lazy evaluation.
- Decorators & closures; `functools` (`lru_cache`, `partial`, `wraps`).
- Concurrency: `threading` vs `multiprocessing` vs **`asyncio`** (critical for LLM API calls).
- Modules, packages, `__init__.py`, imports, and project layout (`src/` layout).
- Virtual environments & packaging with **`uv`** (2026 standard), `pyproject.toml`.
- Testing with **`pytest`**, fixtures, parametrization; linting/formatting with **`ruff`** + `black`.

### 3. The Scientific & Data Stack
- **NumPy** — ndarrays, broadcasting, vectorization, axis operations (the foundation of all ML).
- **Pandas** — Series/DataFrame, indexing (`loc`/`iloc`), groupby, merge/join, missing data, time series.
- **Matplotlib / Seaborn / Plotly** — visualization for EDA.
- **Jupyter / nbconvert / Polars** (fast modern alternative to Pandas — worth knowing in 2026).

### 4. AI-Engineering-Specific Python
- HTTP & APIs: `requests`, `httpx` (async), `pydantic` (v2) for data validation & structured LLM output.
- Building APIs: **FastAPI** (the default for serving AI in production).
- CLIs: `typer` / `argparse`. Config: `pydantic-settings`, `.env`.
- Working with files: JSON, CSV, Parquet, PDF parsing (`pypdf`, `unstructured`).

> **Why `pydantic` matters:** structured LLM outputs, tool/function-calling schemas, and API contracts all run through it. Learn it well.

---

## 🧮 Data Structures & Algorithms *Needed for AI*

You do **not** need competitive-programming mastery. You need the subset below — for writing efficient data/retrieval code and for passing the coding screen.

### Must-Know Data Structures
| Structure | Why it matters in AI |
|-----------|----------------------|
| Arrays / Lists / NumPy arrays | Tensors, batches, embeddings |
| Hash maps / Sets / Dicts | Caching, deduplication, vocab/token maps |
| Stacks / Queues | Tree/graph traversal, BFS/DFS, agent task queues |
| Heaps / Priority Queues | **Top-k retrieval**, beam search |
| Trees / Tries | Tokenizers, parsing, KD-trees |
| Graphs | Knowledge graphs, agent workflows, **LangGraph** |
| **Vectors & similarity** | Cosine/dot-product similarity = the heart of RAG |

### Must-Know Algorithms
- Sorting & binary search; two pointers; sliding window.
- BFS/DFS, topological sort (DAGs power agent/LangGraph workflows).
- Recursion & dynamic programming basics.
- **Nearest-neighbor search**: brute-force kNN → approximate NN (**HNSW**, IVF). This is the algorithmic core of vector databases — understand it conceptually.
- Hashing, **MinHash/LSH** (dedup & near-duplicate detection for datasets).
- Big-O analysis — be able to reason about cost of retrieval/embedding loops.

### Practice
- **NeetCode 150** (do the patterns, not all 150) or **LeetCode** Easy/Medium focused on arrays, hashmaps, heaps, graphs.
- Implement brute-force cosine-similarity kNN over a list of embeddings **from scratch** (no library). This single exercise demystifies vector DBs.

---

## 🗄️ SQL for AI Engineers

You will pull training data, build features, log/evaluate model outputs, and analyze experiments — all with SQL.

### Topics
- SELECT, WHERE, ORDER BY, LIMIT; aggregate functions; **GROUP BY / HAVING**.
- **JOINs** (inner/left/right/full), self-joins.
- Subqueries & **CTEs** (`WITH`), window functions (`ROW_NUMBER`, `RANK`, `LAG/LEAD`, moving averages).
- Data types, indexes (and how indexes relate to performance), `EXPLAIN`.
- Loading data into Pandas (`pd.read_sql`), SQLite for local work, Postgres for real projects.
- **pgvector** — Postgres extension for vector similarity search (bridges SQL → RAG; revisit in Phase 7).
- Analytics warehouses (conceptual): BigQuery / Snowflake / DuckDB (great local OLAP).

### Practice
- **SQLZoo**, **Mode SQL Tutorial**, **DataLemur** (SQL interview questions), **LeetCode Database**.
- Build a SQLite DB of your LLM API call logs (prompt, tokens, cost, latency) and write analytics queries over it.

---

## 🧪 Practice Exercises (Phase 1)
1. Reimplement 5 Java programs you know in idiomatic, typed Python; run `ruff` + `mypy` clean.
2. Vectorize a slow Python loop with NumPy and benchmark the speedup.
3. Do a full Pandas EDA on a Kaggle dataset (Titanic / Ames Housing): clean, group, visualize.
4. Build a FastAPI endpoint that validates input with Pydantic and calls an LLM.
5. Write async code that fans out 50 LLM API calls concurrently with `asyncio.gather` + rate limiting.

## 🛠️ Mini Projects
- **Async LLM batch processor** — read a CSV of prompts, call an API concurrently, write results + cost report to Parquet.
- **SQL-backed expense analyzer** — load transactions, build CTE/window-function reports, visualize.

## 🎒 Portfolio Project
**"DataOps Toolkit"** — a small, well-tested Python package (with `pyproject.toml`, `pytest`, CI via GitHub Actions, typed API) that ingests messy CSV/JSON/PDF, cleans it with Pandas, stores it in SQLite/Postgres, and exposes a FastAPI query endpoint. This proves *software engineering + data* in one repo.

---

## 📦 Recommended Resources

### Free Courses
- **freeCodeCamp** Python + Data Analysis with Python (YouTube/site).
- **Kaggle Learn** — Python, Pandas, Intro to SQL, Data Cleaning (short, hands-on, free).
- **CS50P** (Harvard, "Introduction to Programming with Python") — free, excellent.
- **Mode / SQLZoo / SQLBolt** — interactive SQL.

### Paid Courses
- **"Python for Everybody" specialization** (Dr. Chuck, Coursera) — gentle and thorough.
- **Talk Python / Test & Code** courses for professional Python practices.

### Books
- *Fluent Python* — Luciano Ramalho (the book that makes you *Pythonic*).
- *Python Crash Course* — Eric Matthes (if you want a gentler ramp).
- *Effective Pandas* — Matt Harrison.
- *SQL for Data Scientists* — Renée Teate.

### YouTube Channels
- **Corey Schafer** (best Python tutorials), **ArjanCodes** (clean Python design), **mCoding**, **Tech With Tim**.

### Documentation
- [Python docs](https://docs.python.org/3/), [NumPy](https://numpy.org/doc/), [Pandas](https://pandas.pydata.org/docs/), [FastAPI](https://fastapi.tiangolo.com), [Pydantic](https://docs.pydantic.dev), [uv](https://docs.astral.sh/uv/).

### GitHub Repositories
- [astral-sh/uv](https://github.com/astral-sh/uv), [astral-sh/ruff](https://github.com/astral-sh/ruff), [tiangolo/fastapi](https://github.com/fastapi/fastapi), [pola-rs/polars](https://github.com/pola-rs/polars).

---

## 🏁 Phase 1 Milestone
> You write typed, tested, idiomatic Python; you can wrangle data with NumPy/Pandas and SQL; you can build & serve an API; and you've shipped a packaged toolkit to GitHub. ✅

[⬅ Phase 0](00-phase-0-prerequisites.md) · [Back to README](../README.md) · [Next: Phase 2 ➡](02-phase-2-mathematics.md)
