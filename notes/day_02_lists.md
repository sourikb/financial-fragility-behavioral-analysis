# Day 2 – Lists and Loops

## What I Learned
- A list stores multiple values under one name
- Items in a list are accessed by position (index), starting at 0
- A for loop repeats an action automatically for every item in a list
- Lists and loops can be combined with if/else to classify multiple individuals

## Simple Example
```python
incomes = [2000, 5000, 3200, 1500, 8000]
expenses = [1800, 4200, 3500, 1600, 6000]

for i in range(5):
    if incomes[i] > expenses[i]:
        print("Person", i+1, "is saving money")
    else:
        print("Person", i+1, "is not saving money")
```

## Key Insight
A for loop allows us to apply the same logic to every individual in a 
dataset automatically. This is the foundation of analyzing household 
financial behavior at scale.
