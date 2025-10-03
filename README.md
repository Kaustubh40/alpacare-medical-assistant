# alpacare-medical-assistant
# AlpaCare Medical Instruction Assistant

This repository contains the implementation of **Problem 1 — AlpaCare Medical Instruction Assistant**, a fine-tuned language model project designed for **safe, educational-only medical instruction**.

## 📌 Project Overview

* Fine-tunes a **pre-trained LLM (<7B parameters)** on the [`lavita/AlpaCare-MedInstruct-52k`](https://huggingface.co/datasets/lavita/AlpaCare-MedInstruct-52k) dataset.
* Uses **LoRA/PEFT** for efficient training on **Google Colab GPUs**.
* Outputs a **non-diagnostic assistant** that provides clear, helpful medical instruction responses.
* Every response includes a mandatory disclaimer:
  *“This is educational only — consult a qualified clinician.”*

## ✅ Key Features

* **Safe by design**: Blocks diagnostic, prescription, or dosage information.
* **LoRA Adapter Training**: Efficient fine-tuning with low GPU memory requirements.
* **Colab Reproducibility**: End-to-end notebooks for training and inference.
* **Human Evaluation**: ≥30 medically-literate reviewers for qualitative safety checks.
* **Artifacts Only**: Deliverable is the **LoRA adapter** (no hosting of full base model).

## 📂 Repo Structure

```
├─ src/
│  ├─ data_loader.py        # Dataset loading, cleaning, splitting
│  ├─ train_lora.py         # Fine-tuning with LoRA/PEFT
│  └─ inference_demo.py     # Safe inference demo with disclaimer
├─ notebooks/
│  ├─ colab-finetune.ipynb  # Training pipeline (Colab-ready)
│  └─ inference_demo.ipynb  # Inference demo (Colab-ready)
├─ data/                    # Processed dataset splits (jsonl)
├─ lora_adapter/            # Saved LoRA adapter weights (zipped for release)
├─ requirements.txt
├─ README.md
└─ REPORT.pdf               # Concise 6-page report (dataset, model, eval, safety)
```

## 🚀 How to Use

1. **Prepare Dataset**

   ```bash
   python src/data_loader.py --sample 200  # small sample for testing
   python src/data_loader.py               # full 90/5/5 split
   ```
2. **Fine-Tune with LoRA (Colab)**
   Open `notebooks/colab-finetune.ipynb` in Google Colab and run cells end-to-end.
3. **Inference Demo**

   * Run `notebooks/inference_demo.ipynb` in Colab, or
   * Run locally:

     ```bash
     python src/inference_demo.py
     ```

## 📊 Evaluation

* **Automated**: Perplexity + text quality metrics (ROUGE/BERTScore).
* **Human**: ≥30 medically-literate reviews (safety, clarity, helpfulness).

## ⚠️ Safety Notice

This project is **educational and research-only**. It is **not** intended for diagnosis, prescriptions, or clinical decision-making. Always consult a licensed healthcare professional for medical concerns.

---
