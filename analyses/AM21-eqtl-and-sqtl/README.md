# AM21 · eQTL and splicing QTL

## Tools

| Tool | Version | Role |
|---|---|---|
| tensorQTL | 1.0.10 (PyPI) | cis-eQTL and sQTL mapping |
| LeafCutter | 2.0.3 (Bioconda) | intron clusters |
| regtools | 1.0.0 | junction extraction |
| plink2 | 2.00a5.10 | genotype files, PCs |
| GATK | 4.7.0.0 (GitHub release) | HaplotypeCaller on RNA-seq only for samples without DNA |

Each tool is listed once, at its latest release on 2026-11-14 (UTC+8): Bioconda or conda-forge unless the version says GitHub, PyPI or CRAN. Pin versions in one environment file per project. The Role column says which tool is the default, which is an alternative to it, and which is a later step. Older tools are listed in the catalogues linked below, not here.

## Steps

The unit of analysis is genotype × tissue: merge clones and duplicate samples using the AM04 KING thresholds before mapping. Map eQTL and sQTL only within subsets from one study and one tissue with many genotypes; combine across studies by meta-analysis rather than by pooling. Use genotypes from DNA of the same genotype; call genotypes from RNA-seq (GATK HaplotypeCaller in RNA mode) only for samples without DNA, check concordance on samples that have both, and use RNA-seq genotypes only in a sensitivity run, never in the primary analysis. Put all inputs on PN_T2T; convert older coordinates through the DS01 chain. Covariates: genetic PCs and a kinship-aware sensitivity run on deduplicated samples; the number of hidden factors is set by a sample-size rule before any eQTL result is seen. FDR: gene-level permutations (beta approximation) followed by Storey q-values; sQTL at the intron-cluster level, with intron clusters assigned to genes through the DS01 annotation (the same one used by salmon, STAR, and SnpEff). Junctions come from STAR BAMs with XS tags (AM15) [待确认: regtools 1.0.0 strand option].

## Command sketch

```bash
regtools junctions extract -s XS x.bam -o x.junc
python -m tensorqtl geno_prefix expr.bed.gz out --covariates cov.txt --mode cis
```

## Outputs

cis-eQTL and sQTL tables with permutation-based FDR

## HPC resources (rough)

8 CPU, 32 GB; GPU optional for tensorQTL

## Catalogue entries

- [vitis-pangenome §10 expression](https://github.com/Xuzhen-Li/vitis-pangenome#section-10)

## Used by projects

- [19. Public RNA-seq on PN_T2T: expression atlas, eQTL/sQTL and allele-specific expression](../../projects/19-public-rnaseq-on-t2t/)
