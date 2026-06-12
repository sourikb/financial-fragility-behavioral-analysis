# Day 2 – Assessment

## Question 1 (Conceptual)
You have a list of 1,000 households with their income and expenses. 
Why is a for loop more practical than writing if/else 1,000 times?

**Answer:** Using a for loop makes the process extremely concise. 
Python automatically runs the if/else logic through all 1,000 households 
sequentially without having to write it out separately each time.

## Question 2 (Behavioral Economics Connection)
Why is the "saving vs. not saving" classification insufficient to identify 
truly financially fragile households?

**Answer:** Saving or not saving alone does not capture true financial 
fragility. A household may have existing wealth, passive income, or 
inheritance that provides resilience without active saving. Conversely, 
a household that appears to be saving may still be fragile if savings 
are small, debt is high, or behavioral factors like present bias cause 
chronic undersaving. Financial fragility is about resilience to shocks, 
not just the saving/not saving binary.

## Question 3 (Code)
Store debt levels of four households in a list and print each with 
its household number.

**Answer:**
```python
debts = [4000, 5000, 6000, 7000]
for i in range(4):
    print("Household", i+1, ":", debts[i])
```

**Output:**
Household 1 : 4000
Household 2 : 5000
Household 3 : 6000
Household 4 : 7000

## Self-Correction Note
Initially wrote debts[0] and "i+1" as a string. Identified and 
corrected both errors independently.
