# Research Note 07 – Heterogeneity Analysis as a Core Research Strategy

## Concept Connection
The groupby operation enables the empirical study of heterogeneity — 
how relationships, outcomes, and behaviors vary across subpopulations. 
For a behavioral economics study of financial fragility, heterogeneity 
is not a secondary concern. It is often the primary finding. The 
average household is a useful benchmark, but it tells almost nothing 
about which households are at risk, which interventions would help, 
or why disparities exist.

## Paper-Relevant Insight
Today's lesson exposed a fundamental research principle: the *shape* 
of a relationship across groups often matters more than the average. 
A strictly monotonic pattern, a weakly monotonic pattern with a 
plateau, and a non-monotonic pattern each suggest different underlying 
mechanisms. The capstone must report and interpret these shapes 
deliberately.

Specifically, for the SCF financial fragility analysis:
- Stratify fragility measures by education, age, race, and income 
  quintile
- Examine debt patterns across education levels for non-monotonic 
  features (e.g., plateaus suggesting threshold effects)
- Identify combinations of demographic characteristics that produce 
  surprising patterns
- Report group sample sizes alongside all group statistics; small 
  groups should be flagged for cautious interpretation

## Methodological Direction (for paper)
The capstone will include:
1. Summary tables of fragility measures stratified by single 
   demographic variables (education, race, age cohort, region)
2. Cross-tabulated summaries using multi-variable groupby (e.g., 
   fragility by education and race)
3. Explicit notation of small-group cells where statistics are 
   imprecise
4. Discussion of any non-monotonic or plateau patterns and the 
   behavioral or structural mechanisms that might explain them
5. Standard errors and 95% confidence intervals around all group 
   statistics

## Methodological Note
Heterogeneity analysis is often where the most policy-relevant 
findings emerge. A policy that benefits the average household may 
harm specific subpopulations. A behavioral nudge that increases 
saving for college-educated households may have no effect on 
high-school-educated households. The capstone must present 
heterogeneity not as an afterthought but as a central analytical 
chapter.

## Connection to SQL
The split-apply-combine pattern in pandas groupby maps directly to 
SQL GROUP BY. By Day 15-20, every analysis performed in pandas 
groupby will be replicated in SQL. This dual-language documentation 
will strengthen both the academic paper and the industry portfolio 
by demonstrating fluency across the standard data stack.

## Status
groupby operations operational on toy data. Heterogeneity analysis 
on real SCF data planned for Days 15-20. SQL replication planned in 
parallel.
