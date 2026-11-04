# Script manifest

Authoritative source directory on the original Google Cloud VM:

```text
/home/akhmadtaufiq2003/THESIS_WGS/00_scripts/
```

The uploaded VM archive was audited on 2026-11-04. The production-oriented script set below was selected because it corresponds to the final cohort, AMR, mobilome, integron, statistical, sensitivity, and figure workflow. All selected Python scripts passed `python3 -m py_compile` during the archive audit.

## Core cohort and metadata

- `freeze_final_cohort.py`
- `build_master_qc.py`
- `build_tree_annotation.py`

## AMR consolidation

- `consolidate_amrfinder_AMR_189_v2.py`

Earlier v1 files remain part of the VM provenance but are not designated as the final AMR consolidation script.

## MOB-recon workflow

- `run_mob_recon_189_v1.py`
- `consolidate_mob_recon_189_v1.py`
- `link_amrfinder_mobrecon_189_v2.py`

The v2 AMRFinderPlus-MOB-recon linkage is preferred over v1 because it includes the corrected Bactopia-to-MOB-recon contig identifier transformation.

## IntegronFinder workflow

- `run_integronfinder_189_v1.py`
- `consolidate_integronfinder_189.py`
- `link_amr_integron_189.py`
- `link_amr_integron_mob_189.py`

## Integrated master table and primary statistics

- `build_integron_amr_mob_master_189.py`
- `stats_integron_amr_mob_collection_v2.py`

The v2 statistics script is the designated final pooled-analysis script.

## Confounding and sensitivity analysis

- `audit_collection_lineage_overlap_v1.py`
- `sensitivity_within_phylogroup_v1.py`
- `map_sra_to_bioproject_189.py`
- `bioproject_pairwise_sensitivity_v1.py`
- `build_final_results_table_v1.py`

## Final figures

- `Figure_AMR_Mobilome_Burden_v2.py`
- `Figure_Integron_Composition_v2.py`
- `Supplementary_Figure_Sensitivity_v1.py`

## Legacy / exploratory scripts

The VM archive also contains earlier versions and scripts for resistome exploratory analysis, virulence analysis, phylogeny visualization, Panaroo/accessory-genome analysis, and multiple draft figure versions. These are retained in the original VM archive for provenance but are intentionally excluded from the primary reproducibility pipeline for this repository.

Examples include:

- earlier `analyze_*` versions
- `Figure_Integron_Composition_v1.py`
- `figure_amr_mobilome_burden_v1.py`
- `stats_integron_amr_mob_collection_v1.py`
- multiple `plot_core_phylogeny_*.R` iterations
- multiple virulence and resistome plotting drafts

## Validation status

- Production-oriented Python scripts selected above: syntax validation passed.
- The original uploaded script archive size was approximately 335 KB compressed.
- Production scripts should be copied byte-for-byte from the original VM archive. They should not be reconstructed from prose or memory.

## Important archival principle

The repository documentation already records the analytical logic and output paths. The next provenance step is to synchronize the exact production script files themselves from the original VM into `scripts/`.

Recommended repository organization:

```text
scripts/
├── 00_cohort/
├── 01_amr/
├── 02_mobilome/
├── 03_integron/
├── 04_statistics/
├── 05_sensitivity/
└── 06_figures/
```

Each production script should remain unchanged from the version actually used to generate the final outputs. Any later refactoring should be committed separately and clearly labelled.
