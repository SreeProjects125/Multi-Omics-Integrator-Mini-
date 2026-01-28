This mini project explores whether integrating multiple -omics data types
can improve breast cancer subtype classification compared to using only one -omics
modality. I use a public multi-omics dataset derived from TCGA BRCA (via Kaggle),
which includes gene expression, copy number, mutation, and protein features per
patient.

Dataset:BRCA Multi-Omics (TCGA) (Kaggle)
700 breast cancer patients
- **Modalities used:**
  - RNA-seq / gene expression 
  - Copy number variation 

   - Dropped samples with missing subtype labels.
   - Separated features into omics blocks using column-name prefixes.
   - Standardized all features and removed constant features with a
     `VarianceThreshold`.

 Logistic regression using only gene expression features.
  Logistic regression using concatenated gene expression + copy-number features.
   - 80/20 train–test split with stratification by subtype.
   - 5-fold cross-validation to estimate mean accuracy and variability.
   - Classification report and confusion matrix for both models.

- **Single-omics
  - Test accuracy: ~0.70
  - Mean CV accuracy: ~0.68 ± 0.03

- **Multi-omics 
  - Test accuracy: ~0.74
  - Mean CV accuracy: ~0.72 ± 0.02

## Takeaways
- Even a simple classical ML model (logistic regression) can benefit from
  combining multiple -omics modalities.
- This "mini integrator" can be extended with more advanced feature selection
  or deep learning, but it already shows the core idea of multi-omics
  integration for precision oncology.
