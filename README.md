# Wekeza Mixture-of-Recursions Depth Dataset

This repository contains a Jupyter Notebook that generates a small, structured dataset to simulate **"recursive thinking depth"** in a financial question-answering model.  
It is inspired by the paper:

> **Mixture-of-Recursions: Learning Dynamic Recursive Depths for Adaptive Token-Level Computation**  
> Sangmin Bae et al., 2024

---

## 📜 Paper Connection

The MoR paper proposes:
- **Parameter sharing** across recursion steps (efficiency).
- **Adaptive computation** — tokens can be processed at different recursion depths.
- **Token-level depth control** for dynamic reasoning.

Our approach here implements **the dataset side** of that idea:
- We tag each question with a `<depth>` token.
- Depth determines how much reasoning detail the model provides:
  - `<depth=1>` → short, direct answer.
  - `<depth=2>` → step-by-step reasoning (Chain-of-Thought).
  - `<depth=3>` → detailed analysis with references.

This allows Wekeza LLM to **simulate recursive depth control** during training/inference, without modifying the model architecture.

---

## 📂 Files

- **`wekeza_depth_dataset.jsonl`** → Generated dataset (JSONL format).
- **`depth_dataset_generator.ipynb`** → Notebook that creates the dataset.

---

## 🛠 How It Works

1. **Seed Examples**:  
   Provide seed Q&A in three versions:
   - Short answer
   - Step-by-step reasoning
   - Detailed analysis

2. **Depth Formatting**:  
   Each question is prepended with a `<depth>` tag:
   ```text
   <depth=1> How do I invest in a Kenyan Money Market Fund?
