# AM09 · Gene presence/absence and copy number

## Tools

| Tool | Version | Role |
|---|---|---|
| Liftoff | 1.6.3 |  |
| OrthoFinder | 3.2 |  |
| mosdepth | 0.3.14 |  |
| miniprot | 0.18 |  |

Each tool is listed once, at its latest release on 2026-11-14 (UTC+8): Bioconda or conda-forge unless the version says GitHub, PyPI or CRAN. Pin versions in one environment file per project. The Role column says which tool is the default, which is an alternative to it, and which is a later step. Older tools are listed in the catalogues linked below, not here.

## Steps

Call gene PAV from orthogroups and from liftover; confirm each absence with read depth and with a sequence search on the haplotype, so annotation misses are separated from real deletions.

## Command sketch

```bash
liftoff -g ref.gff3 -o hap.lift.gff3 hap.fa ref.fa
mosdepth -b genes.bed sample sample.bam
```

## Outputs

PAV matrix with evidence class per cell

## HPC resources (rough)

8 CPU, 32 GB per haplotype

## Catalogue entries

- [vitis-pangenome §7 gene PAV](https://github.com/Xuzhen-Li/vitis-pangenome#section-7)
- [gene-structure-annotation §7 lift-over](https://github.com/Xuzhen-Li/gene-structure-annotation#section-7)

## Used by projects

- [05. Gene presence/absence across grape pangenomes under one pipeline](../../projects/05-gene-pav-across-pangenomes/)
- [06. A genus-wide NLR catalogue with integrated domains and collapse checks](../../projects/06-vitis-pan-nlrome/)
- [07. Copy number and birth–death of stilbene and aroma gene families (STS, TPS, CCD, LOX)](../../projects/07-metabolic-gene-families/)
