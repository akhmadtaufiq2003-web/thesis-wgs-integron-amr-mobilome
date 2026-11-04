# Script manifest

The following production scripts are expected to exist under the original VM directory:

```text
/home/akhmadtaufiq2003/THESIS_WGS/00_scripts/
```

Known or workflow-referenced scripts include:

- `Figure_AMR_Mobilome_Burden_v2.py`
- `Figure_Integron_Composition_v2.py`
- `Supplementary_Figure_Sensitivity_v1.py`
- ARG-integron-MOB linkage script
- per-isolate master-table builder
- collection-level binary/burden statistics script
- collection-lineage overlap audit script
- within-phylogroup sensitivity script
- SRA-to-BioProject mapping script
- BioProject pairwise sensitivity script
- final-results-table builder

Exact filenames for scripts not explicitly preserved in the current archive should be obtained from the VM rather than inferred.

## Archival target

Each committed production script should be accompanied by:

1. source path on VM
2. intended input files
3. intended output files
4. interpreter/environment
5. date or commit when archived
