# DS22 · Public grape phenotypes, GWAS summary statistics and variant call sets

Inputs for meta-analysis and genomic prediction. Most grape GWAS do not release full summary statistics, so this module starts with an inventory.

## Sources

| Part | Where |
|---|---|
| Bordeaux germplasm call sets | [PRJEB123002](https://www.ebi.ac.uk/ena/browser/view/PRJEB123002) (variant call sets of a diverse germplasm collection; no read runs) [待确认: linked paper] |
| Grapepan GWAS | phenotypes and association results in the paper's supplementary tables [待确认] |
| Across-population prediction | data availability as stated in the cited 2022 study [待确认] |

Sizes are sums of `fastq_bytes` from the ENA portal API or file sizes from the Zenodo API, read on 2026-11-14 (UTC+8). They are download sizes, not disk needs after processing.

## Licence and reuse

Per source [待确认].

## Download (sketch)

```bash
# inventory first: for each GWAS paper record trait, n, genotype platform, whether summary statistics are public, and the URL
```

## Preparation

Harmonise trait names and units; lift positions to PN_T2T (DS01).

## QC

Allele and strand checks against the PN_T2T reference.

Shared conventions (layout, manifests, naming, coordinates) are in [`docs/DATA_PREP.md`](../../../../templates/DATA_PREP.md).

## Cite

- Liu et al. 2024. Grapevine pangenome facilitates trait genetics and genomic breeding. *Nature Genetics*. [doi:10.1038/s41588-024-01967-5](https://doi.org/10.1038/s41588-024-01967-5)
- Brault et al. 2022. Across-population genomic prediction in grapevine opens up promising prospects for breeding. *Horticulture Research*. [doi:10.1093/hr/uhac041](https://doi.org/10.1093/hr/uhac041)

## Used by projects

- [21. Meta-analysis of public GWAS, cross-ancestry genomic prediction and SV markers](../../projects/21-gwas-meta-and-cross-ancestry-prediction/)
