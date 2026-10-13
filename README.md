# Machine-learning-
The repository for machine learning practice
Completed the first pass of data preparation on a bank marketing project (7,813 training rows, 47 features). The mistakes taught me more than the steps. 🐍

What I did:
✅ Train/test split first, preprocessing after
✅ "unknown" → NaN → most-frequent imputation (fit on train)
✅ One-hot encoding for categorical columns
✅ Log transformation for skewed numeric columns
✅ Yeo-Johnson for columns with negative values (balance, pdays)
✅ Scaling

Mistakes I made (and fixed):
1️⃣ I fitted the encoder on train but forgot to apply the same transform to X_test. Rule now: fit on train, transform on test.
2️⃣ I ran the log cell twice, which created NaN values. Fix: restored the column from the original data and applied the log once.

What I learned:
🔹 Compare the histogram AND the skew value before choosing a transformation
🔹 One-hot encoding creates the dummy variable trap, so use drop='first' to remove redundant columns
🔹 PowerTransformer (Yeo-Johnson) handles negative values and also standardizes the output by default (mean 0, std 1)

Self-audit of my output (my own rubric, not a benchmark):
About 5.5/10 as-is: fine for a baseline, not final. Reviewing it showed:
⚠️ Imputing "unknown" with the most frequent value turned "never contacted" customers into "previous campaign: failure"
⚠️ "duration" is only known after a call ends, so it is a leakage risk
⚠️ My one-hot columns are still collinear until I apply drop='first'

Next: fix these, then train a baseline model with and without "duration" to measure the leakage effect.

Dataset: Bank Marketing (UCI / Kaggle). Notebook and processed CSV: [GitHub link]

Which preprocessing mistake taught you the most? 👇

#DataScience #MachineLearning #Python #FeatureEngineering #LearningInPublic #AIEngineering
