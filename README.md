# ADE Transformers with SHAP

Benchmarking **biomedical transformers** for adverse drug event (ADE) detection on **ADE Corpus v2**, with **post-hoc SHAP** explanations and **external validation** on the SetFit ADE split.

> Notebooks only (no datasets). Reproducible end-to-end: preprocessing → training → threshold tuning → evaluation → SHAP.

---

## 📦 Repository contents
notebooks/
01_finetune_ade_v2.ipynb # full pipeline: preprocessing → training → tuning → SHAP
02_external_eval_setfit.ipynb # external evaluation on SetFit ADE (no retraining; fixed thresholds)
requirements.txt
LICENSE
README.md


---

## ⬇️ Get the notebooks
**Option A — Download ZIP**
1. Click the green **Code** button → **Download ZIP**.
2. Unzip locally.

**Option B — Clone**
```bash
git clone https://github.com/<your-username>/ade-transformers-shap.git
cd ade-transformers-shap

🛠️ Setup

Create a fresh Python 3.10 environment and install dependencies:

# with conda (example)
conda create -n ade-ade python=3.10 -y
conda activate ade-ade

# install packages
pip install -r requirements.txt


requirements.txt (pinned): torch, transformers, datasets, evaluate, scikit-learn, pandas, numpy, matplotlib, seaborn, shap.

🧪 Data

ADE Corpus v2 (train/val/test; abstracts).

SetFit ADE split (external evaluation).

Datasets are NOT included. Obtain ADE v2 from its original source; load SetFit ADE via Hugging Face Datasets. Configure paths/loaders in the first cells of each notebook.

▶️ Run

Launch Jupyter:

jupyter notebook


Open notebooks/01_finetune_ade_v2.ipynb

Preprocess → train BioBERT / PubMedBERT / BERT-base + TF-IDF baselines

Tune decision thresholds on validation (max F1)

Export metrics/plots/SHAP examples to results/ (paths shown in the notebook)

Open notebooks/02_external_eval_setfit.ipynb

Loads the fixed thresholds from step 2

Evaluates on SetFit ADE without retraining

📊 Results (summary)

Numbers may vary slightly; these are the reference values from the manuscript.

ADE v2 (held-out test; thresholds tuned on validation)

BioBERT — F1 0.8884, AUC 0.9838

PubMedBERT — F1 0.8836, AUC 0.9854

BERT-base — F1 0.8331, AUC 0.9677

TF-IDF + LinearSVM — F1 0.7283, AUC 0.9293

SetFit ADE (external; same thresholds, no retraining)

BioBERT — F1 0.9683, AUC 0.9965

PubMedBERT — F1 0.9421, AUC 0.9924

BERT-base — F1 0.8779, AUC 0.9732

SHAP explanations
Token-level SHAP highlights align with clinical intuition: ADE lexemes and causal markers (e.g., rash, nausea, after) increase 
𝑝
(
𝐴
𝐷
𝐸
)
p(ADE); negations/ameliorative phrases (no adverse effects, resolved) decrease it.

🔁 Reproducibility

Leak-free 80/10/10 splits (hash-checked)

Fixed random seeds

Thresholds tuned on validation and frozen for test & external eval

Notebooks save metrics, confusion matrices, ROC/PR curves, and SHAP examples

🧑‍⚖️ License

Code released under the MIT License (see LICENSE).

📣 Cite

If you use this repository, please cite:
El Husseiny M., Ishak D. Benchmarking biomedical transformers for ADE detection with SHAP explanations. 2025. (manuscript)

✉️ Contact

Questions or issues? Open a GitHub Issue or email your.email@domain
.

::contentReference[oaicite:0]{index=0}
