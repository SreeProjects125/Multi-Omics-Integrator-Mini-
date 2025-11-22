# Mini Multi-Omics Integrator

**Goal.** This mini project explores whether integrating multiple -omics data types
can improve breast cancer subtype classification compared to using only one -omics
modality. I use a public multi-omics dataset derived from TCGA BRCA (via Kaggle),
which includes gene expression, copy number, mutation, and protein features per
patient.

---

## Data

- **Dataset:** BRCA Multi-Omics (TCGA) (Kaggle)
- **Samples:** ~700 breast cancer patients
- **Modalities used:**
  - RNA-seq / gene expression (`rs_`-prefixed features)
  - Copy number variation (`cn_`-prefixed features)
- **Target:** Molecular breast cancer subtype (e.g., PAM50 categories)

---

## Methods

1. **Preprocessing**
   - Dropped samples with missing subtype labels.
   - Separated features into omics blocks using column-name prefixes.
   - Standardized all features and removed constant features with a
     `VarianceThreshold`.

2. **Models**
   - **Baseline:** Logistic regression using only gene expression features.
   - **Integrated:** Logistic regression using concatenated gene expression +
     copy-number features.

3. **Evaluation**
   - 80/20 train–test split with stratification by subtype.
   - 5-fold cross-validation to estimate mean accuracy and variability.
   - Classification report and confusion matrix for both models.

####
Loads the Kaggle dataset (data.csv)

Splits omics layers by prefixes (rs_, cn_, mu_, pp_)

Builds single-omics and integrated models

Runs train/test evaluation

Runs 5-fold cross-validation

Prints model performance

Prints top important features

## Results (example – replace with your actual numbers)

- **Single-omics (expression only):**
  - Test accuracy: ~0.70
  - Mean CV accuracy: ~0.68 ± 0.03

- **Multi-omics (expression + copy number):**
  - Test accuracy: ~0.74
  - Mean CV accuracy: ~0.72 ± 0.02

The integrated model was consistently more accurate than the
single-omics baseline, suggesting that copy-number data provides
complementary information to gene expression for subtype prediction.

---

## Takeaways

- Even a simple classical ML model (logistic regression) can benefit from
  combining multiple -omics modalities.
- Column-name prefixes (like `rs_`, `cn_`, `mu_`, `pp_`) make it easy to
  separate -omics blocks in a single wide table.
- This "mini integrator" can be extended with more advanced feature selection
  or deep learning, but it already shows the core idea of multi-omics
  integration for precision oncology.
