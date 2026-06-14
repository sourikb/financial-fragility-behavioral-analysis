# Day 6 – Assessment

## Level 1 – Conceptual Understanding
Explain when to use each of the four chart types, with examples from 
financial or behavioral economics.

**Answer:**
- **Bar chart:** Compares values across discrete categories. Example: 
  Average monthly expenditure by U.S. census region or by income quintile.
- **Histogram:** Shows the distribution of a single continuous variable. 
  Example: Distribution of monthly average expenditures across U.S. 
  households.
- **Scatterplot:** Reveals the relationship between two variables. 
  Example: Relationship between monthly average expenditures and net 
  worth held in liquid assets across U.S. households.
- **Boxplot:** Compares distributions across groups, showing medians, 
  quartiles, and outliers. Example: Distribution of monthly average 
  expenditures across U.S. households categorized by immigration or 
  citizenship status.

**Reflection note:** Initial answers used non-domain examples (gym 
attendance). Feedback emphasized the importance of always anchoring 
tool understanding in domain-specific examples — this builds the 
reflex of connecting computational skills to applied behavioral 
economics research.

## Level 2 – Applied Thinking
Create a histogram of liquid_assets and a scatterplot of income 
against liquid_assets, both with proper titles and axis labels.

**Code:**
```python
import pandas as pd
import matplotlib.pyplot as plt
import numpy as np

np.random.seed(42)

incomes = np.random.normal(loc=60000, scale=20000, size=200)
liquid_assets = 0.15 * incomes + np.random.normal(loc=0, scale=5000, size=200)

df = pd.DataFrame({
    "income": incomes,
    "liquid_assets": liquid_assets
})

# Histogram
plt.hist(df["liquid_assets"], bins=15)
plt.title("Distribution of Household Liquid Assets")
plt.xlabel("Liquid Assets ($)")
plt.ylabel("Number of Households")
plt.show()

# Scatterplot
plt.scatter(df["income"], df["liquid_assets"])
plt.title("Relationship between Income and Liquid Assets")
plt.xlabel("Household Income ($)")
plt.ylabel("Liquid Assets ($)")
plt.show()
```

**Observation:** The scatterplot shows a positive relationship — 
higher-income households tend to hold more in liquid assets, with 
substantial variation around the trend.

## Level 3 – Critical / Analytical Thinking (Three Mechanisms Rule)

**Setup:** A colleague observes the positive scatterplot relationship 
between income and liquid assets and concludes: "Higher income causes 
households to save more in liquid assets."

**Three mechanisms named before writing (calibration adjustment):**
- Statistical/Methodological: Reverse causation (a specific case of 
  "correlation is not causation")
- Economic/Structural: Endogeneity through wealth-income feedback
- Behavioral/Psychological: Precautionary motive heterogeneity

**Mechanism 1 (Statistical/Methodological) — Reverse causation:**
The colleague's claim assumes income causes liquid asset accumulation, 
but the causal arrow could run the other way. Households with higher 
liquid asset holdings generate capital income (interest, dividends, 
capital gains) that boosts reported income. Without an identification 
strategy that separates wage income from wealth-derived income, the 
direction of causality cannot be established from the scatterplot 
alone.

**Mechanism 2 (Economic/Structural) — Endogeneity through wealth-income 
feedback:**
The income and liquid assets variables are mutually reinforcing. Higher 
liquid asset holdings generate returns that are themselves classified 
as income, especially in datasets like the SCF where capital income 
is included in the income measure. A household with substantial liquid 
holdings may appear higher-income partly because of those holdings — 
not the reverse. Disentangling this requires either an instrumental 
variable for income shocks or a panel structure that separates wage 
income changes from wealth income changes.

**Mechanism 3 (Behavioral/Psychological) — Precautionary motive 
heterogeneity (rewritten with feedback):**
Two households with identical income may hold very different liquid 
asset levels because of unobserved differences in precautionary 
preferences. These preferences depend on household composition, 
near-term expenditure needs, subjective risk perception, and access 
to informal insurance from family networks. A household with more 
dependents, near-term obligations, or strong precautionary concerns 
will hold more liquid assets regardless of income. This means the 
positive scatterplot relationship is partly driven by unobserved 
precautionary preferences correlated with income, not income itself. 
A household with the same income but no precautionary motive would 
appear below the trend; one with strong precautionary motives would 
appear above it.

## Reflection
Day 6 produced visible improvement in mechanism-based reasoning 
compared to Day 5. The key habits being trained are:
1. Naming one specific mechanism per category rather than listing 
   multiple
2. Staying within the chosen category (not mixing structural and 
   behavioral arguments in the same paragraph)
3. Closing the loop by connecting the mechanism back to the specific 
   analysis being critiqued

Continued deliberate practice with the Three Mechanisms Rule and the 
mechanism bank as a reasoning aid.
