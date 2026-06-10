# Day 4 – Introduction to pandas and DataFrames

## What I Learned
- pandas is the standard Python tool for handling tabular data
- A DataFrame is a structured table with rows and columns, similar to 
  a spreadsheet
- A list of dictionaries can be converted directly into a DataFrame
- DataFrames have built-in tools for inspection: .shape, .columns, .describe()
- Columns are accessed with df["column"] and support methods like 
  .mean(), .max(), .min()
- Rows can be filtered using conditions: df[df["debt"] > 5000]
- A condition like df["debt"] > 5000 returns True/False for every row; 
  pandas keeps only the True rows
- New variables can be created in a single line: 
  df["debt_to_income"] = df["debt"] / df["income"]

## Simple Example
```python
import pandas as pd

households = [
    {"income": 5000, "expenses": 3200, "debt": 8000},
    {"income": 2000, "expenses": 2500, "debt": 12000},
    {"income": 9000, "expenses": 4000, "debt": 1000}
]

df = pd.DataFrame(households)
df["debt_to_income"] = df["debt"] / df["income"]
print(df)
```

## Key Insight
pandas allows the same logic we developed manually with loops and 
dictionaries to be executed in single, vectorized operations across 
thousands of households. Constructing new variables from existing ones 
(feature engineering) is the foundation of applied behavioral data 
analysis and is central to building the financial fragility measure 
in the capstone project