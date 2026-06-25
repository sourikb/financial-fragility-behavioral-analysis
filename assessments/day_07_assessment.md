# Day 7 – Assessment

## Level 1 – Conceptual Understanding
Explain the split-apply-combine pattern used by groupby and give two 
examples from financial/behavioral economics where this would be 
essential.

**Answer:** In split-apply-combine, the DataFrame is split on the 
basis of one or more attributes, a particular statistic is computed 
on a variable of interest within each group, and the results are 
combined into a single output. Note: groupby shows how a statistic 
*differs across groups*, not "variation in the variable" — that is 
a distinct concept (spread within data).

**Examples:**
- Median household income across U.S. counties
- Average stock market investment by gender

## Level 2 – Applied Thinking
Compute mean and median debt-to-income ratio by education level, 
count households by age_group × education, and identify the 
age_group × education combination with highest mean debt.

**Code:**
```python
import pandas as pd

data = [
    {"household_id": 1, "income": 4000, "debt": 9000, "age_group": "25-34", "education": "high school"},
    # ... (full dataset)
]

df = pd.DataFrame(data)
df["debt_to_income_ratio"] = df["debt"] / df["income"]

print("Mean DTI by education:")
print(df.groupby("education")["debt_to_income_ratio"].mean())

print("Median DTI by education:")
print(df.groupby("education")["debt_to_income_ratio"].median())

print("Household count by age_group × education:")
print(df.groupby(["education", "age_group"])["debt_to_income_ratio"].count())

print("Highest mean debt combination:")
print(df.groupby(["age_group", "education"])["debt"].mean().sort_values(ascending=False).head(1))
```

**Result:** The age 25-34, high school education combination has the 
highest mean debt at $11,500.

## Level 3 – Critical / Analytical Thinking (Three Mechanisms Rule)

**Setup:** A colleague claims that the education-debt relationship 
proves education causes lower debt-to-income ratios, and that 
expanding college access will reduce financial fragility.

**Three mechanisms named:**
- Statistical/Methodological: Measurement validity of debt and 
  income variables (composition of debt types, active vs. passive 
  income)
- Economic/Structural: Income stability and risk (static vs. 
  dynamic income, professional volatility)
- Behavioral/Psychological: Precautionary motive heterogeneity

**Mechanism 1 (Statistical/Methodological):**
The colleague's analysis treats debt and income as homogeneous 
measures, but composition matters. Long-term mortgage debt has 
different fragility implications than high-interest consumer debt. 
Active wage income behaves differently than passive investment 
income. Without knowing the composition of these variables, the 
debt-to-income ratio is not a clean measure across education 
groups. High school households reporting only active income may 
appear more fragile than they are if they also hold significant 
passive income from businesses or inheritance.

**Mechanism 2 (Economic/Structural):**
The analysis assumes income stability is comparable across education 
groups, but this likely varies systematically. Static current 
income misses the dynamics of income trajectory. The small sample 
size compounds this problem. High debt-to-income ratios for the 
25-34 high school subgroup might reflect temporary life-stage 
patterns rather than persistent fragility.

**Mechanism 3 (Behavioral/Psychological):**
Educational attainment is not the sole determinant of debt 
behavior. Precautionary motives vary across households based on 
informal insurance networks, social ties, and subjective risk 
perception.

## Reflection (honest)
Three recurring patterns in mechanism-based reasoning identified 
across Days 4-7:
1. Multiple mechanisms continue to blend within single paragraphs
2. Named mechanisms sometimes do not match the actual argument
3. The "close the loop" step (connecting back to the specific claim 
   being critiqued) is frequently omitted

Starting Day 8, Level 3 will use guided construction: pre-approval 
of mechanism choices and structured paragraph templates. After 
three guided assessments, will return to open-form Level 3 to 
evaluate whether the depth-and-focus skill has consolidated.
