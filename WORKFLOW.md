# Workflow

## Production root

The original analysis was run under:

```text
/home/akhmadtaufiq2003/THESIS_WGS
```

The script directory was:

```text
/home/akhmadtaufiq2003/THESIS_WGS/00_scripts
```

## Major workflow stages

### 1. Final metadata and cohort audit

Primary metadata:

```text
00_metadata/DATASET_AUDIT_MASTER/master_qc_illumina_final.tsv
00_metadata/tree_annotation_189.tsv
```

Final cohort size: 189 isolates.

### 2. AMR consolidation

Final consolidated AMRFinderPlus output:

```text
23_resistome_189/amrfinderplus_AMR_hits_189_v2.tsv
```

### 3. MOB-recon integration

Final AMR-MOB context table:

```text
24_mobilome_189/amr_mob_linkage_v2/amr_hits_with_mob_recon_context_189_v2.tsv
```

### 4. IntegronFinder consolidation

Batch root:

```text
25_integronfinder_189/batch_v1
```

Consolidated outputs:

```text
25_integronfinder_189/consolidated/integron_elements_189.tsv
25_integronfinder_189/consolidated/integron_structures_189.tsv
25_integronfinder_189/consolidated/integron_isolate_summary_189.tsv
```

### 5. ARG-integron linkage

```text
26_amr_integron_linkage_189/amr_integron_linkage_189.tsv
```

### 6. ARG-integron-MOB triple linkage

```text
27_amr_integron_mob_189/amr_integron_mob_context_189.tsv
```

The actual MOB-recon location field in this table is:

```text
MOB_Location_Prediction
```

### 7. Per-isolate master table

```text
28_integron_amr_mob_master_189/integron_amr_mob_master_189.tsv
```

### 8. Statistical outputs

```text
29_integron_amr_mob_stats_189/collection_binary_comparisons_v2.tsv
29_integron_amr_mob_stats_189/collection_burden_comparisons_v2.tsv
```

### 9. Final manuscript-oriented results table

```text
34_final_results_tables/TABLE_FINAL_integron_amr_mobilome_results_v1.tsv
```

### 10. Figures

Main burden figure:

```text
35_figures_integron_mobilome/Figure_AMR_Mobilome_Burden_v2.png
35_figures_integron_mobilome/Figure_AMR_Mobilome_Burden_v2.svg
35_figures_integron_mobilome/Figure_AMR_Mobilome_Burden_v2.pdf
```

Integron composition figure:

```text
36_figures_integron_composition/Figure_Integron_Composition_v2.png
36_figures_integron_composition/Figure_Integron_Composition_v2.svg
36_figures_integron_composition/Figure_Integron_Composition_v2.pdf
```

Sensitivity figure directory:

```text
37_figures_sensitivity/
```

## Recommended archival procedure

Before publication, copy the exact production scripts from the VM into this repository and export the relevant conda environment(s). Do not recreate production scripts from memory if the originals remain available.

Recommended checks:

1. Verify software versions from executable logs or `--version` output.
2. Archive the exact script corresponding to each final table/figure.
3. Record checksums for immutable final input tables if data-sharing policy permits.
4. Preserve accession-level metadata needed to reconstruct the cohort.
5. Do not upload raw FASTQ files to GitHub.
6. Do not claim plasmid/chromosome localization beyond MOB-recon's short-read prediction.
