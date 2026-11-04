# Prostate Cancer Project

Exploratory data analysis and machine learning classification of prostate biopsy outcomes
(Benign vs. Malignant), based on recorded clinical measurements, symptoms, and lifestyle
factors.

## Repository structure

```
data/
  prostate_cancer_prediction.csv   # raw dataset (27,945 patients x 30 columns)
notebooks/
  prostate_cancer_project.ipynb    # full analysis: EDA -> preprocessing -> modeling
requirements.txt                   # Python dependencies
```

## Getting started

```bash
pip install -r requirements.txt
jupyter notebook notebooks/prostate_cancer_project.ipynb
```

## What the notebook covers

1. **Data cleaning** — missing-value handling (defensive; this dataset has none).
2. **Exploratory data analysis** — distributions of all numerical and categorical features,
   and of the target (`Biopsy_Result`).
3. **Bivariate analysis** — Mann-Whitney U tests (numerical features) and Chi-squared tests
   (categorical features) against `Biopsy_Result`.
4. **Feature preparation** — one-hot encoding, train/test split, leakage guard (drops
   post-diagnosis columns such as `Cancer_Stage` and `Treatment_Recommended`).
5. **Baseline models** — Logistic Regression, Decision Tree, Random Forest, SVC, KNN.
6. **Class imbalance handling** — SMOTE oversampling vs. random undersampling.
7. **Feature engineering & selection** — clinical ratios, log transforms, RFE.
8. **Hyperparameter tuning** — SMOTE + XGBoost pipeline tuned with `RandomizedSearchCV`.
9. **Final comparison and conclusion**, including an important caveat about the dataset's
   predictive signal (see the notebook's last section).

## Key finding

The bivariate tests and every modeling approach (baseline, resampled, feature-engineered,
tuned) converge on the same result: ROC-AUC stays near 0.50 regardless of technique. The
EDA suggests `Biopsy_Result` is largely independent of the other recorded columns in this
particular file, which is common for synthetic/practice datasets. The notebook is best used
as a methodology reference (EDA, imbalance handling, feature selection, tuning) rather than
as a source of clinically meaningful predictions — see the notebook's Conclusion section for
details and recommendations for applying this pipeline to real clinical data.

## License

MIT — see [LICENSE](LICENSE).
