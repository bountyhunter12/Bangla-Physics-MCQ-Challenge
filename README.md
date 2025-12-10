# 🧠 Reasoning in Low-Resource Languages  
### **A Case Study on Bengali Physics MCQs with LLMs**


---

## 📌 Introduction

This project explores how modern Large Language Models (LLMs) perform on **Bengali Physics Multiple-Choice Questions (MCQs)** — a low-resource language and a highly structured reasoning task.

The goal is to build an automated **Bengali Physics Question Answering System** that:

- Evaluates small and mid-sized LLMs on structured physics MCQs  
- Demonstrates how **prompt engineering**, **regex-driven decoding**, and **lightweight preprocessing** improve accuracy  
- Works effectively in a constrained, low-resource setting  

---

## 📂 Dataset Description

Competition dataset includes three files:

- **train.csv** — Bengali Physics MCQs with correct answers  
- **test.csv** — Unlabeled MCQs for prediction  
- **sample_submission.csv** — Required format for final output  

### **Column Overview**
| Column | Description |
|--------|-------------|
| `id` | Unique identifier |
| `question` | Bangla physics question |
| `options` | List of four options (A–D) |
| `answer` | Correct option (A/B/C/D) *(only in train.csv)* |

### **Dataset Size**
- **1500 training samples**  
- **200 test samples**  
- Questions cover:
  - Mechanics  
  - Thermodynamics  
  - Optics  
  - Electromagnetism  
  - Modern Physics  

---

## 📊 Dataset Analysis

- All samples are **Bengali-language Physics MCQs**  
- Each instance contains:
  - A conceptual or numerical physics question  
  - Exactly four answer choices  
- Content difficulty ranges from **high school to early undergraduate level**

---

## 🎯 Problem Statement

To build a system that **accurately answers Bengali Physics MCQs** in a **low-resource setting**.

### Key Challenges:
- LLMs struggle with structured MCQs, especially in non-English languages  
- Zero-shot performance varies heavily based on prompt design  
- Bengali-specific formatting and parsing inconsistencies  
- Dataset contains malformed option strings  

---

## ⚙️ Workflow Summary

1. Load and preprocess dataset  
2. Parse option lists & clean broken rows  
3. Apply structured prompt template  
4. Run **Qwen3-14B** for inference  
5. Extract final answer using regex  
6. Generate `submission.csv` for competition  

---

## 🧹 Data Preprocessing

To ensure consistent parsing:

- Fixed malformed option lists using regex  
- Standardized option formatting (A–D always present)  
- Repaired broken input rows with fallbacks  
- Cleaned special characters and spacing  
- Reduced ambiguity for downstream prompt application  

---

## 🧠 Prompt Design

A carefully structured prompt was designed to guide the LLM toward **precise**, **step-based**, and **minimal** output.

### **Prompt Goals**
- Step-by-step reasoning for numerical problems  
- Concise explanations for conceptual ones  
- Output **only** the final answer (single letter A–D)  
- Avoid unnecessary elaboration


---



## 🤖 Model & Inference Setup

### **Model Used**
- **Qwen3-14B** Multilingual LLM  
- Chosen for balance between reasoning ability and resource constraints  

### **Inference Settings**

| Hyperparameter | Value |
|----------------|-------|
| Temperature | 0.05 |
| Max New Tokens | 3000 |
| Top P | 0.90 |
| Top K | 60 |
| Sampling | True |

### **Decoding**
- Applied **two-stage regex extraction** to ensure valid A/B/C/D output  

---

## 📈 Results Analysis

| Method | Accuracy |
|--------|----------|
| **Zero-Shot** | **82.00%** |
| Few-Shot | 62.00% |
| Chain-of-Thought | 74.00% |
| Fine-Tuned (LoRA) | 72.00% |



## 📌 Competition Rules Followed

✔ Only open-source models allowed  
✔ External translation allowed (open-source only)  
✔ No paid/API models (OpenAI, Claude, Gemini not allowed)  
✔ No external physics datasets  
✔ Cloud GPUs permitted  

---

## 👥 Team — Agents_1223

- **Arpita Mallik – CUET**  
- **Faozia Fariha – CUET**

---


