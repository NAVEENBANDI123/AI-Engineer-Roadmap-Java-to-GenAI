# Phase 3 — Machine Learning

> **Goal:** Master classical ML end-to-end: framing problems, building features, training/evaluating models, and shipping a full pipeline with scikit-learn.
> **Time:** ~4 weeks (20 hrs/wk) · **Prerequisite:** Phase 1 (Python/Pandas) + Phase 2 intuition (LinAlg, Probability, Stats).

[⬅ Phase 2](02-phase-2-mathematics.md) · [Back to README](../README.md) · [Next: Phase 4 ➡](04-phase-4-deep-learning.md)

---

## 🎯 Learning Objectives
- Frame a business problem as a supervised/unsupervised ML problem.
- Build the full ML lifecycle: data → features → train → evaluate → tune → deploy.
- Know when classical ML beats deep learning (often, for tabular data!).
- Avoid the cardinal sins: leakage, bad validation, optimizing the wrong metric.

## 📚 Topics to Study

### 1. ML Foundations & Workflow
- Supervised vs unsupervised vs reinforcement learning.
- Train/validation/test splits; **cross-validation**; data leakage (the #1 silent killer).
- Bias–variance trade-off; over/underfitting; regularization (L1/L2).
- The full pipeline mindset (scikit-learn `Pipeline` + `ColumnTransformer`).

### 2. Supervised Learning — Regression
- Linear & polynomial regression; Ridge, Lasso, ElasticNet.
- Metrics: MAE, MSE, RMSE, R².

### 3. Supervised Learning — Classification
- Logistic regression; k-NN; Naive Bayes; SVM.
- **Decision trees → Random Forests → Gradient Boosting (XGBoost, LightGBM, CatBoost)** — the workhorses of tabular ML and Kaggle.
- Metrics: accuracy, **precision/recall/F1**, ROC-AUC, PR-AUC, confusion matrix, log loss.
- Class imbalance: resampling, class weights, SMOTE, threshold tuning.

### 4. Unsupervised Learning
- Clustering: **k-Means**, hierarchical, DBSCAN.
- Dimensionality reduction: **PCA**, t-SNE, UMAP (great for visualizing embeddings later!).
- Anomaly detection basics.

### 5. Feature Engineering & Data Prep
- Encoding categoricals (one-hot, target/ordinal), scaling/normalization.
- Handling missing data, outliers; datetime & text features.
- Feature selection & importance (permutation importance, SHAP).

### 6. Model Selection & Tuning
- Hyperparameter tuning: grid/random search, **Optuna** (Bayesian).
- Ensembling: bagging, boosting, stacking.
- **Experiment tracking** (intro to MLflow / Weights & Biases — deepened in Phase 11).

## 🧠 Detailed Explanation

Classical ML is *not* obsolete in the LLM era — for **tabular/structured data** (most enterprise data), gradient-boosted trees (XGBoost/LightGBM) routinely beat deep learning while being cheaper, faster, and interpretable. As an AI Engineer you must know when to reach for a 50ms boosted-tree model versus a 2-second LLM call.

The core loop never changes: **define metric → split data correctly → engineer features → train baseline → iterate → validate honestly → deploy → monitor.** Master scikit-learn `Pipeline`s so preprocessing is fit only on training data — this single habit prevents most leakage bugs.

You'll also build the intuition that powers everything later: a model is a function with parameters tuned to minimize a loss on data, evaluated on data it never saw. Embeddings, clustering, and dimensionality reduction (PCA/UMAP) directly resurface when you visualize and debug LLM embeddings in RAG (Phase 7).

## 🧪 Practice Exercises
1. Build a leakage-free scikit-learn `Pipeline` with `ColumnTransformer` for a mixed tabular dataset.
2. Train logistic regression, random forest, and XGBoost on the same task; compare metrics + ROC curves.
3. Tune XGBoost with Optuna; track runs in MLflow.
4. Cluster a dataset with k-Means; pick `k` with the elbow/silhouette method; visualize with PCA.
5. Diagnose & fix a deliberately leaky pipeline.

## 🛠️ Mini Projects
- **Churn prediction** — full pipeline, imbalance handling, SHAP explanations, threshold tuning.
- **House price regression** — feature engineering, regularization, error analysis.
- **Customer segmentation** — clustering + PCA/UMAP visualization + business narrative.

## 🎒 Portfolio Project
**"End-to-End ML Service"** — pick a real tabular dataset, build a leakage-free pipeline, tune with Optuna, track with MLflow, wrap the best model in a **FastAPI** endpoint, containerize with Docker, and write a README with metrics, SHAP plots, and trade-off discussion. This is a complete, hireable artifact.

---

## 📦 Recommended Resources

### Free Courses
- **Andrew Ng — "Machine Learning Specialization"** (DeepLearning.AI/Stanford, audit free) — the canonical starting point.
- **Kaggle Learn** — Intro to ML, Intermediate ML, Feature Engineering (hands-on, short).
- **StatQuest** ML playlists (YouTube).
- **scikit-learn official tutorials**.

### Paid Courses
- **Machine Learning Specialization** (Coursera, for certificate).
- **Udemy: "Machine Learning A-Z"** (broad, project-based).

### Books
- *Hands-On Machine Learning with Scikit-Learn, Keras & TensorFlow* — Aurélien Géron (**the** practical bible; Part I covers this phase).
- *An Introduction to Statistical Learning (ISLP)* — free PDF.
- *Approaching (Almost) Any Machine Learning Problem* — Abhishek Thakur.

### YouTube Channels
- **StatQuest**, **Krish Naik**, **Data School**, **Sentdex**.

### Documentation
- [scikit-learn](https://scikit-learn.org/stable/), [XGBoost](https://xgboost.readthedocs.io), [LightGBM](https://lightgbm.readthedocs.io), [Optuna](https://optuna.org), [MLflow](https://mlflow.org/docs/latest/index.html), [SHAP](https://shap.readthedocs.io).

### GitHub Repositories
- [scikit-learn/scikit-learn](https://github.com/scikit-learn/scikit-learn), [dmlc/xgboost](https://github.com/dmlc/xgboost), [optuna/optuna](https://github.com/optuna/optuna), [ageron/handson-ml3](https://github.com/ageron/handson-ml3).

---

## 🏁 Phase 3 Milestone
> You can take a raw dataset to a tuned, validated, deployed model in a leakage-free pipeline, explain it with SHAP, and serve it via an API. ✅

[⬅ Phase 2](02-phase-2-mathematics.md) · [Back to README](../README.md) · [Next: Phase 4 ➡](04-phase-4-deep-learning.md)
