# Day 4 – Assessment

## Level 1 – Conceptual Understanding
What is a DataFrame, and why is it more useful than a list of dictionaries 
for real-world economic data?

**Answer:** A DataFrame organizes data into a structured table with rows 
and columns, making inspection, transformation, and analysis far more 
efficient than working with lists of dictionaries. With dictionaries, 
each element must be accessed individually, and operations require 
explicit loops. pandas operations are vectorized — they apply across 
entire columns at once, which is both faster and cleaner.

## Level 2 – Applied Thinking
Construct a `liquid_to_income` variable, filter households below 0.5, 
and print the result.

**Answer:**
```python
import pandas as pd

households = [
    {"income": 6000, "expenses": 4500, "debt": 15000, "liquid_assets": 2000},
    {"income": 3500, "expenses": 3800, "debt": 8000, "liquid_assets": 500},
    {"income": 12000, "expenses": 7000, "debt": 20000, "liquid_assets": 30000},
    {"income": 2500, "expenses": 2400, "debt": 5000, "liquid_assets": 100}
]

df = pd.DataFrame(households)

# Create new variable
df["liquid_to_income"] = df["liquid_assets"] / df["income"]

# Filter
low_liquid_to_income = df[df["liquid_to_income"] < 0.5]

# Print
print(low_liquid_to_income)
```

**Output:**
   income  expenses   debt  liquid_assets  liquid_to_income
0    6000      4500  15000           2000          0.333333
1    3500      3800   8000            500          0.142857
3    2500      2400   5000            100          0.040000

Households 0, 1, and 3 appear. Household 2 is excluded because its 
liquid-to-income ratio (2.5) exceeds 0.5.

## Level 3 – Critical / Analytical Thinking
Why might using `liquid_to_income < 0.5` as a fragility classifier 
mislead the analysis?

**Answer (expanded with feedback):**

**Statistical / methodological angle:**
The 0.5 threshold is arbitrary and not empirically derived. A meaningful 
cutoff should be calibrated to the population — cost of living, household 
composition, and prior empirical benchmarks. Binary classifications also 
destroy information that a continuous measure preserves and amplify 
measurement error near the boundary.

**Economic / behavioral angle:**
Three distinct mechanisms make the ratio unreliable:
1. Endogeneity — fragility may itself cause low liquidity (households 
   in crisis draw down their buffers), so the cross-sectional ratio 
   cannot establish causal direction.
2. Mental accounting — households may hold liquid assets in 
   psychologically "untouchable" accounts (retirement, education), 
   inflating apparent resilience.
3. Heterogeneity in precautionary motives — identical low ratios may 
   reflect strong informal insurance networks (low fragility) or 
   inability to save (high fragility); the ratio cannot distinguish them.

## Reflection
Initial economic reasoning identified that "other factors matter" but 
did not isolate distinct analytical mechanisms. Feedback emphasized 
the importance of grounding critiques in named mechanisms — endogeneity, 
mental accounting, heterogeneity — rather than general observations.