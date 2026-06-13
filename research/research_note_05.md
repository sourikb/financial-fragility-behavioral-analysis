# Research Note 05 – Missingness as a Behavioral and Structural Signal

## Concept Connection
Real survey data is rarely complete. The Survey of Consumer Finances 
(SCF), like all household surveys, contains missing values across 
income, asset, debt, and demographic variables. The choice of how to 
handle this missingness will shape every downstream finding in the 
capstone analysis.

## Paper-Relevant Insight
Today's exploration revealed a critical research principle: 
missingness in behavioral and financial survey data is rarely random. 
It is often correlated with the very outcome the researcher seeks to 
study. Households experiencing financial distress, low financial 
literacy, or psychological discomfort around debt are 
systematically more likely to skip or underreport relevant fields.

This has direct consequences for the capstone:
- Mean imputation in the SCF will likely understate fragility 
  because the most fragile households are the most likely to be 
  missing on key variables.
- Listwise deletion will likely bias the sample toward more 
  financially organized, higher-literacy households.
- The choice of strategy must be defended explicitly in the paper.

## Methodological Direction (for paper)
The capstone will:
1. Report the pattern and magnitude of missingness for each variable 
   used in the fragility index.
2. Conduct sensitivity analyses comparing results under three 
   strategies: listwise deletion, mean imputation, and 
   model-based imputation (later in the project).
3. Discuss whether observed missingness patterns are consistent with 
   "missing at random" (MAR) or "missing not at random" (MNAR) 
   assumptions.
4. Use multiple imputation methods if missingness exceeds 5-10 
   percent for key variables.

## Methodological Note
A defensible paper must explicitly justify its missingness strategy. 
Silent imputation or unexplained deletion is a common weakness in 
applied behavioral economics work and a frequent target of referee 
criticism. The capstone will treat the handling of missing data as 
a methodological decision, not a preprocessing step.

## Status
Toy-data exploration complete. Real SCF missingness patterns to be 
documented when the dataset is loaded (planned for Days 12-15).