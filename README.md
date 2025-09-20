ADE Transformers with SHAP
================================

Summary
- Notebooks for ADE detection using biomedical transformers (BioBERT, PubMedBERT, BERT-base) with post‑hoc SHAP explanations.
- Trained/evaluated on ADE Corpus v2; external validation on the SetFit ADE split.
- Datasets are NOT included.

Repository contents
- notebooks/01_finetune_ade_v2.ipynb   (full pipeline: preprocessing → training → threshold tuning → SHAP)
- notebooks/02_external_eval_setfit.ipynb   (external evaluation on SetFit ADE with fixed thresholds)
- requirements.txt, LICENSE, README.md

Setup
1) Create a Python 3.10 environment (example with conda):
   conda create -n ade-ade python=3.10 -y
   conda activate ade-ade
2) Install dependencies:
   pip install -r requirements.txt

Data (not included)
- ADE Corpus v2 (train/val/test; abstracts). Obtain from the original source.
- SetFit ADE split. Load via Hugging Face Datasets.
- Configure paths/loaders in the first cells of each notebook.

Run
1) Start Jupyter:  jupyter notebook
2) Open notebooks/01_finetune_ade_v2.ipynb  (train models, tune thresholds, export metrics and SHAP examples)
3) Open notebooks/02_external_eval_setfit.ipynb  (evaluate on SetFit ADE using fixed thresholds)

Results (reference)
- ADE v2 test:    BioBERT F1 0.8884 AUC 0.9838 | PubMedBERT F1 0.8836 AUC 0.9854 | BERT-base F1 0.8331 AUC 0.9677 | TF-IDF+SVM F1 0.7283 AUC 0.9293
- SetFit external: BioBERT F1 0.9683 AUC 0.9965 | PubMedBERT F1 0.9421 AUC 0.9924 | BERT-base F1 0.8779 AUC 0.9732
- SHAP: token-level attributions highlight ADE terms/causal markers; negations reduce p(ADE).

Reproducibility
- Leak-free 80/10/10 splits, fixed seeds, thresholds tuned on validation and frozen for test/external.

License
- MIT License (see LICENSE).

Contact
-   <mohamad.elhusseiny@lau.edu>

Citation
- El Husseiny M., Ishak D. Benchmarking biomedical transformers for ADE detection with SHAP explanations. 2025. (manuscript)
