# Reproducibility notes

## Design limitation

The central design constraint is complete aliasing between BioProject and analysis group. No model can identify an independent analysis-group effect from BioProject using this dataset alone because there is no within-BioProject overlap between bloodstream/invasive and carriage groups.

Therefore:

- pooled comparisons are exploratory
- wording should use "between-cohort" or "cross-study" differences
- causal language should be avoided
- BioProject pairwise and within-phylogroup sensitivity analyses should accompany interpretation

## Strict containment rule

Strict complete-integron ARG status requires full coordinate containment of the AMR interval within a structure classified by IntegronFinder as complete.

This rule is deliberately more conservative than any-overlap linkage.

## Hit-level versus isolate-level summaries

Several outputs operate at different levels:

- AMR-integron-MOB linkage: hit level
- strict ARG gene frequency: hit level
- MOB context distribution of strict ARGs: hit level
- positivity endpoints: isolate level
- AMR/integron burden: isolate level

Do not substitute hit counts for isolate prevalence.

## Multiple testing

False discovery rate correction used the Benjamini-Hochberg procedure within the prespecified comparison families. Manuscript figures and tables should distinguish raw `p` values from adjusted `q` values.

## Version-control principle

Where an exact script exists on the original VM, the archival copy should be taken from that VM. Reconstructed scripts should not be represented as the original production code.
