# DS20 · Public grape small-RNA data

Small-RNA libraries across tissues, for phased siRNA (phasiRNA) work in flowers.

## Sources

| Part | Where |
|---|---|
| miRVine atlas | GEO [GSE59802](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE59802) (70 samples). Whether anthers or flowers at the right stage are included [待确认] |
| Other libraries | ENA query `tax_tree(3603) AND library_strategy="miRNA-Seq"` [待确认: count] |

Sizes are sums of `fastq_bytes` from the ENA portal API or file sizes from the Zenodo API, read on 2026-11-14 (UTC+8). They are download sizes, not disk needs after processing.

## Licence and reuse

GEO: no use restrictions; cite the study.

## Download (sketch)

```bash
prefetch $(cat gse59802_srr.txt) && fasterq-dump --split-files *.sra
```

## Preparation

Adapter trimming for small RNA; keep 20–24 nt reads.

## QC

Length distribution and known miRNA recovery.

Shared conventions (layout, manifests, naming, coordinates) are in [`docs/DATA_PREP.md`](../../docs/DATA_PREP.md).

## Cite

- Belli Kullan et al. 2015. miRVine: a microRNA expression atlas of grapevine based on small RNA sequencing. *BMC Genomics*. [doi:10.1186/s12864-015-1610-5](https://doi.org/10.1186/s12864-015-1610-5)

## Used by projects

- [22. Population-level evolution of the sex-determining region (demoted)](../../projects/22-sex-region-population-level/)
