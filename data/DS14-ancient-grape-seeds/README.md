# DS14 · Archaeological grape seed sequencing

Target-enriched and shotgun data from archaeological seeds.

## Sources

| Part | Where |
|---|---|
| French seeds (Iron Age to medieval) | [PRJNA489970](https://www.ebi.ac.uk/ena/browser/view/PRJNA489970) (36 runs, 3.6 GB, targeted capture); genotypes [figshare 10.6084/m9.figshare.7610987](https://doi.org/10.6084/m9.figshare.7610987) |
| Cetamura del Chianti | [PRJEB89110](https://www.ebi.ac.uk/ena/browser/view/PRJEB89110) (141 runs, 131.7 GB; capture and WGS) |
| France, 4000 years (2026) | [PRJEB94459](https://www.ebi.ac.uk/ena/browser/view/PRJEB94459) (15,743 runs, 682.5 GB, WGS libraries) |
| Grotte di Pertosa | [PRJNA999173](https://www.ebi.ac.uk/ena/browser/view/PRJNA999173) (19 runs, 13.2 GB; WGS and capture) [待确认: linked paper] |

Sizes are sums of `fastq_bytes` from the ENA portal API or file sizes from the Zenodo API, read on 2026-11-14 (UTC+8). They are download sizes, not disk needs after processing.

## Licence and reuse

INSDC no restrictions; figshare licence [待确认].

## Download (sketch)

```bash
per BioProject filereport as DS10
```

## Preparation

Keep library-level metadata (capture vs shotgun, UDG treatment [待确认]).

## QC

Damage patterns with mapDamage2 (AM17).

Shared conventions (layout, manifests, naming, coordinates) are in [`docs/DATA_PREP.md`](../../docs/DATA_PREP.md).

## Cite

- Ramos-Madrigal et al. 2019. Palaeogenomic insights into the origins of French grapevine diversity. *Nature Plants*. [doi:10.1038/s41477-019-0437-5](https://doi.org/10.1038/s41477-019-0437-5)
- Inanli et al. 2026. Grapevine cultivation at Cetamura del Chianti: multiproxy evidence for centuries of continuity from the Etruscans to the Romans. *Journal of Archaeological Science*. [doi:10.1016/j.jas.2026.106605](https://doi.org/10.1016/j.jas.2026.106605)
- Noraz et al. 2026. Ancient DNA reveals 4000 years of grapevine diversity, viticulture and clonal propagation in France. *Nature Communications*. [doi:10.1038/s41467-026-70166-z](https://doi.org/10.1038/s41467-026-70166-z)
- Cohen et al. 2023. Ancient DNA from a lost Negev Highlands desert grape reveals a Late Antiquity wine lineage. *Proceedings of the National Academy of Sciences*. [doi:10.1073/pnas.2213563120](https://doi.org/10.1073/pnas.2213563120)

## Used by projects

- [20. Archaeological grape seeds: graph mapping and low-coverage imputation](../../projects/20-ancient-seeds-on-graph/)
