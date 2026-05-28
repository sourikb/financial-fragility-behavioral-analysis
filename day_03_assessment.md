# Day 3 – Assessment

## Level 1 – Conceptual Understanding
When would you choose a dictionary over a list? Give a financial example.

**Answer:** Use a dictionary when each observation has multiple named 
attributes. Example: storing the division between stocks, bonds, and 
commodities for each household portfolio.

## Level 2 – Applied Thinking
Calculate and print a household's debt-to-income ratio.

**Answer:**
```python
household = {"income": 4000, "expenses": 3500, "debt": 20000}
debt_to_income_ratio = household["debt"] / household["income"]
print("Debt-to-income ratio:", debt_to_income_ratio)
```
**Output:** Debt-to-income ratio: 5.0

## Level 3 – Critical / Analytical Thinking
Why might relying only on debt-to-income ratio misclassify households?

**Answer (expanded with feedback):**
The debt-to-income ratio alone is insufficient for several distinct reasons:
1. Composition of debt — a high ratio from low-interest mortgage debt 
   differs greatly from high-interest consumer debt; the ratio treats 
   all debt as identical.
2. Income stability — a stable income can service the same ratio far 
   more safely than a volatile, gig-based income; the ratio ignores 
   income risk.
3. Behavioral dynamics — the ratio is a static snapshot and does not 
   capture tendencies such as present bias and chronic re-borrowing.
Additionally, the ratio ignores savings buffers and other assets/investments.

## Reflection
Initial reasoning focused on omitted assets. Feedback emphasized 
distinguishing reasons across different analytical dimensions 
(debt quality, income risk, behavioral dynamics).