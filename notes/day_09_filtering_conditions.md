# Day 9 – Filtering with Multiple Conditions

## What I Learned
- Multiple conditions are combined with & (AND) and | (OR)
- Each condition MUST be wrapped in its own parentheses, because & and 
  | have higher operator precedence than > and <; without parentheses, 
  Python evaluates the wrong thing and throws an error
- & (AND) requires all conditions to be True — produces a narrower set
- | (OR) requires any condition to be True — produces a broader set
- The OR set is always at least as large as the AND set; if they are 
  equal, the conditions overlap perfectly in that data (worth 
  investigating, not assuming)
- A filter can be turned into a stored flag: 
  df["flag"] = (condition1) & (condition2)
- A boolean flag column can be quantified: .sum() counts True values, 
  .mean() gives the proportion True

## Simple Example
```python
import pandas as pd

df = pd.DataFrame([
    {"household_id": 1, "income": 5000, "liquid_savings": 500, "debt": 12000},
    {"household_id": 2, "income": 8000, "liquid_savings": 15000, "debt": 6000},
    {"household_id": 3, "income": 3000, "liquid_savings": 200, "debt": 9000}
])
df["debt_to_income"] = df["debt"] / df["income"]

# Combine two conditions with AND
df["fragile_flag"] = (df["debt_to_income"] > 2.0) & (df["liquid_savings"] < 1000)

# Quantify
print("Number fragile:", df["fragile_flag"].sum())
print("Proportion fragile:", df["fragile_flag"].mean())
```

## Key Insight
The choice between AND and OR when defining fragility is not a technical 
decision — it is a policy and values decision. AND produces a narrow, 
high-confidence group (fewer false positives, but misses households 
severely fragile on a single dimension). OR produces a broad, inclusive 
group (catches more at-risk households, but includes some less fragile 
ones). An applied economist's value lies in framing this tradeoff for 
decision-makers, not in writing the code.

Equally important: a filter is a temporary view, but a flag is a 
permanent variable. Once fragility is stored as a column, it can be 
counted, turned into a rate, grouped, cross-tabulated, and ultimately 
modeled as an outcome variable. The capstone's outcome variable will 
be exactly this kind of constructed multi-condition flag.

## Course Module Note
Boolean logic for multi-condition filtering, the parentheses 
precedence rule, and the AND/OR policy tradeoff are directly usable 
as a module in the BSQE Research Methods course.
