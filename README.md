# DL4H-finalproject

Sentence-Level Radiology Classification Reproduction Study

This repository contains the code, data samples, and experimental results for a reproducibility study of sentence-level radiology report classification using Bio_ClinicalBERT, following the modeling component of a secure radiology triage system.

The project trains a 3-class classifier for:
	•	normal
	•	abnormal
	•	uncertain

using publicly available MIMIC-CXR report text and weak rule-based labels.

## Experiments

Baseline Model

Bio_ClinicalBERT + class-weighted cross-entropy
	•	Accuracy: 0.9999
	•	Macro F1: 0.9997
	•	Loss: 0.00030

Ablation 1 — No Class Weights

Same model and hyperparameters as baseline; loss changed to standard cross-entropy.
	•	Accuracy: 0.99987
	•	Macro F1: 0.99920
	•	Loss: 0.00083

Shows a small but measurable degradation without weights.

Ablation 2 — RoBERTa-base Encoder

Encoder replaced with roberta-base.
	•	Accuracy: 0.99980
	•	Macro F1: 0.99960
	•	Loss: 0.00078

Performs slightly worse than Bio_ClinicalBERT.

## How to Run

Upload the full dataset CSVs into:
/content/drive/MyDrive/DL4H_data/

Then open any notebook under /notebook/ and run all cells.
Each run automatically exports:
	•	test_metrics.json
	•	test_metrics.csv
	•	loss_curve.png

into the correct results/ subfolder.
