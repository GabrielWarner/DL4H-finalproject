# DL4H Final Project: Radiology Sentence-Level Classification

This repository contains the code and notebooks for reproducing the sentence-level radiology classification component from:

**_Integrating ChatGPT into Secure Hospital Networks: A Case Study on Improving Radiology Report Analysis_**

UIUC CS598 DL4H — Fall 2025  
Author: **Gabriel Warner (gsw3)**

---

## Overview

The goal of this project is to reproduce a 3-way radiology sentence classifier that labels sentences as:

- **Normal**
- **Abnormal**
- **Uncertain**

The reproduction focuses only on the sentence-level classification module from the original paper, using **Bio_ClinicalBERT** fine-tuned on weakly labeled MIMIC-CXR text.

Three experimental configurations are included:

- **Baseline:** 3-class weighted cross-entropy  
- **Ablation 1:** Remove class weigts  
- **Ablation 2:** Use RoBERTa-base instead of Bio_ClinicalBERT

---

## Repository Structure

.
├── data/
│   ├── train_mini.csv
│   ├── val_mini.csv
│   └── test_mini.csv
│
├── notebook/
│   ├── baseline_ce.ipynb
│   ├── baseline_ce_no_weights.ipynb
│   └── baseline_ce_roberta.ipynb
│
├── results/
│   ├── baseline/
│   │   ├── baseline_loss_curve.png
│   │   ├── test_metrics.csv
│   │   └── test_metrics.json
│   │
│   ├── ablation_no_weights/
│   │   ├── loss_curve_no_weights.png
│   │   ├── no_weights_loss_curve.png
│   │   ├── test_metrics.csv
│   │   └── test_metrics.json
│   │
│   └── ablation_roberta/
│       ├── loss_curve_roberta.png
│       ├── test_metrics.csv
│       └── test_metrics.json
│
├── pyhealth_example.py
├── README.md
└── .gitignore


---

## Environment (Colab)

All experiments were run in **Google Colab** with pinned versions:

transformers==4.57.2
datasets==2.21.0
evaluate==0.4.3


The exact Python and PyTorch versions are logged inside each notebook.

---

## Data Format

Your CSV files must contain:

report_id
sentence_id
text
label


Place them under `./data/` when running locally.

---

## How to Run

Open notebook in Google Colab and run all cells. Setup cells will install the correct package versions.


