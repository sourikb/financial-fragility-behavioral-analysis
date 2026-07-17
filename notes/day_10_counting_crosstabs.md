# Day 10 – Counting and Cross-Tabulating Categorical Data

## What I Learned
- value_counts() returns the count of each distinct value in a column
- value_counts(normalize=True) returns proportions instead of counts
- Before running value_counts(), identify which columns are categorical:
  - df.dtypes shows declared types (object = text/categorical)
  - df.select_dtypes(include="object") returns just the text columns
  - df.nunique() catches DISGUISED categoricals — survey data often
    stores education, race, region as numeric codes (1, 2, 3), which
    look numeric by dtype but are categorical. A column with 50,000
    rows and 4 distinct values is a category wearing a number's clothing.
- pd.crosstab(df["A"], df["B"]) produces a two-way table:
  - Rows = values of the first variable
  - Columns = values of the second variable
  - Cells = counts at each intersection
- normalize="index" → each row sums to 1 → P(column | row)
- normalize="columns" → each column sums to 1 → P(row | column)
- normalize="all" → entire table sums to 1

## Simple Example
```python
import pandas as pd

df = pd.DataFrame([
    {"education": "high school", "fragile": True},
    {"education": "college", "fragile": False},
    {"education": "high school", "fragile": True},
    {"education": "graduate", "fragile": False}
])

# Reconnaissance
print(df.dtypes)
print(df.nunique())
print(df["education"].value_counts())

# Two-way table: counts
print(pd.crosstab(df["education"], df["fragile"]))

# Risk: what share of each education group is fragile?
print(pd.crosstab(df["education"], df["fragile"], normalize="index"))

# Composition: of fragile households, how is education distributed?
print(pd.crosstab(df["education"], df["fragile"], normalize="columns"))
```

## Key Insight
The distinction between normalize="index" and normalize="columns" is
the distinction between P(fragile | education) and P(education | fragile).
These are different questions with different answers and different
policy uses:

- Row-normalized answers a RISK question: "Of high school households,
  what share are fragile?" Use this to decide WHOM TO TARGET.
- Column-normalized answers a COMPOSITION question: "Of fragile
  households, what share are high school educated?" Use this to decide
  HOW TO SIZE a program.

These can diverge sharply. A group can have the highest fragility rate
(high risk) while representing a small share of all fragile households
(low composition) — simply because the group is small. Confusing the
two is base-rate neglect rendered in table form. A crosstab is Bayes'
conditioning structure displayed as a grid.

Always report both the rate AND the underlying count. "100% of graduate
households are non-fragile" is meaningless when n=2.

## Course Module Note
The risk-vs-composition distinction (P(A|B) vs P(B|A) via crosstab
normalization) is directly usable as a BSQE module, and pairs naturally
with a lecture on base-rate neglect and conditional probability. It is
a rare case where a behavioral bias and a pandas argument illuminate
each other.
