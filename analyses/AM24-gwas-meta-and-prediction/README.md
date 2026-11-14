# AM24 · GWAS meta-analysis and genomic prediction

## Tools

| Tool | Version | Role |
|---|---|---|
| METAL | 2020-05-05 (GitHub release) | fixed-effect meta-analysis |
| metafor | 5.2-1 (CRAN) | random effects (REML, Hartung–Knapp) |
| LDSC | 1.0.1 (Bioconda) | intercepts for overlap and inflation |
| GEMMA | 0.98.5 | per-study GWAS |
| regenie | 4.1.3.1 | alternative GWAS |
| BGLR | 1.1.4 (CRAN) | genomic prediction |
| rrBLUP | 4.6.3 (CRAN) | alternative prediction |

Each tool is listed once, at its latest release on 2026-11-14 (UTC+8): Bioconda or conda-forge unless the version says GitHub, PyPI or CRAN. Pin versions in one environment file per project. The Role column says which tool is the default, which is an alternative to it, and which is a later step. Older tools are listed in the catalogues linked below, not here.

## Steps

Harmonise alleles and positions on PN_T2T. Identify sample overlap between studies at the individual level with AM04; where individual data are missing, estimate overlap from LDSC intercepts and use an overlap-corrected meta-analysis; LDSC is used only above a minimum number of SNPs and samples fixed in advance. Effect sizes in the replication set are estimated from the replication set itself rather than carried over from discovery. Check each study's genomic-control λ or LDSC intercept and correct once, not twice. Meta-analyse with METAL (fixed effects) and metafor (random effects by REML with the Hartung–Knapp adjustment when fewer than five studies); discovery and replication study sets are disjoint and fixed in advance. Prediction: deduplicate with AM04 (one sample per genotype), keep clones and relatives in the same fold, perform all marker QC and selection inside training folds, report the largest training–test kinship, and compare with within-group cross-validation at matched sample size.

## Command sketch

```bash
metal metal_script.txt
```

## Outputs

Meta-analysis tables; prediction accuracy by train/test group

## HPC resources (rough)

8 CPU, 32 GB

## Catalogue entries

- [vitis-pangenome §11](https://github.com/Xuzhen-Li/vitis-pangenome#section-11)

## Used by projects

- [21. Meta-analysis of public GWAS, cross-ancestry genomic prediction and SV markers](../../projects/21-gwas-meta-and-cross-ancestry-prediction/)
