# EEG-PreProp-RAG
*An EEG-specific retrieval-augmented generation (RAG) system for automated preprocessing, inspired by CodeRAG-Bench.*

**Project Links**
- 📦 [GitHub Repository](https://github.com/sanvi1855544/eeg_preprop_rag/blob/main/README.md)
- 📄 [NeurIPS-formatted paper](https://github.com/sanvi1855544/eeg_preprop_rag/blob/main/CS_159_report.pdf)
---

## Motivation

EEG preprocessing is a foundational step in BCI research, yet it is often under-standardized, inconsistently documented, and a frequent source of downstream failure.  
This project explores whether retrieval-augmented code generation can be used to produce robust, task-appropriate EEG preprocessing pipelines directly from natural language descriptions.

Originally developed as a final project for **CS 159: Advanced Topics in Machine Learning (Caltech)**, this work adapts the CodeRAG-Bench framework to the EEG domain.

---

## System Overview

The system follows a standard **RAG pipeline**:

- Retrieves domain-specific context from:
  - MNE documentation
  - Public EEG GitHub repositories
  - Curated EEG-related Stack Overflow discussions
- Supports both **canonical** and **open** retrieval strategies
- Generates executable Python preprocessing code
- Evaluates outputs on:
  - Syntax validity
  - Task completion
  - Robustness to noisy or underspecified prompts  
  using GPT 3.5

---

## Retrieval Evaluation

<p align="center">
  <img src="https://github.com/user-attachments/assets/e331122e-42cf-4109-b322-6ccaa34d8f80" width="600"/>
</p>

*Canonical retrieval performance across ranking metrics (NDCG, MRR, Recall, Precision).*

The combined retrieval dataset merges all sources and trades slightly lower raw metric scores for improved **generalizability**, reflecting the diversity of real-world EEG queries and documentation styles.

---

## Code Generation & Post-Processing

<p align="center">
  <img src="https://github.com/user-attachments/assets/6b8841e5-bc68-4c73-a238-8b2734619234" width="600"/>
</p>

Generator outputs are optionally refined using **GPT-4o** as a post-processing step.  
Given a minimally processed EEG signal description, GPT-4o corrects and stabilizes the generated script before execution.

The resulting preprocessing pipeline was applied to a 3-second EEG segment from a real recording, demonstrating the feasibility of **one-shot RAG-based preprocessing**.

---
## Demo Notebooks

- 📘 [Canonical retrieval demo](https://colab.research.google.com/drive/1mrqxg_F7dJNWkNi088yIs3XUYL8661Xv?usp=sharing)
- 📘 [Open retrieval notebook](https://colab.research.google.com/drive/1atFGomyJCbrI2S-9OK4QvcANrtvGu9nM?usp=sharing)
- 📘 [EEG data experiment notebook](https://colab.research.google.com/drive/1JXk2TGh3RdKOL02GBv8yX0XwuqZUNRbu?usp=sharing)
