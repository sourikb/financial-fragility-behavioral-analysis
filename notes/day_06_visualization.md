# Day 6 – Visualization with matplotlib

## What I Learned
- matplotlib is the foundational Python library for creating charts
- The standard import convention is: import matplotlib.pyplot as plt
- Every research-quality chart must have a title and axis labels with 
  units; unlabeled charts are not communication, only decoration
- Four core chart types form the foundation of applied data visualization:

  1. Bar chart (plt.bar) — compares values across discrete categories
  2. Histogram (plt.hist) — shows the distribution of a single 
     continuous variable
  3. Scatterplot (plt.scatter) — reveals the relationship between 
     two variables
  4. Boxplot (plt.boxplot) — compares distributions across groups, 
     showing medians, quartiles, and outliers in a single view

- np.random.seed(N) ensures reproducibility; without it, simulated 
  results change every run
- Simulation parameters (mean, standard deviation, sample size, 
  noise level) are research design choices that must be made 
  deliberately and, in formal work, defended

## Simple Example
```python
import pandas as pd
import matplotlib.pyplot as plt
import numpy as np

np.random.seed(42)

incomes = np.random.normal(loc=50000, scale=15000, size=100)
df = pd.DataFrame({"income": incomes})

plt.hist(df["income"], bins=15)
plt.title("Distribution of Household Incomes")
plt.xlabel("Income ($)")
plt.ylabel("Number of Households")
plt.show()
```

## Key Insight
Visualization is not decoration — it is the primary means by which 
patterns in data become visible. A scatterplot can reveal a 
relationship that no table communicates as quickly. A boxplot can 
expose outliers that a mean conceals. A histogram can reveal 
distributional shape that a summary statistic flattens.

Research-quality visualization requires deliberate design choices: 
chart type, axis labels, scale, and the explicit acknowledgment 
that visible associations are starting points for analysis, not 
substitutes for causal identification.

## Course Module Note
The four-chart visualization toolkit (bar, histogram, scatter, 
boxplot) plus simulation calibration is directly usable as a 
foundational module in the BSQE Research Methods in Quantitative 
Economics course. Both topics are typically underserved in 
undergraduate quantitative training.
