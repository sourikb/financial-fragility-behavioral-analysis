# Day 7 – Group Operations with pandas groupby

## What I Learned
- groupby splits a DataFrame into subgroups based on one or more 
  variables, allowing statistics to be computed within each group
- The pattern is called "split-apply-combine":
  1. Split the data into groups
  2. Apply a function (mean, median, count, etc.) within each group
  3. Combine the results back into a single output
- Single-variable groupby: df.groupby("education")["income"].median()
- Multiple statistics at once: df.groupby("education")["income"].agg([...])
- Multi-variable groupby: df.groupby(["education", "region"])
- Multiple variables and multiple statistics: 
  df.groupby("education").agg({"income": [...], "debt": [...]})
- Empty cells in a multi-variable groupby reveal where data has gaps 
  across combinations
- The pattern of statistics across groups matters as much as the 
  individual values — monotonic, plateau, and non-monotonic 
  relationships each suggest different mechanisms

## Simple Example
```python
import pandas as pd

households = [
    {"income": 5000, "debt": 8000, "education": "high school"},
    {"income": 9000, "debt": 1000, "education": "college"},
    {"income": 12000, "debt": 4000, "education": "graduate"}
]

df = pd.DataFrame(households)

# Single variable, single statistic
print(df.groupby("education")["income"].median())

# Single variable, multiple statistics
print(df.groupby("education")["income"].agg(["mean", "median", "count"]))

# Multiple variables and multiple statistics
print(df.groupby("education").agg({
    "income": ["mean", "median"],
    "debt": ["mean", "median"]
}))
```

## Key Insight
groupby is the workhorse of applied data analysis. Most empirical 
questions in behavioral economics — whether examining heterogeneity 
across demographics, computing summary statistics within subpopulations, 
or comparing outcomes across treatment groups — start with a groupby. 
The conceptual pattern of split-apply-combine is identical to SQL's 
GROUP BY, which makes groupby the natural bridge to SQL.

Equally important is reading the *shape* of grouped results precisely. 
A strictly monotonic relationship, a weakly monotonic one with 
plateaus, and a non-monotonic pattern each suggest different underlying 
mechanisms. Group sizes (the count column) must always be inspected 
before interpreting group statistics.

## Course Module Note
The split-apply-combine pattern, along with its direct mapping to SQL 
GROUP BY, is one of the most central concepts in any applied 
quantitative methods curriculum. This is directly usable as a major 
module in the BSQE Research Methods in Quantitative Economics course.
