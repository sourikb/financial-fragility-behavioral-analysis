# Day 10 — Worked Questions

## Topic
value_counts, proportions, and two-way crosstabs (risk vs composition)

---

## Level 2 — Homeowner × Fragility Crosstab

### Problem
Input: a 10-row DataFrame of households with columns `household_id`,
`education`, `homeowner` (bool), `fragile` (bool).

Required output:
1. Overall fragility rate (single number)
2. Crosstab of homeowner × fragile, raw counts
3. Same crosstab, row-normalized
4. One sentence interpreting the row-normalized table

### Setup (input data)
```python
import pandas as pd

data = [
    {"household_id": 1, "education": "high school", "homeowner": False, "fragile": True},
    {"household_id": 2, "education": "college", "homeowner": True, "fragile": False},
    {"household_id": 3, "education": "high school", "homeowner": False, "fragile": True},
    {"household_id": 4, "education": "graduate", "homeowner": True, "fragile": False},
    {"household_id": 5, "education": "college", "homeowner": False, "fragile": True},
    {"household_id": 6, "education": "high school", "homeowner": True, "fragile": False},
    {"household_id": 7, "education": "graduate", "homeowner": True, "fragile": False},
    {"household_id": 8, "education": "college", "homeowner": False, "fragile": True},
    {"household_id": 9, "education": "high school", "homeowner": False, "fragile": True},
    {"household_id": 10, "education": "college", "homeowner": True, "fragile": False}
]

df = pd.DataFrame(data)
```

### Solution
```python
# 1. Overall fragility rate
fragile_ratio = df["fragile"].sum() / len(df)
print(f"Overall Fragility Rate: {fragile_ratio}")   # 0.5
# One-line alternative: df["fragile"].mean()

# 2. Raw-count crosstab, relabeled for a manuscript
cross = pd.crosstab(df["homeowner"], df["fragile"])
manuscript = cross.rename(
    index={False: "Non-homeowners", True: "Homeowners"},
    columns={False: "Not fragile", True: "Fragile"}
)
print(manuscript)

# 3. Row-normalized as percentages
pct = pd.crosstab(df["homeowner"], df["fragile"], normalize="index") * 100
pct = pct.rename(
    index={False: "Non-homeowners", True: "Homeowners"},
    columns={False: "Not fragile", True: "Fragile"}
)
print(pct)
```

### Output

Overall Fragility Rate: 0.5

fragile Not fragile Fragile
homeowner
Non-homeowners 0 5
Homeowners 5 0

fragile Not fragile Fragile
homeowner
Non-homeowners 0.0 100.0
Homeowners 100.0 0.0


### Pattern
- `df["bool_col"].mean()` → rate of a True/False flag in one line.
- `pd.crosstab(index, columns)` → two-way count table (raw counts by default).
- `normalize="index"` → row-conditional shares = P(outcome | row group) = **risk**.
- `normalize="columns"` → column-conditional shares = P(row group | outcome) = **composition**.
- `.rename(index=..., columns=...)` → turn True/False labels into publication-ready text.

### Interpretation note
The row-normalized table answers P(fragile | homeownership) — a *risk*
statement ("among non-homeowners, X% are fragile"). The keyword is
*among*. A 0%/100% split is a warning sign (perfect separation), not a
triumphant finding — in real data it signals a leaked or
definitionally-overlapping variable, something to distrust and
investigate.

### Assistance level used
- Code: produced independently (full solution not needed).
- Interpretation (Q4): needed sharpening — I first described
  normalization mechanically; the P(A|B) / risk framing was corrected
  by Claude. → **concept named by Claude**
