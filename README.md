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

## Reproducibility Commands

### 1. Clone the repository

Run the following commands in your terminal:

git clone https://github.com/GabrielWarner/DL4H-finalproject.git
cd DL4H-finalproject

### 2. Prepare the data directory (Google Drive)

Create the folder:

/content/drive/MyDrive/DL4H_data/

Upload the full dataset files into this folder:
	•	train.csv
	•	val.csv
	•	test.csv

Each file must include the columns:
	•	report_id
	•	sentence_id
	•	text
	•	label

### 3. Run the three experiment notebooks

Open and run all cells in:

notebook/baseline_ce.ipynb
notebook/baseline_ce_no_weights.ipynb
notebook/baseline_ce_roberta.ipynb

Each notebook will:
	•	load data from /content/drive/MyDrive/DL4H_data/
	•	train for 3 epochs
	•	evaluate on the test set
	•	save output files into results/

### 4. Expected output files

After running all three notebooks, your directory will contain:

results/baseline/
• test_metrics.json
• test_metrics.csv
• baseline_loss_curve.png

results/no_weights/
• test_metrics.json
• test_metrics.csv
• baseline_loss_curve_no_weights.png

results/roberta/
• test_metrics.json
• test_metrics.csv
• baseline_loss_curve_roberta.png
