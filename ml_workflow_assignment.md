
# ML Workflow Assignment

## Task 1 — Label and Data Leakage Identification

**Label column:** `repeat_purchase_flag`  
This is the target variable the model is trying to predict — it directly encodes the outcome (repeat purchase within 30 days) that we want to learn from all other features.

**Data leakage column:** `discount_used_on_repeat_order`  
This column contains information that is only known *after* the repeat purchase has already occurred, meaning it would not be available at prediction time and would cause the model to appear more accurate than it actually is in production.

---

## Task 2 — Missing ML Workflow Steps

### Step 1 — Exploratory Data Analysis (EDA)

Before training any model, EDA should be performed to understand the distribution of each feature, check for missing values, spot outliers, and examine class balance in the target variable. In this dataset, `repeat_purchase_flag` is likely imbalanced — most customers probably do *not* make a repeat purchase within 30 days — and training a gradient boosting model on imbalanced data without addressing it first will produce a model that is biased toward predicting the majority class.

### Step 2 — Feature Engineering and Baseline Model

A simple baseline model (such as logistic regression or even a majority-class classifier) should be established before reaching for gradient boosting. This gives a performance floor to compare against, ensures the features are correctly scaled and encoded, and often reveals that a simpler model is sufficient. Jumping straight to a complex model makes it impossible to know whether the added complexity is actually buying anything, and it makes debugging much harder if something goes wrong.
