# Research Note 06 – Visualization as a Research Tool

## Concept Connection
Visualization is not a presentation layer added at the end of analysis. 
It is an integral part of the research process from the very beginning. 
Before any model is fit, distributions must be inspected, relationships 
must be visualized, and outliers must be identified. The Survey of 
Consumer Finances analysis will rely heavily on visualization at every 
stage — exploration, variable construction, model diagnostics, and 
final presentation.

## Paper-Relevant Insight
Today's lesson reinforced a critical research principle: the shape of 
a distribution often matters more than its mean. A behavioral 
economics study of financial fragility must visualize distributions, 
not just report summary statistics.

Specifically:
- Histograms of debt, income, and liquid assets will reveal whether 
  these variables are normally distributed, skewed, or bimodal.
- Scatterplots of behavioral proxies against the fragility outcome 
  will reveal whether relationships are linear, nonlinear, or 
  characterized by threshold effects.
- Boxplots stratified by education, age, and race will reveal 
  heterogeneity that aggregate statistics would obscure.

## Methodological Direction (for paper)
The capstone will include:
1. Distribution plots of every key variable in the fragility index.
2. Bivariate scatterplots showing the relationship between each 
   behavioral proxy and the outcome.
3. Boxplots stratified by demographic subgroups to reveal 
   heterogeneity.
4. Diagnostic plots after regression and ML models (residuals, 
   calibration curves).
5. Publication-quality figures for the final paper and 
   industry-portfolio versions of the work.

## Methodological Note
A scatterplot revealing a strong association is a starting point, not 
a conclusion. The capstone must consistently distinguish between 
correlation visible in charts and causal claims requiring identification 
strategies. This distinction will be made explicit in every figure 
caption and discussion.

## Reproducibility Principle
All simulations and visualizations in the capstone will use a fixed 
random seed, documented explicitly. All figures will be reproducible 
from the public code on GitHub. This is a non-negotiable standard for 
both academic publication and industry credibility.

## Status
Visualization toolkit (bar, histogram, scatter, boxplot) operational. 
Publication-quality formatting (titles, labels, units) practiced. 
Real SCF visualizations planned for Days 12-20.
