# Research Note 09 – Constructing the Fragility Outcome Variable

## Concept Connection
Multi-condition filtering is the mechanism by which the capstone's 
central outcome variable — the financial fragility flag — will be 
constructed. The Survey of Consumer Finances analysis requires 
transforming raw financial variables into a binary or categorical 
fragility classification. Today's lesson established the technical 
foundation: combining conditions across multiple dimensions and 
storing the result as an analyzable variable.

## Paper-Relevant Insight
The construction of a fragility flag forces an explicit definitional 
choice with real consequences. Whether fragility requires distress on 
ALL dimensions (AND logic) or ANY dimension (OR logic) fundamentally 
changes which households are classified as fragile, and therefore 
changes every downstream statistic, regression, and prediction.

This has direct implications for the capstone:
- The definition of the fragility outcome must be stated explicitly 
  and justified theoretically
- AND-based definitions produce conservative, high-confidence 
  classifications; OR-based definitions produce inclusive ones
- The prevalence of fragility (the proportion flagged) is highly 
  sensitive to this choice and must be reported transparently
- Sensitivity analysis across alternative definitions strengthens 
  the paper's credibility

## Methodological Direction (for paper)
The capstone will:
1. Define fragility using explicit, theoretically-grounded thresholds 
   across multiple dimensions (buffer, debt-to-income, income 
   stability where measurable)
2. Construct the fragility flag as a stored variable
3. Report the resulting prevalence of fragility
4. Conduct sensitivity analysis comparing AND-based, OR-based, and 
   index-based definitions
5. Discuss how the choice of definitional logic affects conclusions 
   and policy implications

## Methodological Note
The definition of the outcome variable is one of the most 
consequential decisions in the entire analysis. A poorly justified 
or arbitrary fragility definition undermines every result that 
follows. The paper will treat the outcome definition as a substantive 
research decision requiring theoretical justification and empirical 
sensitivity testing — not as a preprocessing convenience.

## Connection to Modeling
Once fragility is stored as a flag, it becomes the target variable 
for later classification models. The proportion flagged (the base 
rate) will directly affect model evaluation: a low base rate creates 
class imbalance, which must be addressed in the machine learning 
phase (Days 41-60). Today's flag construction is the first step in 
that modeling pipeline.

## Status
Multi-condition flag construction operational on toy data. Real SCF 
fragility variable construction planned for the modeling phase. 
Definitional sensitivity analysis to be designed alongside it.
