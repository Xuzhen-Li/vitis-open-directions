# AM08 · Gene-family search across haplotypes

## Tools

| Tool | Version | Role |
|---|---|---|
| miniprot | 0.18 |  |
| HMMER | 3.4 |  |
| InterProScan | 6 (EBI; release tag [待确认]) |  |
| OrthoFinder | 3.2 |  |
| AGAT | 1.7.0 |  |
| eggNOG-mapper | 2.1.15 |  |
| CAFE | 5.1.0 |  |

Each tool is listed once, at its latest release on 2026-11-14 (UTC+8): Bioconda or conda-forge unless the version says GitHub, PyPI or CRAN. Pin versions in one environment file per project. The Role column says which tool is the default, which is an alternative to it, and which is a later step. Older tools are listed in the catalogues linked below, not here.

## Steps

Use published annotations first. Re-find family members on every haplotype with miniprot (protein-to-genome) plus HMM domain search, so missed or fragmented models are counted. Classify domains, build trees, place members on the genome.

## Command sketch

```bash
miniprot -t 16 --gff hap.fa family_seeds.faa > hits.gff
hmmsearch --domtblout dom.tsv PF00931.hmm proteins.faa
```

## Outputs

member table per haplotype (complete/partial/pseudogene), trees

## HPC resources (rough)

16 CPU, 32 GB, < 2 h per haplotype

## Catalogue entries

- [gene-structure-annotation §4 protein evidence](https://github.com/Xuzhen-Li/gene-structure-annotation#section-4)
- [gene-function-annotation §3 domains](https://github.com/Xuzhen-Li/gene-function-annotation#section-3)
- [§9 plant gene families](https://github.com/Xuzhen-Li/gene-function-annotation#section-9)

## Used by projects

- [05. Gene presence/absence across grape pangenomes under one pipeline](../../projects/05-gene-pav-across-pangenomes/)
- [06. A genus-wide NLR catalogue with integrated domains and collapse checks](../../projects/06-vitis-pan-nlrome/)
- [07. Copy number and birth–death of stilbene and aroma gene families (STS, TPS, CCD, LOX)](../../projects/07-metabolic-gene-families/)
