# Production script archive

The exact production-oriented scripts selected from the original Google Cloud VM archive were bundled on 2026-11-04 as:

```text
thesis_wgs_production_scripts.tar.gz
```

SHA-256:

```text
6917691ea5f9f3ed8374fa8252aba321f549d5ef0bd455e4cbe408e716280441
```

Archive size: approximately 44 KB.

## Included scripts

### Cohort and metadata
- freeze_final_cohort.py
- build_master_qc.py
- build_tree_annotation.py

### AMR
- consolidate_amrfinder_AMR_189_v2.py

### Mobilome
- run_mob_recon_189_v1.py
- consolidate_mob_recon_189_v1.py
- link_amrfinder_mobrecon_189_v2.py

### Integron
- run_integronfinder_189_v1.py
- consolidate_integronfinder_189.py
- link_amr_integron_189.py
- link_amr_integron_mob_189.py

### Integrated master/statistics
- build_integron_amr_mob_master_189.py
- stats_integron_amr_mob_collection_v2.py

### Sensitivity and confounding audit
- audit_collection_lineage_overlap_v1.py
- sensitivity_within_phylogroup_v1.py
- map_sra_to_bioproject_189.py
- bioproject_pairwise_sensitivity_v1.py
- build_final_results_table_v1.py

### Figures
- Figure_AMR_Mobilome_Burden_v2.py
- Figure_Integron_Composition_v2.py
- Supplementary_Figure_Sensitivity_v1.py

## Integrity check

After downloading the archive, verify with:

```bash
sha256sum thesis_wgs_production_scripts.tar.gz
```

Expected digest:

```text
6917691ea5f9f3ed8374fa8252aba321f549d5ef0bd455e4cbe408e716280441
```

The full original `00_scripts/` archive remains broader and contains exploratory, superseded, and legacy scripts. This production-only archive intentionally excludes those files from the primary reproducibility set.
