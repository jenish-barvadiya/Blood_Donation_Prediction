# Blood_Donation_Prediction

#  Problems Faced with the Blood Donation Dataset

While working with the `Warm_Up_Predict_Blood_Donations` dataset, several issues were identified that could potentially impact model training and evaluation:

###  Irregular Column Naming
- Column names contain **leading/trailing spaces**, which can cause bugs or confusion in code.
- Solution: Applied `df.columns.str.strip()` to clean column names.


###  Redundant Feature
- The feature `Total Volume Donated (c.c.)` is a **linear multiple** of `Number of Donations` (i.e., Volume = Donations × 250).
- This redundancy adds no value and can cause **multicollinearity** issues in some models.
- Solution: Dropped the redundant volume column.

### Class Imbalance
- The target variable `Made Donation in March 2007` is highly **imbalanced**:
  - Only ~24% of the samples are positive cases.
- This can lead to:
  - Biased models favoring the majority class.
  - Inflated accuracy with poor recall for the minority class.
- Suggested Actions:
  - Use **stratified sampling** for train-test split.
  - Apply **resampling techniques** like SMOTE or RandomOverSampler.
  - Prefer metrics like **F1-score**, **AUC**, and **Recall** over plain accuracy.
