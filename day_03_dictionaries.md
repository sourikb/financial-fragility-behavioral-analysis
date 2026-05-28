# Day 3 – Dictionaries and Structured Data

## What I Learned
- A dictionary stores values with labels (keys) instead of positions
- Values are accessed by key: household["income"]
- Dictionaries are clearer than lists when data has named attributes
- Multiple dictionaries can be stored in a list (a list of dictionaries)
- A list of dictionaries mirrors the structure of a real dataset: 
  rows (households) and columns (attributes)

## Simple Example
```python
households = [
    {"income": 5000, "expenses": 3200, "debt": 8000},
    {"income": 2000, "expenses": 2500, "debt": 12000},
    {"income": 9000, "expenses": 4000, "debt": 1000}
]

for i in range(3):
    savings = households[i]["income"] - households[i]["expenses"]
    print("Household", i+1, "savings:", savings)
```

## Key Insight
A list of dictionaries is conceptually identical to a dataset table. 
Financial fragility cannot be judged on savings alone — debt must be 
considered jointly. This reinforces the need for multiple variables 
in the capstone analysis.