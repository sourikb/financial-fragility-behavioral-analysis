# Day 8 – Assessment

## Level 1 – Conceptual Understanding
Difference between sort_values() and rank(), with examples.

**Answer:** sort_values() reorders the rows of the DataFrame based on 
one or more columns. rank() assigns a rank number to each row based 
on a column without moving the rows. Use sort_values() when you want 
to see data in order (e.g., a ranked report table). Use rank() when 
you want to store each row's position as a variable for later 
filtering or modeling.
- sort_values example: order households ascending by savings.
- rank example: assign fragility ranks using a fragility index.

## Level 2 – Applied Thinking
Construct months_of_buffer, rank with rank 1 = most fragile, sort 
most-to-least fragile.

**Code:**
```python
import pandas as pd

data = [
    {"household_id": 1, "income": 5000, "liquid_savings": 500, "debt": 12000},
    {"household_id": 2, "income": 8000, "liquid_savings": 15000, "debt": 6000},
    {"household_id": 3, "income": 3000, "liquid_savings": 200, "debt": 9000},
    {"household_id": 4, "income": 12000, "liquid_savings": 40000, "debt": 3000},
    {"household_id": 5, "income": 4500, "liquid_savings": 800, "debt": 10000},
    {"household_id": 6, "income": 6000, "liquid_savings": 2000, "debt": 7000}
]

df = pd.DataFrame(data)
df["months_of_buffer"] = df["liquid_savings"] / (df["income"] / 12)
df["months_of_buffer_rank"] = df["months_of_buffer"].rank(ascending=True)
print(df.sort_values("months_of_buffer_rank"))
```

**Result:** Household 3 is most fragile by buffer (0.8 months), but 
Household 1 has the highest debt (12,000). Different measures flag 
different households — direct evidence that the choice of fragility 
measure changes who is identified as most in need.

## Level 3 – Critical / Analytical Thinking (Guided Construction)

**Setup:** A colleague proposes using months_of_buffer as the single 
official fragility metric for the whole study.

**Three mechanisms:**
- Statistical/Methodological: Proxy Measure Validity
- Economic/Structural: Income Stability and Risk
- Behavioral/Psychological: Mental Accounting

**Statistical/Methodological — Proxy Measure Validity:**
No single proxy fully captures the underlying construct. Fragility 
has many dimensions — buffer, debt, income stability, access to 
credit, social support — and months_of_buffer represents only one. 
As found in Level 2, Household 3 was most fragile by buffer while 
Household 1 had the highest debt: different measures rank different 
households as most fragile. Adopting a single metric would 
systematically miss households fragile on other dimensions.

**Economic/Structural — Income Stability and Risk:**
The measure divides annual income by 12, treating income as a stable 
monthly flow. But income is a flow variable that varies month to 
month depending on profession (gig, seasonal, commission work). A 
household with the same buffer but volatile income faces different 
fragility than one with stable income. The measure ignores this, so 
using it alone would misclassify households with unstable income.

**Behavioral/Psychological — Mental Accounting:**
The measure counts all liquid savings as available buffer. But 
households mentally partition savings into accounts they refuse to 
touch (retirement, children's education), so the behaviorally 
accessible buffer may be smaller than the measured buffer. Adopting 
months_of_buffer as the single metric would overstate true resilience 
for households with strong mental accounting constraints.

## Interview-Style Question
Build a fragility ranking from income, savings, and debt in one 
afternoon; name the single biggest risk.

**Answer (compressed, interview-form):**
Compute a buffer index (liquid savings / monthly income), flag the 
lowest buffers as most fragile, and use debt-to-income as a secondary 
robustness check. The biggest risk is proxy validity — a single index 
captures only one dimension of fragility. In the Level 2 data, the 
household most fragile by buffer was not the one with the highest 
debt, so ranking on one metric would miss a whole category of at-risk 
customers. Mitigation: flag anyone in the worst quartile on either 
measure, not just one.

## Reflection
Day 8 marked clear progress on mechanism-based reasoning under the 
guided-construction format. Three focused paragraphs, one mechanism 
each, all closing the loop. Key correction: two paragraphs initially 
made the same income-volatility argument under different labels; 
sharpened so Proxy Validity addressed multidimensionality (with Level 
2 evidence) while Income Stability addressed the denominator. 
Interview answer required compression from ~320 to ~150 words and 
explicit answering of both halves of the question. Estimated depth 
reached ~80% of research-grade, up from ~25% on Day 4.
