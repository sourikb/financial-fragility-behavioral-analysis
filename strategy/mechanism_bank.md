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
### Correlation Is Not Causation
A visible association between two variables (in a scatterplot, 
correlation coefficient, or regression) does not establish that one 
causes the other. Three competing explanations always remain:
1. Reverse causation — Y may cause X rather than X causing Y
2. Omitted variables — a third factor Z may drive both X and Y
3. Selection — the sample itself may be non-random

- Example: A negative scatterplot relationship between income and 
  debt may reflect income reducing debt, debt reducing earning 
  capacity, or financial literacy driving both.
- Capstone relevance: Every visible relationship in the SCF analysis 
  will be flagged as associational unless a causal identification 
  strategy (IV, DiD, RD, natural experiment) is explicitly applied.

### Shape of Relationships in Grouped Data
Aggregate statistics across groups can mask important patterns. A 
relationship may appear monotonic in summary but contain plateaus, 
non-linearities, or reversals at finer levels. The shape itself often 
reveals more than the average.
- Strictly monotonic: outcome changes consistently in one direction
- Weakly monotonic: outcome moves in one direction but contains 
  plateaus or repetitions
- Non-monotonic: outcome reverses direction (U-shaped, inverted-U, 
  threshold effects)
- Example: Mean debt declines from high-school to college households 
  but plateaus from college to graduate households, suggesting a 
  behavioral or structural threshold has been crossed.
- Capstone relevance: All grouped statistics in the SCF analysis must 
  be reported with their full shape across groups, not just direction 
  of effect. Plateaus and non-monotonic patterns will be flagged 
  explicitly as candidates for mechanism-based explanation.

### Proxy Measure Validity
A ranking, classification, or analysis is only as valid as the 
variable used to construct it. A proxy that imperfectly captures the 
underlying construct will systematically misclassify cases, even when 
the computation is flawless.
- Example: Ranking households by debt-to-income to identify fragility 
  misclassifies a high-ratio household with large liquid savings as 
  fragile, and a low-ratio household with zero emergency buffer as 
  secure.
- Capstone relevance: The fragility measure must be validated as a 
  proxy before it is used to rank or target. Multiple candidate 
  measures will be compared, and the sensitivity of conclusions to 
  the choice of proxy will be reported explicitly.

### Outcome Definition Sensitivity
The way a binary or categorical outcome is defined determines which 
cases are classified as positive, and therefore shapes every 
downstream statistic and model. Conjunctive (AND) definitions produce 
narrow, conservative classifications; disjunctive (OR) definitions 
produce broad, inclusive ones. The same underlying data can yield very 
different prevalence rates depending on this choice.
- Example: Defining fragility as high debt-to-income AND low savings 
  flags fewer households than high debt-to-income OR low savings. The 
  measured fragility rate can swing dramatically based purely on the 
  definitional logic.
- Capstone relevance: The fragility outcome definition must be stated 
  explicitly, justified theoretically, and subjected to sensitivity 
  analysis across AND-based, OR-based, and index-based alternatives. 
  The reported prevalence of fragility is meaningless without stating 
  the definition that produced it.

### Conditioning Direction (Risk vs Composition)
P(A|B) and P(B|A) are different quantities that answer different
questions. Reporting only one direction invites misinterpretation, and
the two can diverge sharply when group sizes differ.
- Risk: "Of high school households, what share are fragile?"
  (conditioning on the demographic) — identifies who is most vulnerable.
- Composition: "Of fragile households, what share are high school
  educated?" (conditioning on the outcome) — identifies where the volume
  of the problem sits.
- Example: A small group may have a 100% fragility rate (highest risk)
  while comprising only 5% of all fragile households (small share),
  simply because the group is small.
- Capstone relevance: Every demographic breakdown in the SCF analysis
  will report both directions, with raw counts alongside proportions.
  Subgroups where the two directions diverge are flagged as the most
  policy-relevant findings.
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
### Small Subgroup Distortions
Group statistics computed on small subgroups carry large standard 
errors and are easily distorted by individual observations. The 
smaller the group, the less the group statistic should be trusted.
- Example: A "graduate" group with only 2 households produces a mean 
  that is essentially the average of two observations; one unusual 
  household shifts the entire group statistic.
- Capstone relevance: All SCF analyses stratified by demographic 
  combinations must report group sample sizes alongside statistics. 
  Cells with fewer than a minimum threshold (typically n=30 for 
  asymptotic inference, or larger for behavioral measures) will be 
  flagged or aggregated.
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

  ### Base-Rate Neglect in Research Presentation
The tendency to ignore underlying base rates when interpreting
conditional probabilities — documented extensively as an individual
cognitive bias — also operates on researchers and readers interpreting
tables. A reader shown only P(education | fragile) will often
mistakenly reason as though they have been shown P(fragile | education).
- Example: "75% of fragile households have high school education" is
  frequently misread as "high school households are 75% likely to be
  fragile" — a different and possibly very wrong claim.
- Capstone relevance: The same bias the paper studies in households
  operates on the paper's own readers. Table design must actively
  prevent it: state the conditioning direction explicitly in every
  caption, and report both directions where relevant.
---

## Status

Active and growing. New mechanisms will be added as they emerge in 
the learning journey. By the end of Year 1, this document is expected 
to contain 20-30 named mechanisms with concrete examples.

By Year 3, this document doubles as:
- Interview preparation for top firms
- A teaching resource for the BSQE Research Methods course
- A reference for the working paper's methodology section
