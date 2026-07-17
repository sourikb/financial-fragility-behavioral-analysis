# Research Note 10 – Conditioning Direction and Policy Targeting

## Concept Connection
Cross-tabulation is the primary tool for producing the descriptive
tables that anchor any empirical paper. For the SCF financial fragility
analysis, crosstabs will generate the Table 1 breakdowns of fragility
across education, race, age cohort, region, and homeownership status.
The technical operation is simple; the interpretive decision — which
direction to condition — is substantive.

## Paper-Relevant Insight
Today's lesson surfaced a distinction with direct policy consequences:
P(fragile | education) and P(education | fragile) are different
quantities that answer different questions.

- Row-normalized (conditioning on education) yields a RISK statement:
  what share of a demographic group is fragile. This identifies which
  groups are most vulnerable.
- Column-normalized (conditioning on fragility) yields a COMPOSITION
  statement: what share of fragile households belong to a demographic
  group. This identifies where the volume of the problem sits.

These can diverge sharply when group sizes differ. A small group can
have the highest fragility rate while contributing a minor share of all
fragile households. Targeting on risk alone may address a small
population efficiently while missing the bulk of fragility; targeting
on composition alone may spread resources across a large, mostly
non-fragile population.

## Methodological Direction (for paper)
The capstone will:
1. Report BOTH conditioning directions for every key demographic
   breakdown, not just one
2. Report raw cell counts alongside all proportions, so readers can
   assess precision
3. Flag any subgroup where the two directions diverge substantially —
   these are the most policy-relevant findings
4. Explicitly state in each table caption which quantity is being
   reported (e.g., "cells report the share of each education group
   classified as fragile")

## Methodological Note
Reporting only one conditioning direction is a common and consequential
omission in applied work. A reader who sees "75% of fragile households
have high school education" cannot infer the fragility rate among high
school households — and vice versa. Papers that report only one
direction invite base-rate confusion in readers and reviewers. The
capstone will report both.

## Behavioral Connection
The risk-versus-composition confusion is base-rate neglect operating at
the level of research design rather than individual judgment. This is
worth noting explicitly in the paper: the same cognitive error that
behavioral economics documents in individuals also appears in how
empirical results are presented and consumed. This gives the paper a
reflexive methodological point that connects its behavioral subject
matter to its own analytical practice.

## Status
Crosstab operations operational on toy data. Real SCF demographic
breakdowns planned for the descriptive phase. Both conditioning
directions to be reported as standard practice.
