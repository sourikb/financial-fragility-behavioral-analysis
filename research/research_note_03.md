# Research Note 03 – Multidimensional Measurement of Financial Fragility

## Concept Connection
A list of dictionaries mirrors the row-column structure of survey data 
such as the SCF. Each household is a record; each attribute (income, 
expenses, debt) is a field. This is the mental model we will carry into 
the real dataset.

## Paper-Relevant Insight
Today's analysis demonstrated that savings alone is a misleading 
indicator of financial health. A household with positive savings can 
still be fragile if debt is high relative to income and savings. This 
motivates a composite fragility measure rather than a single-variable 
threshold.

## Variable Idea (refined)
Preliminary financial fragility should consider multiple dimensions:
- Savings (income minus expenses)
- Debt level
- Debt relative to income (debt-to-income ratio)
- Time required to clear debt from current savings

In the SCF, these will be operationalized using actual asset, liability, 
and income variables.

## Methodological Note (for paper)
Single-threshold classifications risk misclassifying resilient and 
fragile households. A multidimensional or index-based approach is more 
defensible both academically and for applied prediction.

## Status
Data structure understood conceptually. SCF dataset not yet loaded.
