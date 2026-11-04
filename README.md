# Thesis WGS: Integron, AMR, and Mobilome Analysis

Reproducibility archive for a comparative whole-genome sequencing analysis of 189 *Escherichia coli* isolates, focused on antimicrobial resistance genes (ARGs), integron-associated ARGs, and predicted plasmid/chromosome context.

## Cohort

- Total isolates: **189**
- Bloodstream/invasive cohort: **112**
- Intestinal carriage cohort: **77**

The pooled cohort comparison is **cross-study/between-cohort**, not an independently adjusted estimate of biological source effect. BioProject and analysis group are completely aliased in this dataset:

- PRJDB18396: 92 bloodstream/invasive, 0 carriage
- PRJNA596854: 20 bloodstream/invasive, 0 carriage
- PRJDB18129: 0 bloodstream/invasive, 77 carriage

Accordingly, pooled group differences must not be interpreted as an independent causal effect of bloodstream origin.

## Analysis overview

The workflow integrates:

1. Cohort curation and metadata harmonization
2. AMR gene detection using AMRFinderPlus
3. Plasmid reconstruction/context assignment using MOB-recon
4. Integron detection using IntegronFinder
5. ARG-integron interval linkage
6. ARG-integron-MOB triple linkage
7. Per-isolate master table generation
8. Pooled exploratory statistical comparisons
9. Multiple-testing correction
10. BioProject and phylogroup sensitivity analyses
11. Publication-quality visualization

## Key operational definitions

### IntegronFinder structure classes

IntegronFinder outputs were treated as distinct structure categories:

- **complete integron**
- **CALIN**
- **In0**

These categories were not collapsed into a single biological entity for downstream linkage.

### Strict complete-integron ARG

A strict complete-integron ARG was defined as an AMRFinderPlus ARG interval whose genomic coordinates were **fully contained within** an IntegronFinder structure classified as **complete**.

Partial overlap, boundary overlap, same-contig proximity, CALIN association, and In0 association were not counted as strict complete-integron containment.

### MOB-recon context

ARGs linked to MOB-recon output were described as:

- **predicted plasmid-associated**
- **predicted chromosome-associated**

These are short-read assembly-based context predictions and do not establish definitive physical localization.

## Confirmed integrated outputs

- AMRFinderPlus AMR hits: **2,042**
- Unique AMR symbols: **84**
- AMR classes: **16**
- AMR subclasses: **26**
- IntegronFinder element rows: **959**
- IntegronFinder structures: **209**
- Integron-positive isolates: **122/189**
- Complete integrons: **60 structures**
- CALIN: **121 structures**
- In0: **28 structures**
- Strict complete-integron ARG hits: **116**
- Isolates carrying at least one strict complete-integron ARG: **58**
- Strict complete-integron ARGs predicted plasmid-associated: **108/116 (93.1%)**
- Strict complete-integron ARGs predicted chromosome-associated: **8/116 (6.9%)**

## Repository organization

```text
.
├── README.md
├── METHODS.md
├── WORKFLOW.md
├── environment/
│   └── software_versions.md
├── docs/
│   ├── data_dictionary.md
│   ├── reproducibility_notes.md
│   └── script_manifest.md
└── scripts/
    └── README.md
```

The original production scripts currently reside on the analysis VM under:

```text
/home/akhmadtaufiq2003/THESIS_WGS/00_scripts/
```

They should be copied into `scripts/` from the source VM rather than reconstructed from memory.

## Reproducibility status

This repository currently archives the verified analytical logic, definitions, known output locations, and statistical interpretation rules. Exact production scripts and remaining software-version records should be synchronized from the original VM before final publication or release.

## Interpretation constraint

Because collection group is completely confounded with BioProject, pooled bloodstream/invasive versus carriage comparisons are exploratory cross-study comparisons. Sensitivity analyses by BioProject and within major phylogroups are therefore essential components of interpretation.
