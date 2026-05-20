<div align="center">

# 🐕 The Not-So-Secret Life of Dogs

### Fine-Grained Dog Breed Classification via Transfer Learning

[![Python](https://img.shields.io/badge/Python-3.10%2B-blue?style=flat-square&logo=python)](https://python.org)
[![PyTorch](https://img.shields.io/badge/PyTorch-2.x-EE4C2C?style=flat-square&logo=pytorch)](https://pytorch.org)
[![Kaggle](https://img.shields.io/badge/Kaggle-Notebook-20BEFF?style=flat-square&logo=kaggle)](https://kaggle.com)
[![License](https://img.shields.io/badge/License-MIT-green?style=flat-square)](LICENSE)

> 🧠 A deep learning study comparing ResNet-50 and EfficientNet-B3 on 120-class dog breed classification using the Stanford Dogs Dataset — featuring transfer learning, augmentation ablation, and Grad-CAM interpretability.

</div>

---

## 📋 Contents

- [About the Project](#-about-the-project)
- [Key Results](#-key-results)
- [Dataset](#-dataset)
- [Methodology](#-methodology)
- [Repo Structure](#-repo-structure)
- [Getting Started](#-getting-started)
- [Results](#-results)
- [Team](#-team)

---

## 🔍 About the Project

Fine-grained visual classification (FGVC) is among the most challenging tasks in computer vision. Unlike coarse-grained recognition, FGVC requires discriminating between visually similar sub-categories — in this case, 120 dog breeds that share near-identical body shapes but differ in subtle features like coat texture, ear shape, and facial structure.

This project investigates two state-of-the-art CNN architectures — **ResNet-50** and **EfficientNet-B3** — both pre-trained on ImageNet-1K and fine-tuned using a structured two-stage protocol. Augmentation strategies were ablated across five configurations, and all results were validated across three independent random seeds for statistical robustness.

---

## 🏆 Key Results

| Model | Top-1 Accuracy | Macro-F1 | Top-5 Accuracy |
|---|---|---|---|
| **ResNet-50** | **88.58% ± 0.07%** | **88.00%** | ~98% |
| EfficientNet-B3 | 80.88% ± 0.42% | ~80% | ~96% |

- ✅ ResNet-50 superiority confirmed via paired t-test (p = 0.0012)
- ✅ Dataset integrity: zero corrupt images across all 20,580 samples
- ✅ Best single run: 88.88% (ResNet-50, no random rotation)

---

## 📦 Dataset

**Stanford Dogs Dataset** — Khosla et al., 2011

- 20,580 JPEG images across **120 dog breeds**
- Perfectly balanced: exactly 100 training samples per class
- Stratified train / val / test splits with reproducible seeds

---

## ⚙️ Methodology

**Work Packages:**

- `WP1` — Dataset download, extraction, and integrity verification
- `WP2` — Preprocessing pipeline: augmentation transforms and stratified splits
- `WP3` — ResNet-50 baseline with two-stage fine-tuning across 3 seeds
- `WP4` — EfficientNet-B3 training and augmentation ablation study (5 configs)
- `WP5` — Evaluation: Top-1/5, macro-F1, confusion matrices, Grad-CAM

**🔁 Two-Stage Fine-Tuning Protocol:**
1. Freeze backbone — train classifier head only
2. Unfreeze all layers — low-LR full fine-tuning

**🔬 Augmentation Ablation:** Random crop, horizontal flip, color jitter, random rotation — individually removed to isolate contribution.

**👁️ Interpretability:** Grad-CAM visualizations on the final conv layer to validate model attention on discriminative breed features.

---

## 📁 Repo Structure

```
the-not-so-secret-life-of-dogs/
│
├── notebook/
│   └── the-not-so-secret-life-of-dogs.ipynb   # Main training + evaluation notebook
│
├── report/
│   └── CV_Project_Report.docx                  # Full project report
│
├── synopsis/
│   └── CV_Assignment-3_Synopsis.docx           # Project synopsis
│
├── presentation/
│   └── The-Not-So-Secret-Life-of-Dogs.pptx     # Slide deck
│
├── README.md
└── requirements.txt
```

---

## 🚀 Getting Started

**Requirements**

```bash
pip install torch torchvision grad-cam scipy seaborn scikit-learn
```

**Run the Notebook**

Open `notebook/the-not-so-secret-life-of-dogs.ipynb` in Kaggle or Google Colab (T4 GPU recommended).

```
⏱️ Estimated runtime: ~2.5 hours on a T4 GPU
```

The notebook auto-detects the runtime environment (Colab / Kaggle / local) and downloads the Stanford Dogs Dataset automatically.

---

## 📊 Results

**Augmentation Ablation (ResNet-50, single run):**

| Config | Top-1 Accuracy |
|---|---|
| Full augmentation (baseline) | 88.58% |
| No random rotation | **88.88%** |
| No color jitter | 88.10% |
| No horizontal flip | 87.90% |
| Minimal augmentation | 86.40% |

Removing random rotation slightly improved accuracy, suggesting mild overfitting from angular diversity under short training runs — an interesting finding worth exploring in future work.

---

## 👥 Team Members

- **Mohid Arshad** — [GitHub](https://github.com/akamohid) | [LinkedIn](https://www.linkedin.com/in/akamohid/)  
- **Mohammad Hasnain** — [LinkedIn](https://www.linkedin.com/in/mohammad-hasnain-3670452a7/)  
- **Tahir Mehmood** — [LinkedIn](https://www.linkedin.com/in/tahir-mehmood-622a412a0/)

---

<div align="center">
Made with 🧪 curiosity, ☕ caffeine, and 20,580 dog photos.
</div>
