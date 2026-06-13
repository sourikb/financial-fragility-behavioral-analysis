# Mechanism Bank

A running catalog of analytical mechanisms that sharpen 
mechanism-based reasoning — the ability to identify distinct causal, 
behavioral, or structural mechanisms behind observed patterns rather 
than listing surface-level observations.

This is a continuously updated document. New mechanisms are added as 
they emerge in lessons, assessments, and project work.

## How to Use This Bank

When critiquing a method, building a variable, or interpreting a 
result, reach for mechanisms across three distinct categories:

1. Statistical / Methodological
2. Economic / Structural
3. Behavioral / Psychological

A research-grade critique identifies at least one mechanism from each 
category, not three variations of the same idea.

---

## Statistical and Methodological Mechanisms

### Arbitrary Thresholds
Cutoffs chosen without empirical or theoretical justification 
mischaracterize continuous reality as binary. The choice of threshold 
often determines the conclusion.
- Example: Using debt-to-income > 0.4 vs > 0.5 to classify fragility.
- Capstone relevance: Any threshold-based fragility classifier must 
  be justified empirically.

### Measurement Error Near Boundaries
Binary classifications hide noise at the cutoff. Households just above 
and just below behave similarly but are coded differently.
- Capstone relevance: Continuous fragility scores will be more 
  defensible than binary classifications.

### Information Loss From Binarization
Converting continuous measures to binary discards variance and 
predictive power.
- Capstone relevance: Both binary and continuous outcome variables 
  will be modeled in parallel.

### Mean Imputation Collapses Variance
Replacing missing values with the column mean preserves sample size 
but eliminates real variation in the data. The imputed values cluster 
artificially at the central tendency, which can flip classifications 
and bias regression estimates.
- Example: A truly low-income household imputed with the sample mean 
  income appears financially healthier than it is.
- Capstone relevance: Mean imputation will not be used naively in 
  the SCF analysis. Multiple imputation or model-based imputation 
  will be considered when missingness is substantial.
---

## Economic and Structural Mechanisms

### Endogeneity
The proposed cause and effect may move together because each 
influences the other.
- Example: Low liquidity may cause fragility, but fragility may also 
  cause low liquidity (households in crisis draw down buffers).
- Capstone relevance: Cross-sectional SCF data cannot establish 
  causal direction without identification strategy.

### Composition Effects
A summary statistic may hide heterogeneous components with different 
implications.
- Example: A debt-to-income ratio of 5.0 from low-interest mortgage 
  debt differs fundamentally from the same ratio in high-interest 
  consumer debt.
- Capstone relevance: Disaggregate debt by type before modeling.

### Income Stability and Risk
Static income measures miss the variance and reliability of income 
flows, which matter as much as level.
- Capstone relevance: The SCF includes income volatility proxies. 
  These must be incorporated.
  
### Selection Bias in Missingness
Non-response is rarely random. Households who refuse to disclose 
income, assets, or debt often differ systematically from those who 
respond. Imputing their values with the responder mean assumes 
they are average when they are typically not.
- Example: Very high-income or very low-income households are more 
  likely to refuse income disclosure than middle-income households.
- Capstone relevance: SCF imputation strategies must explicitly 
  consider the structure of who is missing, not just how many.
---

## Behavioral and Psychological Mechanisms

### Mental Accounting
Households partition wealth into psychologically separate accounts 
and may refuse to draw from some (retirement, education) even in 
financial distress.
- Capstone relevance: Liquid asset measures overstate true 
  resilience if mental accounting constraints are ignored.

### Present Bias
Households systematically overweight immediate consumption against 
future financial security, leading to chronic undersaving and 
re-borrowing.
- Capstone relevance: A behavioral proxy for present bias is 
  central to the fragility analysis.

### Precautionary Motive Heterogeneity
Identical balance sheets may reflect very different precautionary 
behaviors depending on informal insurance networks, social ties, 
and risk perception.
- Capstone relevance: Two households with low liquidity may have 
  very different actual fragility based on unobserved social and 
  community support.

### Missing Not at Random (MNAR) from Behavioral Causes
The very act of skipping a survey question can be driven by the 
outcome being studied. Households experiencing financial distress, 
shame around debt, low financial literacy, or cognitive overload 
are more likely to leave key fields blank. This means missingness 
is itself a signal of fragility.
- Example: Households with high credit card debt may underreport 
  or skip debt disclosure due to shame; households in financial 
  crisis may be too cognitively overloaded to complete detailed 
  asset breakdowns.
- Capstone relevance: The SCF fragility analysis must treat 
  missingness in debt and asset variables as potentially 
  informative, not as a nuisance to be removed.
---

## Status

Active and growing. New mechanisms will be added as they emerge in 
the learning journey. By the end of Year 1, this document is expected 
to contain 20-30 named mechanisms with concrete examples.

By Year 3, this document doubles as:
- Interview preparation for top firms
- A teaching resource for the BSQE Research Methods course
- A reference for the working paper's methodology section
