# Phase 2 — Mathematics for AI

> **Goal:** Build *just enough* math intuition to understand, debug, and innovate on ML/DL — not to become a mathematician. Emphasis on **intuition + code**, not proofs.
> **Time:** ~3–4 weeks (can run in parallel with Phase 1) · **Prerequisite:** High-school algebra; Python (Phase 1) for the code parts.

[⬅ Phase 1](01-phase-1-programming-foundations.md) · [Back to README](../README.md) · [Next: Phase 3 ➡](03-phase-3-machine-learning.md)

---

## 🎯 Learning Objectives
- Read ML papers and library docs without the math being a wall.
- Understand *why* gradient descent, backprop, attention, and loss functions work.
- Translate math into NumPy/PyTorch and back.

> ⚠️ **Pacing advice for the fast track:** If your goal is applied GenAI/RAG/agents jobs, learn the **intuition** here and move on — don't rabbit-hole. Come back for depth when you hit Phases 4, 9, 10. Math is a tool, not a gate.

---

## 📐 Linear Algebra (most important)
The native language of ML — data, embeddings, and model weights are all vectors/matrices/tensors.

**Topics**
- Scalars, vectors, matrices, **tensors**; shapes & broadcasting.
- Vector operations: addition, scaling, **dot product**, norms (L1/L2), unit vectors.
- **Cosine similarity** (the math behind embeddings & RAG retrieval).
- Matrix multiplication (and why shapes must align — the #1 beginner bug).
- Identity/inverse/transpose, rank, linear independence.
- **Eigenvalues/eigenvectors**, **SVD**, PCA (dimensionality reduction).
- Matrix decompositions intuition; projections.

**Why it matters:** A neural network layer is `y = Wx + b` — a matrix multiply plus a vector. Embeddings are vectors; retrieval is similarity between vectors. Attention is scaled dot-products of matrices.

## 📈 Calculus
Powers *learning* — how models improve via gradients.

**Topics**
- Functions, limits, slopes; derivatives & rules (product, quotient, **chain rule**).
- **Partial derivatives & gradients** (multivariable).
- The **chain rule = backpropagation**; computational graphs.
- Maxima/minima, convexity, saddle points.
- Gradient descent & variants (SGD, momentum, Adam) — intuition.

**Why it matters:** Training = minimizing a loss function by following its gradient downhill. Backprop is just the chain rule applied across layers.

## 🎲 Probability
The language of uncertainty, classification, and generative models.

**Topics**
- Sample spaces, events, conditional probability, independence.
- **Bayes' theorem** (foundational for many models & intuition).
- Random variables; discrete vs continuous distributions.
- Key distributions: Bernoulli, Binomial, **Gaussian/Normal**, Poisson, Uniform, Categorical.
- Expectation, variance, covariance.
- **Likelihood, MLE**, cross-entropy (the standard classification/LLM loss).
- Sampling, **softmax & temperature** (how LLMs pick the next token!), KL divergence.

**Why it matters:** LLMs output a probability distribution over the next token; temperature/top-p sampling and cross-entropy loss are pure probability.

## 📊 Statistics
For data understanding, evaluation, and experimentation.

**Topics**
- Descriptive stats: mean, median, mode, variance, std, percentiles, IQR.
- Distributions, skew, outliers; correlation vs causation.
- Sampling, **Central Limit Theorem**, confidence intervals.
- Hypothesis testing, p-values, **A/B testing** (you'll use this to evaluate models/features).
- Bias/variance trade-off; over/underfitting (bridges into Phase 3).
- Evaluation metrics intuition: precision/recall/F1, ROC/AUC.

**Why it matters:** You can't evaluate or trust a model without statistics. A/B testing decides whether your AI feature actually helped.

---

## 🧪 Practice Exercises
1. Implement dot product, matrix multiply, and cosine similarity **from scratch** in NumPy; verify against `np.dot`.
2. Hand-derive the derivative of `f(x)=x²` and of a simple 1-layer network's loss; confirm with `torch.autograd`.
3. Visualize gradient descent minimizing a 2D function; plot the path.
4. Implement softmax with temperature; show how temperature changes the distribution.
5. Run a t-test / simple A/B test on a dataset and interpret the p-value.
6. Do PCA on a dataset and visualize the top-2 components.

## 🛠️ Mini Projects
- **"Math of ML" notebook series** — one notebook each for LinAlg, Calculus, Probability, Stats, each implementing the concept in NumPy with visualizations.
- **Gradient descent visualizer** — animate optimizers (SGD/momentum/Adam) on toy loss surfaces.

## 🎒 Portfolio Project
**"Linear Regression & Logistic Regression from Scratch"** — implement both (forward pass, loss, gradients, training loop) in pure NumPy, no scikit-learn. Compare to scikit-learn for correctness. This demonstrates you truly understand learning, not just `.fit()`.

---

## 📦 Recommended Resources

### Free Courses
- **3Blue1Brown — "Essence of Linear Algebra" & "Essence of Calculus"** (YouTube) — the best intuition-builders in existence. *Watch first.*
- **Khan Academy** — Linear Algebra, Multivariable Calculus, Statistics & Probability (free, thorough).
- **Imperial College "Mathematics for Machine Learning"** (Coursera, free to audit).
- **StatQuest with Josh Starmer** (YouTube) — stats/ML concepts explained simply ("BAM!").

### Paid Courses
- **"Mathematics for Machine Learning and Data Science"** — DeepLearning.AI specialization (Coursera).

### Books
- *Mathematics for Machine Learning* — Deisenroth, Faisal, Ong (**free PDF** at mml-book.github.io).
- *The Elements of Statistical Learning* — Hastie et al. (free PDF; reference, advanced).
- *Think Stats* / *Think Bayes* — Allen Downey (free, code-first).
- *Introduction to Statistical Learning (ISLP, Python edition)* — free PDF, gentler than ESL.

### YouTube Channels
- **3Blue1Brown**, **StatQuest**, **Khan Academy**, **Mathematics for Machine Learning (Imperial)**.

### Documentation / Tools
- [NumPy linear algebra](https://numpy.org/doc/stable/reference/routines.linalg.html), [SymPy](https://www.sympy.org) (symbolic math), [SciPy stats](https://docs.scipy.org/doc/scipy/reference/stats.html).

### GitHub Repositories
- [mml-book/mml-book.github.io](https://github.com/mml-book) materials, ISLP labs, 3Blue1Brown's `manim` for visualization.

---

## 🏁 Phase 2 Milestone
> You can read a model equation (e.g., attention or cross-entropy loss) and explain what each symbol does; you implemented core math in NumPy; you built linear/logistic regression from scratch. ✅

[⬅ Phase 1](01-phase-1-programming-foundations.md) · [Back to README](../README.md) · [Next: Phase 3 ➡](03-phase-3-machine-learning.md)
