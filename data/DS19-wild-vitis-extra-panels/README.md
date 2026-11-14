# DS19 · Extra wild Vitis panels (V. riparia, V. californica, 40 Vitis species)

Smaller wild panels used as donors or outgroups for introgression and ancestry work.

## Sources

| Part | Where |
|---|---|
| Introgression panel (2023) | [PRJNA910315](https://www.ebi.ac.uk/ena/browser/view/PRJNA910315) (40 runs, 266.7 GB, WGS); NGDC mirror PRJCA016655 [待确认: run count] |
| *V. riparia* | [PRJNA512170](https://www.ebi.ac.uk/ena/browser/view/PRJNA512170) (49 runs, 202.0 GB, WGS) |
| 40 Vitis species | [PRJNA490319](https://www.ebi.ac.uk/ena/browser/view/PRJNA490319) (41 runs, 329.0 GB, WGS; one or two samples per species) [待确认: linked paper] |

Sizes are sums of `fastq_bytes` from the ENA portal API or file sizes from the Zenodo API, read on 2026-11-14 (UTC+8). They are download sizes, not disk needs after processing.

## Licence and reuse

INSDC no restrictions.

## Download (sketch)

```bash
per BioProject filereport as DS10
```

## Preparation

Species labels from ENA `scientific_name`; check them against the phylogeny before use as donors.

## QC

AM02, AM04.

Shared conventions (layout, manifests, naming, coordinates) are in [`docs/DATA_PREP.md`](../../docs/DATA_PREP.md).

## Cite

- Xiao et al. 2023. Adaptive and maladaptive introgression in grapevine domestication. *Proceedings of the National Academy of Sciences*. [doi:10.1073/pnas.2222041120](https://doi.org/10.1073/pnas.2222041120)
- Girollet et al. 2019. De novo phased assembly of the Vitis riparia grape genome. *Scientific Data*. [doi:10.1038/s41597-019-0133-3](https://doi.org/10.1038/s41597-019-0133-3)

## Used by projects

- [15. Introgression on a graph pangenome: wild-to-cultivated and hybrid cultivars](../../projects/15-graph-introgression/)
