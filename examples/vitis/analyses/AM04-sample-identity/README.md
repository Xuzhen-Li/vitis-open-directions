# AM04 · Sample identity, clones and relatedness

## Tools

| Tool | Version | Role |
|---|---|---|
| plink2 | 2.00a5.10 |  |
| KING | 2.3.2 |  |
| VIVC | [vivc.de](https://www.vivc.de/) |  |

Each tool is listed once, at its latest release on 2026-11-14 (UTC+8): Bioconda or conda-forge unless the version says GitHub, PyPI or CRAN. Pin versions in one environment file per project. The Role column says which tool is the default, which is an alternative to it, and which is a later step. Older tools are listed in the catalogues linked below, not here.

## Steps

Compute KING kinship on LD-pruned SNPs; call duplicates and first-degree pairs; match names and synonyms to VIVC numbers; publish a harmonised sample sheet with one row per unique genotype. Within each clone group, keep the sample with the highest depth unless a project states otherwise.

## Command sketch

```bash
plink2 --vcf x.vcf.gz --indep-pairwise 50 5 0.2 --out prune
plink2 --vcf x.vcf.gz --extract prune.prune.in --make-king-table --out king
```

## Outputs

sample_sheet.tsv, duplicate groups, kinship table

## HPC resources (rough)

8 CPU, 32 GB, < 2 h

## Used by projects

- [08. A harmonised identity table for public grape resequencing panels](../../projects/08-harmonised-sample-panel/)
- [10. Ancestral recombination graphs for hundreds of grape genomes and domestication timing](../../projects/10-arg-domestication-timing/)
- [13. Somatic mutation spectra across grape cultivars, with rates where clone dates are known](../../projects/13-somatic-mutation-spectra-across-cultivars/)
- [16. Inherited and clonal structural variants on a graph: where hemizygous SVs sit and why](../../projects/16-graph-sv-load/)
- [19. Public RNA-seq on PN_T2T: expression atlas, eQTL/sQTL and allele-specific expression](../../projects/19-public-rnaseq-on-t2t/)
- [21. Meta-analysis of public GWAS, cross-ancestry genomic prediction and SV markers](../../projects/21-gwas-meta-and-cross-ancestry-prediction/)
