# Methods

## Study dataset and analytical grouping

The final whole-genome sequencing dataset comprised 189 *Escherichia coli* isolates. Isolates were assigned to two analytical groups based on the study metadata: bloodstream/invasive isolates (n = 112) and intestinal carriage isolates (n = 77). Metadata fields used for phylogenetic and epidemiological annotation included experiment accession, master isolate identifier, analysis group, phylogroup, sequence type, and serotype.

The final tree annotation table used the fields `Experiment_Accession`, `Master_ID`, `Analysis_Group`, `Phylogroup`, `ST`, and `Serotype`.

Because BioProject membership and analysis group were completely aliased, pooled comparisons were treated as exploratory between-cohort comparisons rather than as estimates of an independent bloodstream-source effect. The final mapping was PRJDB18396 (92 bloodstream/invasive isolates), PRJNA596854 (20 bloodstream/invasive isolates), and PRJDB18129 (77 intestinal carriage isolates).

## Antimicrobial resistance gene detection

Acquired and intrinsic antimicrobial resistance determinants were identified using AMRFinderPlus. The consolidated final AMR dataset contained 2,042 AMR hit rows representing 84 gene symbols, 16 antimicrobial classes, and 26 subclasses.

For downstream linkage, each AMR hit was retained as an individual genomic interval with isolate identifier, contig identifier, start coordinate, stop coordinate, gene symbol, AMR class, subclass, and AMRFinderPlus detection method.

The exact AMRFinderPlus software/database version should be recovered from the original run logs before archival release and is intentionally not inferred here.

## Mobilome inference

Plasmid context was inferred using MOB-recon from MOB-suite. Reports were available for all 189 isolates. AMR hits were linked to MOB-recon contig assignments after contig-name normalization.

The final AMR-MOB linkage classified 1,050 AMR hits as predicted plasmid-associated and 992 as predicted chromosome-associated.

MOB-recon classifications were treated as short-read assembly-based context predictions. They were not interpreted as definitive experimental localization of ARGs to plasmids or chromosomes.

The exact MOB-suite/MOB-recon version should be recovered from the original run logs before archival release.

## Integron detection

Integron structures were detected with IntegronFinder version 2.0.6. Batch output was consolidated across all 189 isolates.

Three IntegronFinder structure categories were preserved as distinct entities:

- complete integron
- CALIN
- In0

The consolidated dataset contained 959 integron-related element rows and 209 structures. At isolate level, 122 isolates were IntegronFinder-positive and 67 had no detected structure. The final structure counts were 60 complete integrons, 121 CALIN structures, and 28 In0 structures.

## ARG-integron interval linkage

AMR intervals were linked to IntegronFinder structures using genomic coordinates on normalized contig identifiers.

Each AMR hit was assigned one of four positional relationships:

- `inside_structure`: the complete AMR interval was contained within the detected IntegronFinder structure
- `boundary`: the AMR interval overlapped a structure boundary without full containment
- `same-contig-outside`: the AMR hit and structure were on the same contig but did not overlap
- `no-structure`: no relevant IntegronFinder structure was present on the linked contig

Across 2,042 AMR hits, 301 were classified as inside a detected IntegronFinder structure, 38 as boundary overlaps, 105 as same-contig-outside, and 1,598 as no-structure. Of the 301 fully contained hits, 116 occurred within complete integrons and 185 within CALIN structures.

## Definition of strict complete-integron ARG

A strict complete-integron ARG was defined as an AMRFinderPlus AMR interval whose start and stop coordinates were fully contained within the boundaries of an IntegronFinder structure classified as `complete`.

This definition deliberately excluded:

- partial or boundary overlap
- same-contig proximity without containment
- CALIN-associated ARGs
- In0-associated ARGs

A total of 116 AMR hits met the strict definition, distributed across 58 isolates.

The most frequent strict complete-integron ARGs were:

- `dfrA17`: 45 hits
- `aadA5`: 32
- `dfrA14`: 13
- `aadA2`: 7
- `aadA1`: 6
- `dfrA1`: 6
- `lnu(F)`: 6
- `estX-3`: 1

## ARG-integron-MOB triple linkage

The ARG-integron linkage was combined with MOB-recon context to generate an integrated hit-level table. The final table retained, among other fields, isolate accession, ARG identity, AMR interval, integron positional relationship, structure type, structure coordinates, isolate-level integron positivity, predicted MOB-recon location, and strict complete-integron status.

Among the 116 strict complete-integron ARG hits, 108 (93.1%) were predicted plasmid-associated and 8 (6.9%) were predicted chromosome-associated.

By analytical group:

- bloodstream/invasive: 83 strict hits, of which 78 (94.0%) were predicted plasmid-associated and 5 (6.0%) chromosome-associated
- intestinal carriage: 33 strict hits, of which 30 (90.9%) were predicted plasmid-associated and 3 (9.1%) chromosome-associated

These counts are hit-level, not isolate-level, summaries.

## Per-isolate master table

Hit-level outputs were summarized into a per-isolate master table integrating cohort metadata, AMR burden, MOB-recon context, IntegronFinder structure burden, and strict complete-integron ARG burden.

This table was the primary input for isolate-level statistical comparisons.

## Statistical analysis

Binary endpoints were compared between the bloodstream/invasive and intestinal carriage cohorts using two-sided Fisher exact tests. Effect size was summarized as an odds ratio.

Count/burden endpoints were compared using a nonparametric two-group test, with rank-biserial correlation (RBC) reported as the effect-size measure. Positive RBC values indicate higher ranks in the bloodstream/invasive cohort under the analysis coding used in the production workflow.

Multiple testing within the prespecified endpoint families was controlled using the Benjamini-Hochberg false discovery rate procedure. Adjusted values are reported as `q` values.

Key pooled binary endpoints included:

- any IntegronFinder structure
- complete integron positivity
- at least one strict complete-integron ARG
- at least one strict predicted plasmid-associated complete-integron ARG
- at least one strict predicted chromosome-associated complete-integron ARG

Key burden endpoints included:

- total AMR hit burden
- predicted plasmid-associated ARG burden
- predicted chromosome-associated ARG burden
- total IntegronFinder structure burden
- complete integron burden
- strict complete-integron ARG burden
- strict predicted plasmid-associated complete-integron ARG burden
- CALIN burden

## Sensitivity analyses

Two sensitivity strategies were used to evaluate the strong study-background and lineage structure of the dataset.

First, pairwise BioProject comparisons were performed using PRJDB18129 as the carriage cohort comparator against each bloodstream-associated BioProject separately. This analysis was used to distinguish consistent patterns from study-specific heterogeneity.

Second, within-phylogroup comparisons were performed for the major phylogroups with sufficient representation, particularly phylogroups A and B1. The same principal binary and burden endpoints were examined within lineage strata.

These analyses were interpreted as sensitivity analyses rather than as a complete multivariable solution to confounding.

## Visualization

Publication figures were generated in Python using Matplotlib. Confirmed visualization-environment versions were:

- pandas 3.1.0
- scipy 1.18.1
- matplotlib 3.11.2
- statsmodels 0.15.0
- Pillow 13.0.0
- CairoSVG 2.9.1

Figures were exported in high-resolution PNG and vector SVG/PDF formats.

## Interpretive boundary

The dataset does not permit estimation of a bloodstream-source effect independent of study because analysis group and BioProject are completely confounded. Therefore, pooled differences should be described as between-cohort or cross-study differences. Biological interpretation should emphasize patterns that are supported by sensitivity analyses and should avoid causal language.
