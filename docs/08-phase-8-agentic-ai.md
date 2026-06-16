# Phase 8 — Agentic AI & Multi-Agent Systems

> **Goal:** Build **reliable** AI agents and multi-agent systems — planning, tool use, memory, MCP — and the production architectures that make them trustworthy. Agents are *the* defining hiring theme of 2026.
> **Time:** ~4 weeks (20 hrs/wk) · **Prerequisite:** Phase 6 (tool calling / structured output) + Phase 7 (retrieval as a tool).

[⬅ Phase 7](07-phase-7-rag.md) · [Back to README](../README.md) · [Next: Phase 9 ➡](09-phase-9-fine-tuning.md)

---

## 🎯 Learning Objectives
- Explain what makes a system "agentic": autonomy via the reason → act → observe loop.
- Build single-agent and **multi-agent** systems with tools, planning, and memory.
- Use **MCP (Model Context Protocol)** to connect agents to tools/data the standard way.
- Orchestrate with **LangGraph**, **CrewAI**, and **AutoGen**, and know when to use each (or none).
- Design **production agent architectures**: control, observability, cost, safety, human-in-the-loop.

---

## 📚 Topics to Study

### 1. Agent Foundations
- What is an agent? **LLM + tools + loop + memory + goal.**
- The **ReAct** loop (Reason → Act → Observe → repeat); function/tool calling as the action mechanism.
- Agent vs workflow vs pipeline: **prefer deterministic workflows; add autonomy only where it earns its keep** (Anthropic's "Building Effective Agents" guidance).
- Common patterns: prompt chaining, routing, parallelization, orchestrator–workers, evaluator–optimizer, autonomous agent.

### 2. Tool / Function Calling
- Defining tools (schemas), parsing tool calls, executing, returning results.
- Tool design: granularity, error handling, idempotency, validation, retries.
- Built-in tools: web search, code execution (sandboxed!), file/DB access, APIs, RAG-as-a-tool, computer/browser use.
- Parallel tool calls; tool-choice control; structured results.

### 3. Planning
- Task decomposition, ReAct, **Plan-and-Execute**, Tree/Graph-of-Thoughts, reflection/self-critique loops.
- Goal management, subgoal tracking, replanning on failure.
- Reasoning models as planners (2026); when to plan explicitly vs let the model reason.

### 4. Memory
- **Short-term** (context window / scratchpad) vs **long-term** (persistent store).
- Memory types: episodic, semantic, procedural; conversation summarization & compaction.
- Vector memory (RAG over past interactions); entity/state memory; **memory frameworks** (Mem0, LangMem, Zep).
- Context management & "context window engineering"; avoiding context rot.

### 5. MCP (Model Context Protocol) — 2026 standard
- What MCP is: an open protocol standardizing how apps expose **tools, resources, and prompts** to LLMs (think "USB-C for AI tools").
- Architecture: **MCP hosts/clients ↔ MCP servers**; transports (stdio, HTTP/SSE).
- Building an MCP **server** (expose your tools/data) and connecting an MCP **client/host**.
- Using existing MCP servers (filesystem, GitHub, databases, search, etc.).
- Why it matters: write a tool once, use it across any MCP-compatible client/agent.

### 6. Multi-Agent Systems
- When multiple agents help (specialization, parallelism, separation of concerns) — and when they just add cost/latency.
- Topologies: supervisor/orchestrator–workers, hierarchical, sequential pipeline, group chat/debate, network.
- Roles, handoffs, shared state/blackboard, message passing.
- Coordination failure modes: loops, cost explosions, error propagation, deadlock.

### 7. Frameworks (build with each at least once)
| Framework | Sweet spot |
|-----------|-----------|
| **LangGraph** | Graph/state-machine control over agents; production-grade, durable, human-in-the-loop, checkpoints |
| **CrewAI** | Role-based crews of agents collaborating on tasks; fast to prototype |
| **AutoGen** (Microsoft) | Conversational multi-agent, group chat, research-y flexibility |
| **OpenAI Agents SDK** | Lightweight agents/handoffs/guardrails with OpenAI stack |
| **LlamaIndex Workflows** | Event-driven agent workflows tied to RAG |
| **Pydantic AI** | Type-safe, Pydantic-native agents |
- Also know: smolagents (HF, code-agents), Semantic Kernel. **Know the primitives so you can build framework-free too.**

### 8. Production Agent Architecture
- **Control & guardrails**: allow-lists, sandboxing, spend/step limits, timeouts, **human-in-the-loop** approval.
- **Observability/tracing**: LangSmith, Langfuse, Arize Phoenix, OpenTelemetry — trace every step, tool call, token, cost.
- **Reliability**: retries, fallbacks, deterministic checkpoints, idempotent tools, state persistence/resume.
- **Evaluation**: trajectory eval (did it take the right steps?), task success rate, cost/latency budgets.
- **Security**: prompt injection via tools/data, excessive agency, confused-deputy, secrets handling.
- Deployment patterns: async job queues, durable execution (Temporal-style), streaming, multi-tenant isolation.

## 🧠 Detailed Explanation

An agent is an LLM placed in a **loop** with **tools**, **memory**, and a **goal**: it reasons about what to do, calls a tool, observes the result, and repeats until done. That's powerful and dangerous — autonomy multiplies both capability and failure modes. The defining lesson of 2026 production agents (echoing Anthropic's widely-cited guidance) is **restraint**: start with the simplest thing that works, prefer *deterministic workflows* with LLM steps where possible, and introduce open-ended agency only where the task genuinely needs it. Every bit of autonomy must be paid for with guardrails, observability, and evals.

**Tool calling** is the action mechanism; **MCP** is becoming the standard way to expose those tools and data so you don't rewrite integrations per app. **Memory** is what makes agents useful across time, but naive memory causes context bloat and "context rot" — manage it deliberately (summarize, retrieve, compact). **Multi-agent** systems help when you have genuinely separable roles or parallelism, but they amplify cost, latency, and coordination bugs — reach for them after a single well-tooled agent proves insufficient.

Frameworks accelerate you, but **LangGraph's** explicit state-machine model is the most production-aligned because it gives you control, durability, checkpoints, and human-in-the-loop — exactly what reliability demands. CrewAI and AutoGen are great for role-based and conversational multi-agent prototyping. Regardless of framework, the senior-level skill is **observability + evaluation of agent trajectories**: you can't ship what you can't trace and measure.

---

## 🛠️ Build 10 Real-World Agent Projects

| # | Project | Type | Key Concepts |
|---|---------|------|--------------|
| **1** | **ReAct research assistant** — answers questions using web search + calculator tools | Single-agent | Tool calling, ReAct loop, citations |
| **2** | **Personal MCP toolbox** — build an MCP server exposing your tools (files, notes, a custom API) and use it from a host | Single-agent + MCP | MCP server/client, tool schemas |
| **3** | **Coding agent** — reads a repo, edits files, runs tests in a sandbox, iterates | Single-agent | Sandboxed code execution, file tools, self-correction |
| **4** | **SQL/data analyst agent** — natural language → SQL → charts, with validation & retries | Single-agent | Text-to-SQL, tool validation, structured output |
| **5** | **Customer-support agent** — RAG-as-a-tool + ticketing actions + human handoff | Single-agent | Agentic RAG, HITL, guardrails |
| **6** | **LangGraph stateful workflow agent** — durable, resumable, with checkpoints + human approval node | Single-agent (graph) | State machine, persistence, HITL |
| **7** | **CrewAI content team** — researcher + writer + editor crew produces a publishable article | Multi-agent | Role-based crew, sequential handoffs |
| **8** | **AutoGen problem-solving group chat** — planner + coder + critic debate to solve a task | Multi-agent | Group chat, debate/critique, termination |
| **9** | **Multi-agent "company"** — supervisor routes to specialist worker agents (research, code, QA, ops) | Multi-agent | Orchestrator–workers, shared state, routing |
| **10** | **Production agent platform** — any of the above hardened: tracing (Langfuse), evals, spend/step limits, async queue, multi-tenant, deployed API | Production | Observability, eval, safety, deployment |

> Each project: trace every run, log cost/latency, and write a README on the architecture + failure modes you hit and fixed. Projects 6–10 are strong **senior** signals.

## 🧪 Practice Exercises
1. Build a bare-metal agent loop (no framework): LLM + 2 tools + while-loop + stop condition.
2. Rebuild it in LangGraph as an explicit state graph with a human-approval node.
3. Add long-term vector memory and show it recalling facts across sessions.
4. Write an MCP server with 3 tools and connect it to an MCP host.
5. Add tracing + a trajectory eval and measure task success rate over 20 tasks.
6. Deliberately trigger a cost/loop runaway, then add step/spend guardrails to stop it.

---

## 📦 Recommended Resources

### Free Courses
- **Hugging Face — "AI Agents Course"** (free, hands-on, smolagents/LangGraph).
- **DeepLearning.AI short courses** (free): *AI Agents in LangGraph*, *Multi AI Agent Systems with crewAI*, *AI Agentic Design Patterns with AutoGen*, *Functions/Tools/Agents with LangChain*, *MCP: Build Rich-Context AI Apps with Anthropic*.
- **LangChain Academy — "Introduction to LangGraph"** (free).
- **Anthropic "Building Effective Agents"** (essay) + cookbook; **MCP docs** (modelcontextprotocol.io).

### Paid Courses
- **Maven** agent-engineering cohorts; **Udemy** LangGraph/CrewAI/AutoGen project courses.

### Books
- *Building Agentic AI Systems* (Packt) and *AI Agents in Action* (Manning) — emerging, practical.
- *LLM Engineer's Handbook* — Iusztin & Labonne (agents + production).

### YouTube Channels
- **LangChain**, **AI Jason**, **Sam Witteveen**, **Dave Ebbelaar**, **Cole Medin** (agents/MCP), **Matthew Berman**, **Tech With Tim** (agent builds).

### Documentation
- [Model Context Protocol](https://modelcontextprotocol.io), [LangGraph](https://langchain-ai.github.io/langgraph/), [CrewAI](https://docs.crewai.com), [AutoGen](https://microsoft.github.io/autogen/), [OpenAI Agents SDK](https://openai.github.io/openai-agents-python/), [Pydantic AI](https://ai.pydantic.dev), [smolagents](https://huggingface.co/docs/smolagents), [Langfuse](https://langfuse.com/docs).

### GitHub Repositories
- [modelcontextprotocol/servers](https://github.com/modelcontextprotocol/servers), [langchain-ai/langgraph](https://github.com/langchain-ai/langgraph), [crewAIInc/crewAI](https://github.com/crewAIInc/crewAI), [microsoft/autogen](https://github.com/microsoft/autogen), [openai/openai-agents-python](https://github.com/openai/openai-agents-python), [huggingface/smolagents](https://github.com/huggingface/smolagents), [NirDiamant/GenAI_Agents](https://github.com/NirDiamant/GenAI_Agents) *(large catalog of agent patterns)*.

---

## 🏁 Phase 8 Milestone
> You can build single- and multi-agent systems with tools, memory, planning, and MCP; orchestrate them in LangGraph/CrewAI/AutoGen; and harden them for production with tracing, evals, guardrails, and human-in-the-loop. ✅

[⬅ Phase 7](07-phase-7-rag.md) · [Back to README](../README.md) · [Next: Phase 9 ➡](09-phase-9-fine-tuning.md)
