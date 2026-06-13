# Day 5 – Assessment

## Level 1 – Conceptual Understanding
Explain NaN and describe two strategies for handling it, with one 
situation where each is appropriate.

**Answer (refined with feedback):**
NaN represents a missing value in a pandas DataFrame. Two common 
strategies are:

1. Imputation (filling missing values with mean, median, mode, or a 
   model-based estimate). Appropriate when missingness is small and 
   appears unrelated to the outcome of interest. The critical 
   criterion is the structure of the missingness, not just the 
   variability in the data.

2. Listwise deletion (dropping rows with any missing value). 
   Appropriate when missingness is small and the dropped observations 
   are unlikely to differ systematically from the kept ones. Sample 
   size matters, but missingness pattern matters more.

The choice between strategies should be driven by the structure of 
the missingness in the data, not by convenience.

## Level 2 – Applied Thinking
Identify missing values, drop incomplete rows, and report the loss.

**Code:**
```python
import pandas as pd
import numpy as np

data = [
    {"household_id": 1, "income": 6000, "expenses": 4500, "debt": 15000, "education": "college"},
    {"household_id": 2, "income": 3500, "expenses": np.nan, "debt": 8000, "education": "high school"},
    {"household_id": 3, "income": np.nan, "expenses": 7000, "debt": 20000, "education": "graduate"},
    {"household_id": 4, "income": 2500, "expenses": 2400, "debt": np.nan, "education": "high school"},
    {"household_id": 5, "income": 4500, "expenses": 3500, "debt": 9000, "education": "college"},
    {"household_id": 6, "income": np.nan, "expenses": 5500, "debt": 18000, "education": "college"}
]

df = pd.DataFrame(data)

# Missing value counts
print(df.isna().sum())

# Drop rows
df_cleaned = df.dropna()
print(df_cleaned)

# Compare shapes
print("Old shape:", df.shape)
print("New shape:", df_cleaned.shape)
```

**Result:** 4 of 6 households were dropped (67% data loss). Only 
households 1 and 5 — both college-educated with complete records — 
survived. The "clean" sample is systematically unrepresentative.

## Level 3 – Critical / Analytical Thinking (Three Mechanisms Rule)

**Initial answer (with self-noted limitations):**
Originally misinterpreted the `education` variable as referring to 
students in those educational stages rather than adults whose highest 
completed education is at that level. Reasoning was reconstructed 
with feedback.

**Refined three-mechanism critique:**

**Statistical / Methodological:**
Dropping high-missingness households does not merely shrink the 
sample — it shrinks it non-randomly. The surviving sample is no 
longer representative of the original population. Inferences 
generalize only to households who responded fully, not to all 
households. This is loss of representativeness, not just sample size.

**Economic / Structural:**
Education is correlated with both income and the propensity to 
disclose income. Higher-educated adults often have more complex 
income structures (bonuses, equity, self-employment, capital gains) 
and may either refuse income disclosure or struggle to report a 
single income figure. Dropping households 3 (graduate) and 6 
(college) for missing income systematically removes high-education 
households from the sample. Conclusions about education and fragility 
are structurally biased.

**Behavioral / Psychological:**
Cognitive load, shame, and financial literacy gaps correlate with 
both fragility and non-response. Adults in financial distress may 
not know their exact debt, may avoid thinking about it, or may feel 
shame disclosing it. Leaving a debt field blank can itself be a 
behavioral signal of fragility. Dropping these households likely 
removes the most fragile members of the sample, causing the 
"cleaned" data to systematically understate fragility. This is 
the MNAR (Missing Not at Random) mechanism applied directly.

## Reflection
Two important lessons emerged today:
1. Misinterpreting a variable definition is one of the most common 
   errors in applied analysis. Always verify variable meaning in 
   the codebook before reasoning about it.
2. Each of the three mechanisms must target a distinctly different 
   distortion. The standard is not three plausible reasons; it is 
   three reasons drawn from different analytical layers.
