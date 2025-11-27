# 🧠 Clinical Reasoning & Differential Diagnosis with Large Language Models  
### Deakin University — Capstone Project (B)

## 📌 Project Overview
This project develops a clinical reasoning and differential diagnosis pipeline using **Large Language Models (LLMs)**. The system is fine-tuned on both **structured** and **unstructured** clinical datasets to generate diagnostic reasoning from symptoms or clinical notes.

**Input:** Symptoms or clinical case notes  
**Output:** Step-wise diagnostic reasoning and likely diagnoses  

---

## 🚀 Key Achievements

### 🔹 1. Fine-Tuning Multiple LLMs
Successfully fine-tuned and evaluated:
- **Flan-T5**
- **Mistral-7B (QLoRA)**
- **BioBERT / ClinicalBERT**

**GretelAI Fine-Tuning Results:**

| Model      | Base Accuracy | Fine-Tuned Accuracy |
|------------|---------------|----------------------|
| Flan-T5    | 9.87%         | 47.78%               |
| Mistral    | 11.54%        | 97.64%               |
| BioBERT    | 47%           | 96.69%               |

---

### 🔹 2. MIMIC-III Dataset Pipeline
Developed a full preprocessing pipeline:

- SQL joins across `NOTEEVENTS`, `ADMISSIONS`, and `DIAGNOSES_ICD`
- De-identification of patient data  
- Chunking long notes to avoid token overflow  
- Converting output into instruction-tuning format  

---

### 🔹 3. Symptom Extraction Research
Compared:
- **Biomedical NER models**  
- **GPT-4-mini**

**Outcome:** GPT-4-mini produced more accurate symptom lists → final dataset created using GPT-generated symptoms.

---

### 🔹 4. Evaluation Framework
Metrics used:
- **Accuracy** → GretelAI (single-label)
- **Jaccard, Precision, Recall, F1** → MIMIC-III (multi-label)

Mistral achieved **Jaccard = 0.11** on noisy multi-label diagnosis prediction.

---

## 📚 Datasets

### 1. **GretelAI Dataset (Structured)**
- 1,065 cases
- 22 disease types
- Clean symptom → diagnosis pairs

Notebooks:
- `Flan T5 model.ipynb`
- `Fine_Tuning_Mistral.ipynb`
- `BIO_ClinicalBERT.ipynb`

---

### 2. **MIMIC-III Dataset (Unstructured)**
- ~100MB processed notes  
- ~6,000 diagnosis types  
- Real clinical notes containing noise, redundancy, and multi-label complexity  

Notebook:
- `MIMIC III dataset processing.ipynb`

---

## 🤖 Models & Fine-Tuning

### 📌 Models
| Model | Reason |
|-------|--------|
| **Flan-T5** | Instruction-following, structured reasoning |
| **Mistral-7B (QLoRA)** | Powerful decoder-only model, efficient fine-tuning |
| **BioBERT / ClinicalBERT** | Strong biomedical domain understanding |

### 📌 Techniques
- **Supervised Fine-Tuning (SFT)**
- **QLoRA**
- **Instruction Tuning**
- **Custom clinical reasoning prompts**

---

## 🧪 Experimental Results

### ✔️ GretelAI (Single-Label)
High performance after fine-tuning (up to **97%** accuracy).

### ✔️ MIMIC-III (Multi-Label)
Two-step workflow:
1. **Symptom Extraction**
   - BioNER → fragmented, inconsistent  
   - GPT-4-mini → clean, context-aware symptoms  

2. **Diagnosis Prediction**
   - Metrics: Jaccard, Precision, Recall, F1  
   - Best Jaccard so far: **0.11 (Mistral)**  

---

## 📊 Example Output
**Input Symptoms:**  
`fever, flank pain, dysuria`

**Model Reasoning:**  
