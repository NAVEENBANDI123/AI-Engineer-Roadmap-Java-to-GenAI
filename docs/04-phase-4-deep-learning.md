# Phase 4 — Deep Learning (PyTorch + TensorFlow)

> **Goal:** Understand neural networks deeply and become fluent in **PyTorch** (primary) and **TensorFlow/Keras** (secondary), through to the **Transformer** that powers all modern AI.
> **Time:** ~5 weeks (20 hrs/wk) · **Prerequisite:** Phase 2 (calculus/linalg intuition) + Phase 3 (ML workflow).

[⬅ Phase 3](03-phase-3-machine-learning.md) · [Back to README](../README.md) · [Next: Phase 5 ➡](05-phase-5-generative-ai.md)

---

## 🎯 Learning Objectives
- Understand forward pass, loss, **backpropagation**, and optimization from first principles.
- Build, train, debug, and tune neural networks in PyTorch.
- Know the major architectures: MLP, CNN, RNN/LSTM, and the **Transformer**.
- Use transfer learning and GPUs effectively (Colab/Kaggle).

## 📚 Topics to Study

### 1. Neural Network Foundations
- Perceptron → multilayer perceptron (MLP); layers, weights, biases.
- **Activation functions**: ReLU, GELU, sigmoid, tanh, softmax.
- **Loss functions**: MSE, cross-entropy.
- **Backpropagation** (chain rule across layers) + autograd.
- **Optimizers**: SGD, momentum, RMSProp, **Adam/AdamW**; learning rate schedules.
- Initialization, vanishing/exploding gradients, batch/layer normalization.
- Regularization: **dropout**, weight decay, early stopping, data augmentation.

### 2. PyTorch (your primary framework)
- Tensors, autograd, `nn.Module`, `Dataset`/`DataLoader`.
- The training loop (forward → loss → `backward()` → `optimizer.step()`).
- GPU/`device` management, mixed precision (`autocast`), checkpoints.
- `torchvision`/`torchaudio`; **PyTorch Lightning** for clean training code.

### 3. TensorFlow / Keras (secondary, know it)
- Keras Sequential & Functional API; `model.compile/fit/evaluate`.
- `tf.data` pipelines; SavedModel format; TensorBoard.
- When teams use TF (often production/legacy, TFLite, mobile/edge).

### 4. Core Architectures
- **CNNs** — convolution, pooling, image classification; ResNet, EfficientNet.
- **RNNs / LSTM / GRU** — sequences; their limitations (why attention won).
- **Sequence-to-sequence**, encoder–decoder, the attention mechanism.
- **The Transformer** — self-attention, multi-head attention, positional encodings, feed-forward blocks, residual connections + layer norm. *(Deep dive continues in Phase 5 & 10.)*

### 5. Practical Deep Learning
- **Transfer learning & fine-tuning** pretrained models.
- Handling overfitting; hyperparameter tuning; experiment tracking (W&B).
- Reading benchmarks; debugging training (loss not decreasing, NaNs).

## 🧠 Detailed Explanation

Deep learning is "differentiable programming": you define a network of operations, define a loss, and let autograd compute gradients so an optimizer can nudge millions of parameters downhill. PyTorch makes this concrete and is the **research + industry default in 2026** — its define-by-run graph and ecosystem (Hugging Face, vLLM, Lightning) mean almost everything you'll touch later is PyTorch-first. Learn TensorFlow/Keras enough to be productive on teams that use it (mobile/edge, some enterprises).

The single most important destination of this phase is the **Transformer**. CNNs and RNNs are worth understanding for intuition and for non-LLM tasks, but **attention is all you need** — self-attention lets a model weigh every token against every other token in parallel, which is *why* LLMs scaled. By the end of this phase you should be able to read the original "Attention Is All You Need" paper and explain each block. Karpathy's "Let's build GPT" video + nanoGPT is the bridge into Phase 10.

> 🖥️ **Compute:** Use free **Google Colab** / **Kaggle** GPUs for this phase. You do not need to buy a GPU yet.

## 🧪 Practice Exercises
1. Build an MLP **from scratch in NumPy** (manual backprop) for MNIST; then rebuild in PyTorch and compare.
2. Train a CNN on CIFAR-10; apply data augmentation + transfer learning (ResNet); track in W&B.
3. Build an LSTM text classifier; observe where it struggles on long sequences.
4. Implement single-head self-attention from scratch; then multi-head.
5. Port one model from PyTorch to Keras to feel the API differences.

## 🛠️ Mini Projects
- **Image classifier web app** — fine-tune a pretrained CNN, serve via FastAPI + simple UI.
- **Sentiment analyzer** — RNN/LSTM vs a Transformer baseline; compare.
- **From-scratch micro-autograd** — tiny reverse-mode autodiff engine (à la `micrograd`).

## 🎒 Portfolio Project
**"Vision Transformer Fine-Tuner"** — fine-tune a pretrained image or text model on a custom dataset with PyTorch Lightning, log experiments to W&B, export the model, and deploy an inference API + Gradio/Streamlit demo. Document architecture choices, training curves, and results.

---

## 📦 Recommended Resources

### Free Courses
- **Andrew Ng — "Deep Learning Specialization"** (DeepLearning.AI, audit free).
- **fast.ai — "Practical Deep Learning for Coders"** (free, top-down, project-first).
- **Andrej Karpathy — "Neural Networks: Zero to Hero"** (YouTube; build micrograd → GPT). *Essential.*
- **MIT 6.S191 Introduction to Deep Learning** (free lectures).

### Paid Courses
- **Deep Learning Specialization** (Coursera, for certificate).
- **Udacity / Udemy PyTorch** project courses.

### Books
- *Hands-On Machine Learning* (Géron) — Part II (DL with Keras/TF).
- *Deep Learning with PyTorch* — Stevens, Antiga, Viehmann (free PyTorch edition).
- *Dive into Deep Learning (d2l.ai)* — free, interactive, both frameworks.
- *Deep Learning* — Goodfellow, Bengio, Courville (free, theory reference).

### YouTube Channels
- **Andrej Karpathy**, **3Blue1Brown** (neural nets series), **Aladdin Persson** (PyTorch), **Sentdex**.

### Documentation
- [PyTorch](https://pytorch.org/docs/stable/index.html) + [tutorials](https://pytorch.org/tutorials/), [PyTorch Lightning](https://lightning.ai/docs/pytorch/stable/), [Keras](https://keras.io), [TensorFlow](https://www.tensorflow.org/learn), [Weights & Biases](https://docs.wandb.ai).

### GitHub Repositories
- [karpathy/nn-zero-to-hero](https://github.com/karpathy/nn-zero-to-hero), [karpathy/micrograd](https://github.com/karpathy/micrograd), [pytorch/pytorch](https://github.com/pytorch/pytorch), [Lightning-AI/pytorch-lightning](https://github.com/Lightning-AI/pytorch-lightning), [d2l-ai/d2l-en](https://github.com/d2l-ai/d2l-en).

---

## 🏁 Phase 4 Milestone
> You can build/train/debug neural nets in PyTorch, use transfer learning on a GPU, implement self-attention from scratch, and explain the Transformer architecture block-by-block. ✅

[⬅ Phase 3](03-phase-3-machine-learning.md) · [Back to README](../README.md) · [Next: Phase 5 ➡](05-phase-5-generative-ai.md)
