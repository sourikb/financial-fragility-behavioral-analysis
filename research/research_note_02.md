# Research Note 02 – Lists and Iteration as Data Structure Foundation

## Concept Connection
In behavioral economics, we analyze decisions across many individuals. 
Python lists are the simplest representation of a cross-sectional dataset 
— one value per individual, stored in order.

## Paper-Relevant Insight
The saving vs. not saving classification we built today is a primitive 
version of a financial fragility indicator. In the SCF dataset, we will 
construct a similar binary variable based on liquid assets, income, and 
expense proxies.

## Variable Idea (for future use)
A household can be preliminarily classified as financially fragile if:
    expenses >= income

This will be refined later using actual SCF variables such as:
- Liquid assets relative to income
- Debt-to-income ratio
- Self-reported financial stress

## Status
Preliminary logic established. Dataset not yet loaded.
