# 🏆 Certifications & Portfolio Strategy

[⬅ Back to README](../README.md)

---

## 🎓 Certification Recommendations

> **Reality check:** In AI engineering, **a strong public portfolio > certificates**. Certs help with HR filters, structure your learning, and act as tiebreakers — but no one is hired *because* of a cert. Spend ~80% of effort on projects, ~20% on a couple of well-chosen certs.

### Tier 1 — High value (learning + recognizable)
| Certification | Why | Cost |
|---------------|-----|------|
| **DeepLearning.AI — Deep Learning Specialization** (Coursera) | Best foundational DL credential | Subscription |
| **DeepLearning.AI — Machine Learning Specialization** | Canonical ML intro | Subscription |
| **DeepLearning.AI / AWS — Generative AI with LLMs** | Applied LLM credibility | Subscription |
| **DeepLearning.AI Short Courses** (RAG, agents, evals, fine-tuning) | Free, current, practical — do many | Free |
| **Hugging Face — NLP/LLM & AI Agents courses** (certificates) | Hands-on, respected in GenAI | Free |

### Tier 2 — Cloud certs (valuable if you target that cloud / enterprise)
| Certification | Best for |
|---------------|----------|
| **AWS Certified Machine Learning – Specialty** / **AWS Certified AI Practitioner** | AWS/Bedrock shops |
| **Google Cloud — Professional ML Engineer** / **Generative AI Leader** | GCP/Vertex shops |
| **Microsoft Azure AI Engineer Associate (AI-102)** | Azure/OpenAI-on-Azure shops |
| **NVIDIA — Generative AI / Deep Learning Institute** certs | GPU/infra-heavy roles |
| **Databricks — Generative AI Engineer Associate** | Data+AI platform roles |

### Tier 3 — Nice-to-have / niche
- LangChain Academy (LangGraph) completion, vendor badges (Pinecone/Weaviate), Kaggle competition medals (great signal for ML roles), academic MOOCs (Stanford CS224N/CS229 via YouTube — knowledge, not a cert).

### Certification Strategy
1. Pick **1 foundational** (DL or ML Specialization) + **1 GenAI** (HF or GenAI-with-LLMs).
2. Add **1 cloud cert** matching your target employers' stack.
3. Stack **free DeepLearning.AI short courses** as you hit each phase — they double as learning + credentials.
4. Put certs in a "Certifications" README section and LinkedIn — but let projects lead.

---

## 💼 Portfolio Strategy

Your portfolio is your **proof of work** and the single biggest hiring lever. Build it as you go (don't save it for the end).

### The Anatomy of a Hireable Portfolio
1. **A pinned GitHub profile** with a clean README (who you are, your AI focus, links to flagships).
2. **5–8 polished flagship projects** (see [Projects](15-projects.md)), each with:
   - A **README** stating the problem, **architecture diagram**, key decisions & trade-offs, **evaluation results/metrics**, and limitations.
   - A **live demo** (Hugging Face Spaces / Streamlit Cloud / Vercel) or a 2-min Loom/GIF.
   - Clean, tested code; reproducible setup (`uv`/Docker); clear instructions.
3. **A technical blog** (3–6 posts): "How I built X," "Evaluating RAG with Ragas," "Lessons from a production agent." Teaching proves depth.
4. **OSS contributions** (even small: docs, bug fixes to LangChain/vLLM/HF) — strong credibility signal.
5. **Updated LinkedIn + a one-page resume** with quantified outcomes.

### Flagship Mix That Sells (2026)
| Project type | Why it lands interviews |
|--------------|-------------------------|
| Production **RAG** (hybrid + rerank + **eval**) | The most-requested applied skill |
| **Agent** system (tools, memory, MCP, traced) | The defining 2026 hiring theme |
| **Fine-tuned** model + model card on HF Hub | Shows you go below the API |
| **nano-LLM from scratch** | Rare differentiator; proves true understanding |
| **Productionized** service (Docker, vLLM, monitoring, CI eval gate) | Proves you can ship, not just demo |

### Portfolio Do's and Don'ts
- ✅ **Document trade-offs and eval numbers** — seniors are judged on reasoning, not features.
- ✅ Show **before/after** improvements (e.g., "reranking lifted context precision 0.61→0.83").
- ✅ Keep repos clean: no secrets, good README, tests, `.gitignore`.
- ❌ Don't dump 30 half-finished tutorials. **Quality of a few > quantity.**
- ❌ Don't hide the project behind a wall — make it runnable/viewable in <2 minutes.
- ❌ Don't fake metrics. Be honest about limitations (it reads as senior).

### Visibility Multipliers
- Write a launch post on LinkedIn/X for each flagship; tag the tools used.
- Put demos on **Hugging Face Spaces** (discoverable by recruiters).
- Add a "Now / Learning" section to your profile so people see momentum.
- Engage in communities (see [Resources](20-resources.md)) — referrals beat cold applications.

### 90-Day Portfolio Plan
| Days | Action |
|------|--------|
| 1–30 | Ship 2 beginner + 1 intermediate project; set up GitHub profile README |
| 31–60 | Ship the **Production RAG** flagship + 1 blog post + HF Space demo |
| 61–90 | Ship the **Agent** flagship + productionize one app; polish all READMEs; start applying |

[⬅ Back to README](../README.md) · [Next: Progress Tracking ➡](19-progress-tracking.md)
