# AM25 · Small-RNA and phasiRNA loci

## Tools

| Tool | Version | Role |
|---|---|---|
| fastp | 1.4.0 | adapter trimming |
| ShortStack | 4.1.2 | alignment, multi-mapper placement, and phased-locus calls |
| samtools | 1.25 | BAM handling |

Each tool is listed once, at its latest release on 2026-11-14 (UTC+8): Bioconda or conda-forge unless the version says GitHub, PyPI or CRAN. Pin versions in one environment file per project. The Role column says which tool is the default, which is an alternative to it, and which is a later step. Older tools are listed in the catalogues linked below, not here.

## Steps

Trim adapters; keep 20–24 nt reads; align end to end with at most one mismatch and place multi-mapping reads using ShortStack's local-weighting rule; call phased loci with ShortStack's phasing score; compare by flower sex type [待确认: parameters not yet checked against small-RNA benchmarks].

## Command sketch

```bash
ShortStack --readfile x.trim.fq.gz --genomefile pn_t2t.fa --mmap u --threads 8 --outdir ss_x
```

## Outputs

phasiRNA loci and their expression by tissue

## HPC resources (rough)

8 CPU, 16 GB per library

## Used by projects

- [22. Population-level evolution of the sex-determining region (demoted)](../../projects/22-sex-region-population-level/)
