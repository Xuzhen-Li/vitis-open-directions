# DS06 · Vitis amurensis haplotype assemblies and 330-sample resequencing

Eight haplotype-resolved V. amurensis genomes, a graph pangenome and population resequencing of a cold-hardy wild species.

## Sources

| Part | Where |
|---|---|
| Assemblies | BioProjects PRJNA1272278–PRJNA1272285; pangenome and annotations [zenodo.16534920](https://doi.org/10.5281/zenodo.16534920) (2.31 GB, CC BY 4.0) |
| HiFi/Hi-C | [PRJNA1308837](https://www.ebi.ac.uk/ena/browser/view/PRJNA1308837) (8 runs, 192.6 GB) |
| Resequencing | [PRJNA1089859](https://www.ebi.ac.uk/ena/browser/view/PRJNA1089859) (330 runs, 3,609.4 GB); NGDC PRJCA046381 [待确认] |

Sizes are sums of `fastq_bytes` from the ENA portal API or file sizes from the Zenodo API, read on 2026-11-14 (UTC+8). They are download sizes, not disk needs after processing.

## Licence and reuse

Zenodo CC BY 4.0; INSDC no restrictions.

## Download (sketch)

```bash
zenodo_get 16534920 -o vamur
```

## Preparation

Sample sheet with collection coordinates from BioSample attributes, if present [待确认].

## QC

AM04 identity and relatedness before any population statistic.

Shared conventions (layout, manifests, naming, coordinates) are in [`docs/DATA_PREP.md`](../../../../templates/DATA_PREP.md).

## Cite

- Ma et al. 2026. Population genomics reveals association of transposable elements variants with climatic adaptation in wild Amur grape. *Nature Communications*. [doi:10.1038/s41467-026-70026-w](https://doi.org/10.1038/s41467-026-70026-w)

## Used by projects

- [03. Endogenous florendovirus insertions across grape haplotypes](../../projects/03-endogenous-florendoviruses/)
- [05. Gene presence/absence across grape pangenomes under one pipeline](../../projects/05-gene-pav-across-pangenomes/)
- [06. A genus-wide NLR catalogue with integrated domains and collapse checks](../../projects/06-vitis-pan-nlrome/)
- [10. Ancestral recombination graphs for hundreds of grape genomes and domestication timing](../../projects/10-arg-domestication-timing/)
