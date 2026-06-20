# 🔍 Fine-Tuning T5-base for Question Answering (SQuAD)

> **UAS Deep Learning — Group Task | Fine-Tuning HuggingFace Models**

---

## 📋 Overview

This repository implements **fine-tuning T5-base** (Text-to-Text Transfer Transformer) for **generative Question Answering** using the **SQuAD v1.1** dataset. Unlike extractive QA, T5 generates the answer as text, making it a true Seq2Seq approach.

### Task Summary

| Item | Description |
|------|-------------|
| **Task** | Question Answering (Generative) |
| **Architecture** | Encoder-Decoder (Seq2Seq) Transformer |
| **Model** | `t5-base` (220M parameters) |
| **Dataset** | SQuAD v1.1 (Stanford QA Dataset) |
| **Framework** | HuggingFace Transformers + PyTorch |
| **Metrics** | Exact Match (EM), F1 Score |

---

## 🏗️ Repository Structure

```
finetuning-t5-question-answering/
├── README.md
├── requirements.txt
├── notebooks/
│   └── finetuning_t5_squad.ipynb         # Main notebook
└── reports/
    ├── squad_eda.png
    └── training_curves.png
```

---

## 🚀 How to Run

### Google Colab (Recommended — GPU Required)
1. Upload notebook to Colab
2. Enable **GPU runtime** (T4 minimum, A100 preferred for T5-base)
3. Run all cells sequentially

```bash
# Local installation
pip install -r requirements.txt
jupyter notebook notebooks/finetuning_t5_squad.ipynb
```

---

## 📊 T5 Text-to-Text Paradigm

T5 frames **all NLP tasks as text-to-text**:

```
Input  → "question: Who built the Eiffel Tower?  context: The tower was designed by Gustave Eiffel..."
Output → "Gustave Eiffel"
```

**Fine-tuning approach (Seq2Seq):**
```
[Input Text] → T5 Encoder → Cross-Attention → T5 Decoder → [Generated Answer]
```
Loss is computed on the decoder outputs using teacher forcing during training, and beam search is used during inference.

---

## 📈 Results

| Metric | Value |
|--------|-------|
| **Exact Match (EM)** | 62.70% |
| **F1 Score** | 79.53% |
| **Training Epochs** | 3 |
| **Max Input Length** | 512 tokens |
| **Max Target Length** | 64 tokens |

---

## 🗂️ Dataset

- **SQuAD v1.1**: Reading comprehension QA from Wikipedia passages
- **Train**: 87,599 QA pairs | **Validation**: 10,570 QA pairs
- **HuggingFace**: [`rajpurkar/squad`](https://huggingface.co/datasets/rajpurkar/squad)

---

## 👤 Identifikasi

| Item | Info |
|------|------|
| **Nama** | Rakha Primindra Danuatmaja |
| **NIM** | 1103223001 |
| **Kelas** | TK-46-GAB (Deep Learning) |

---

## 📚 References

- Raffel, C., et al. (2020). [Exploring the Limits of Transfer Learning with a Unified Text-to-Text Transformer](https://arxiv.org/abs/1910.10683)
- Rajpurkar, P., et al. (2016). [SQuAD: 100,000+ Questions for Machine Comprehension of Text](https://arxiv.org/abs/1606.05250)
