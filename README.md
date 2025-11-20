# DL4H-finalproject

Sentence-Level Radiology Classification Reproduction Study

This repository contains the code, data samples, and experimental results for a reproducibility study of sentence-level radiology report classification using Bio_ClinicalBERT, following the modeling component of a secure radiology triage system.

The project trains a 3-class classifier for:
	•	normal
	•	abnormal
	•	uncertain

using publicly available MIMIC-CXR report text and weak rule-based labels.

⸻

## Repository Structure

DL4H-finalproject/
│
├── data/                        → Mini versions of train/val/test used for structure
│   ├── train_mini.csv
│   ├── val_mini.csv
│   └── test_mini.csv
│
├── notebook/                   → Main experiment notebooks
│   ├── baseline_ce.ipynb           (Bio_ClinicalBERT + class weights)
│   ├── baseline_ce_no_weights.ipynb (Ablation 1: no class weights)
│   └── baseline_ce_roberta.ipynb    (Ablation 2: RoBERTa-base)
│
├── results/
│   ├── baseline/               → Results for main experiment
│   │   ├── baseline_loss_curve.png
│   │   ├── test_metrics.csv
│   │   └── test_metrics.json
│   │
│   ├── ablation_no_weights/    → Ablation 1: class weights removed
│   │   ├── no_weights_loss_curve.png
│   │   ├── test_metrics.csv
│   │   └── test_metrics.json
│   │
│   └── ablation_roberta/       → Ablation 2: RoBERTa-base encoder
│       ├── loss_curve_roberta.png
│       ├── test_metrics.csv
│       └── test_metrics.json
│
├── pyhealth_example.py          → Template from original project (not used directly)
├── README.md                    → This file
└── .gitignore

## Experiments

Baseline Model

Bio_ClinicalBERT + class-weighted cross-entropy
	•	Accuracy: 0.9999
	•	Macro F1: 0.9997
	•	Loss: 0.00030

⸻

Ablation 1 — No Class Weights

Same model and hyperparameters as baseline; loss changed to standard cross-entropy.
	•	Accuracy: 0.99987
	•	Macro F1: 0.99920
	•	Loss: 0.00083

Shows a small but measurable degradation without weights.

⸻

Ablation 2 — RoBERTa-base Encoder

Encoder replaced with roberta-base.
	•	Accuracy: 0.99980
	•	Macro F1: 0.99960
	•	Loss: 0.00078

Performs slightly worse than Bio_ClinicalBERT.

⸻

## How to Run

Upload the full dataset CSVs into:
/content/drive/MyDrive/DL4H_data/

Then open any notebook under /notebook/ and run all cells.
Each run automatically exports:
	•	test_metrics.json
	•	test_metrics.csv
	•	loss_curve.png

into the correct results/ subfolder.
