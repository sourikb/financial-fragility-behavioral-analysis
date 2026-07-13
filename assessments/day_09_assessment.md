# Day 9 – Assessment

## Level 1 – Conceptual Understanding
Difference between & (AND) and | (OR); why parentheses are required; 
examples preferring each.

**Answer:** & (AND) filters where all conditions hold — stricter, 
narrower result. | (OR) filters where any condition holds — broader, 
more inclusive result. Each condition must be wrapped in parentheses 
because & and | have higher operator precedence than comparison 
operators (> <); without parentheses Python tries to evaluate the 
logical operator against a raw value (e.g., 1.5 & Series), causing an 
error. AND example: flag a company as fragile only if low revenue AND 
low liquid assets. OR example: flag a company as fragile if it meets 
either condition (broader screening).

## Level 2 – Applied Thinking
Construct a three-condition AND fragility flag; report count and 
proportion; display flagged households.

**Code:**
```python
import pandas as pd

data = [
    {"household_id": 1, "income": 5000, "liquid_savings": 500, "debt": 12000, "missed_payments": 3},
    {"household_id": 2, "income": 8000, "liquid_savings": 15000, "debt": 6000, "missed_payments": 0},
    {"household_id": 3, "income": 3000, "liquid_savings": 200, "debt": 9000, "missed_payments": 5},
    {"household_id": 4, "income": 12000, "liquid_savings": 40000, "debt": 3000, "missed_payments": 0},
    {"household_id": 5, "income": 4500, "liquid_savings": 800, "debt": 10000, "missed_payments": 1},
    {"household_id": 6, "income": 6000, "liquid_savings": 2000, "debt": 7000, "missed_payments": 2},
    {"household_id": 7, "income": 3500, "liquid_savings": 6000, "debt": 4000, "missed_payments": 0}
]

df = pd.DataFrame(data)
df["debt_to_income"] = df["debt"] / df["income"]
df["fragility_flag"] = (df["debt_to_income"] > 1.5) & (df["liquid_savings"] < 1000) & (df["missed_payments"] >= 1)

print("Number flagged:", df["fragility_flag"].sum())
print("Proportion flagged:", df["fragility_flag"].mean())
print(df[df["fragility_flag"]])
```

**Result:** 3 households flagged (1, 3, 5), a 42.9% rate. With three 
strict AND conditions on a small sample, the flag still captures 43% — 
a reminder that "strict" does not automatically mean "few."

## Level 3 – Critical / Analytical Thinking (Guided Construction)

**Setup:** A colleague proposes adopting the three-condition AND flag 
as the official fragility measure.

**Three mechanisms:**
- Statistical/Methodological: Arbitrary Thresholds
- Economic/Structural: Composition Effects
- Behavioral/Psychological: Present Bias

**Statistical/Methodological — Arbitrary Thresholds:**
The cutoffs debt_to_income > 1.5, liquid_savings < 1000, and 
missed_payments >= 1 are chosen without empirical or theoretical 
justification. Cutoffs chosen this way mischaracterize continuous 
reality as binary, and the choice of threshold often determines the 
conclusion. Small changes to any cutoff would reclassify households. 
Adopting this definition officially would embed unjustified thresholds 
into every downstream statistic, which is why the thresholds must be 
justified theoretically and empirically and tested with alternatives.

**Economic/Structural — Composition Effects:**
A summary statistic can hide heterogeneous components with different 
implications. Two households with the identical debt-to-income ratio 
of 1.17 face very different fragility if one holds low-interest 
mortgage debt and the other holds high-interest consumer debt. The 
AND definition treats them identically because both clear the same 
threshold. Adopting it officially would ignore debt composition and 
bias conclusions, which is why debt should be disaggregated by type 
before classifying fragility.

**Behavioral/Psychological — Present Bias:**
Present-biased households overweight immediate consumption and manage 
the visible symptoms of distress to avoid immediate discomfort. A 
present-biased household may keep missed_payments at zero by 
maintaining minimum payments while its finances collapse in less 
visible dimensions. Requiring missed_payments >= 1 therefore excludes 
exactly these households, even though they are severely fragile. 
Adopting this definition officially would systematically under-detect 
present-biased households, which is why the definition should not rely 
solely on visible distress signals like missed payments.

## Interview-Style Question
A manager likes a strict three-condition AND flag because the list is 
short and the budget is small. State your main concern and propose an 
alternative.

**Answer (interview-form):**
My main concern is false negatives. Requiring failure on all three 
conditions makes the list short — which the budget likes — but short 
partly because it excludes households genuinely at risk on two of the 
three dimensions (e.g., one still making minimum payments). I'd 
propose scoring households across all three dimensions, ranking them, 
and sizing the outreach list to the budget from the top of that 
ranking. The budget still controls list length, but we catch the 
highest-risk households overall rather than the narrow group that 
fails all three arbitrary cutoffs.

## Reflection
Second guided-construction assessment. All three Level 3 paragraphs 
held one mechanism and closed the loop on first attempt. Key 
correction: the Composition Effects example initially varied both the 
ratio and the debt type; sharpened to hold the ratio constant (1.17) 
and vary only composition, isolating the mechanism cleanly. Deliberately 
kept Present Bias for interview-defensibility and framed it as 
"households manage visible symptoms, so missed-payment conditions 
under-detect them." Interview answer required narrowing from three 
concerns to one (false negatives) and tying the alternative to the 
manager's real constraint (budget). Depth holding around 80%, with 
improving verbal compression.
