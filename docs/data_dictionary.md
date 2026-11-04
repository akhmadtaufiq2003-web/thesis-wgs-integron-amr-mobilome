# Data dictionary

## Core identifiers

| Field | Meaning |
|---|---|
| `Experiment_Accession` | Sequencing experiment/run-level accession used as isolate key in downstream integration |
| `Master_ID` | Harmonized internal isolate identifier |
| `Analysis_Group` | Bloodstream/invasive or intestinal carriage analytical cohort |
| `Phylogroup` | *E. coli* phylogroup annotation |
| `ST` | Multilocus sequence type |
| `Serotype` | Serotype annotation |

## AMR linkage fields

| Field | Meaning |
|---|---|
| `AMR_Hit_ID` | Unique AMR hit identifier |
| `Element_symbol` | AMRFinderPlus gene/element symbol |
| `Element_name` | AMRFinderPlus element name |
| `Class` | AMR class |
| `Subclass` | AMR subclass |
| `Method` | AMRFinderPlus detection method |
| `AMR_Contig_Raw` | Original AMR contig identifier |
| `Normalized_Contig` | Harmonized contig identifier used for cross-tool linkage |
| `AMR_Start` | AMR interval start coordinate |
| `AMR_Stop` | AMR interval stop coordinate |

## Integron linkage fields

| Field | Meaning |
|---|---|
| `Integron_Relation` | Positional relationship between AMR interval and IntegronFinder structure |
| `Structure_Type` | IntegronFinder structure class, including complete, CALIN, or In0 |
| `Structure_UID` | Unique structure identifier |
| `Structure_Start` | Structure start coordinate |
| `Structure_End` | Structure end coordinate |
| `Distance_to_Structure_bp` | Distance from AMR interval to linked structure when applicable |
| `Isolate_Integron_Positive` | Isolate-level indicator for any IntegronFinder-detected structure |
| `Strict_Complete_Integron_ARG` | TRUE when AMR interval is fully contained within a complete IntegronFinder structure |

## MOB-recon field

| Field | Meaning |
|---|---|
| `MOB_Location_Prediction` | Predicted plasmid-associated or chromosome-associated context from MOB-recon |

## Important semantic rule

`MOB_Location_Prediction` is a computational prediction derived from short-read assemblies. It must not be described as experimentally confirmed plasmid or chromosome localization.
