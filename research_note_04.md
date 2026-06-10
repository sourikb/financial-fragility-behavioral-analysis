# Research Note 04 – DataFrames and Feature Engineering Foundations

## Concept Connection
The DataFrame structure is conceptually identical to the row-column 
layout of the Survey of Consumer Finances. Each household corresponds 
to a row; each financial or demographic attribute corresponds to a 
column. All subsequent analysis in this project will operate on this 
structure.

## Paper-Relevant Insight
The construction of the debt-to-income ratio demonstrates a foundational 
principle of applied behavioral economics research: meaningful 
quantities are rarely available in raw form. They must be engineered 
from existing variables based on theoretical reasoning.

In today's example, one household exhibited a debt-to-income ratio of 
6.0 — debt six times annual income. In any empirical fragility study, 
such a value would be a strong predictor of vulnerability and is 
consistent with documented patterns of present-biased borrowing.

## Methodological Direction (for paper)
The financial fragility measure in the SCF analysis will be constructed 
from multiple engineered variables, including:
- Debt-to-income ratio
- Liquid-assets-to-income ratio
- Savings rate (income minus expenses, scaled by income)
- Debt-to-asset ratio

These will be combined into either a composite index or used as separate 
predictors in regression and machine learning models.

## Methodological Note
Feature engineering must remain transparent and theoretically motivated. 
Variables constructed without theoretical justification weaken both 
academic credibility and model interpretability. Each engineered variable 
in the capstone will be tied explicitly to a behavioral economic concept.

## Status
Core data structure tool (pandas DataFrame) operational. Variable 
construction logic demonstrated on toy data. SCF dataset not yet loaded.