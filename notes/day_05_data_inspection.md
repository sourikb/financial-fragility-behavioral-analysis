# Day 5 – Data Inspection and Basic Cleaning

## What I Learned
- Real data is rarely complete; missing values are represented as NaN 
  in pandas
- The presence of NaN forces a column to convert from integer to 
  floating-point type
- df.isna() returns a True/False map of all missing values
- df.isna().sum() returns the count of missing values per column
- Missing values can be handled in three main ways:
  1. Drop rows with any missing value (df.dropna())
  2. Drop entire columns
  3. Impute (fill) missing values with a statistic (df.fillna(df.mean()))
- Each strategy has tradeoffs in terms of sample size, bias, and 
  variance
- df.dtypes shows the data type of each column; checking this is the 
  first step in detecting silent data quality issues

## Simple Example
```python
import pandas as pd
import numpy as np

households = [
    {"income": 5000, "expenses": 3200, "debt": 8000},
    {"income": np.nan, "expenses": 2800, "debt": 5000},
    {"income": 4500, "expenses": np.nan, "debt": 6000}
]

df = pd.DataFrame(households)

# Detect missing values
print(df.isna().sum())

# Strategy 1: drop rows
df_clean = df.dropna()

# Strategy 2: impute with mean
df_imputed = df.fillna(df.mean())

# Inspect data types
print(df.dtypes)
```

## Key Insight
Handling missing data is not a purely methodological choice. It has 
direct economic and behavioral consequences. The decision to drop, 
keep, or impute affects who is in your sample and therefore what 
conclusions you can draw.

Mean imputation in particular collapses variance, biases individual 
observations toward the central tendency, and can be especially 
misleading in behavioral data where missingness is correlated with 
the outcome of interest.

## Course Module Note
This lesson is directly usable as a teaching module in the BSQE 
Research Methods in Quantitative Economics course. The concepts of 
listwise deletion, mean imputation, and missingness patterns form a 
standard component of any applied data analysis curriculum.