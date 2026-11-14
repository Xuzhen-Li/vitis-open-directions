# DS12 · Resequencing of 204 V. vinifera accessions (Magris et al. 2021)

European-focused cultivated and wild panel, used for origin and introgression of wine grapes.

## Sources

| Part | Where |
|---|---|
| Reads | [PRJNA373967](https://www.ebi.ac.uk/ena/browser/view/PRJNA373967) (443 runs, 2,238.9 GB; WGS plus RNA-seq and RAD-seq), [PRJNA390884](https://www.ebi.ac.uk/ena/browser/view/PRJNA390884) (1 run), [PRJNA385116](https://www.ebi.ac.uk/ena/browser/view/PRJNA385116) (7 runs, 87.6 GB), [PRJNA321480](https://www.ebi.ac.uk/ena/browser/view/PRJNA321480) (12 runs, 109.3 GB; Pinot clones) |

Sizes are sums of `fastq_bytes` from the ENA portal API or file sizes from the Zenodo API, read on 2026-11-14 (UTC+8). They are download sizes, not disk needs after processing.

## Licence and reuse

INSDC no restrictions.

## Download (sketch)

```bash
as DS10, one filereport per BioProject; keep only library_strategy=WGS
```

## Preparation

As DS10.

## QC

AM02, AM04.

Shared conventions (layout, manifests, naming, coordinates) are in [`docs/DATA_PREP.md`](../../docs/DATA_PREP.md).

## Cite

- Magris et al. 2021. The genomes of 204 Vitis vinifera accessions reveal the origin of European wine grapes. *Nature Communications*. [doi:10.1038/s41467-021-27487-y](https://doi.org/10.1038/s41467-021-27487-y)

## Used by projects

- [04. Virus discovery across public grape RNA-seq and unmapped reads](../../projects/04-virus-discovery-in-public-data/)
- [08. A harmonised identity table for public grape resequencing panels](../../projects/08-harmonised-sample-panel/)
- [09. Graph genotyping of the berry colour locus](../../projects/09-berry-colour-locus-graph/)
- [10. Ancestral recombination graphs for hundreds of grape genomes and domestication timing](../../projects/10-arg-domestication-timing/)
- [12. Convergent domestication: grape compared with other crops in one pipeline](../../projects/12-convergent-domestication-cross-crop/)
- [14. TE insertion polymorphisms in cultivated grape from graph genotyping](../../projects/14-te-insertion-polymorphisms-cultivated/)
- [15. Introgression on a graph pangenome: wild-to-cultivated and hybrid cultivars](../../projects/15-graph-introgression/)
- [16. Inherited and clonal structural variants on a graph: where hemizygous SVs sit and why](../../projects/16-graph-sv-load/)
- [20. Archaeological grape seeds: graph mapping and low-coverage imputation](../../projects/20-ancient-seeds-on-graph/)
- [21. Meta-analysis of public GWAS, cross-ancestry genomic prediction and SV markers](../../projects/21-gwas-meta-and-cross-ancestry-prediction/)
