# Day 8 – Sorting and Ranking

## What I Learned
- sort_values() reorders rows based on one or more columns
- ascending=False sorts from highest to lowest
- Selecting top-N records: sort_values(...).head(N)
- Sorting by multiple columns: sort_values(["col1", "col2"], 
  ascending=[True, False]) — the ascending list maps position-by-
  position to the column list
- rank() assigns an explicit rank number to each row based on a column
- With ascending=False in rank(), rank 1 goes to the largest value
- Sorting is not just organization — it is a form of exploratory 
  analysis that reveals structure hidden in unsorted tables

## Simple Example
```python
import pandas as pd

df = pd.DataFrame([
    {"household_id": 1, "income": 4000, "debt": 9000},
    {"household_id": 2, "income": 9000, "debt": 3000},
    {"household_id": 3, "income": 3500, "debt": 14000}
])

df["debt_to_income"] = df["debt"] / df["income"]

# Sort by fragility, most fragile first
df_sorted = df.sort_values("debt_to_income", ascending=False)

# Top 2 most fragile households
top_2 = df.sort_values("debt_to_income", ascending=False).head(2)

# Assign explicit rank
df["fragility_rank"] = df["debt_to_income"].rank(ascending=False)
```

## Key Insight
Sorting and ranking are the computational backbone of any targeting 
or prioritization problem. In policy, this is how limited resources 
are directed to the neediest households. In credit risk, this is how 
applicants are ranked by default probability. The technical operation 
is trivial; the economic judgment lies in choosing the RIGHT variable 
to rank on. A debt-to-income ranking is only as good as debt-to-income 
is a valid proxy for the underlying construct (fragility) — a household 
with a high ratio but large savings may be less fragile than one with 
a lower ratio and no savings.

## Course Module Note
Sorting, ranking, and top-N selection are directly usable as a module 
in the BSQE Research Methods course, especially paired with a 
discussion of targeting criteria and their validity.
