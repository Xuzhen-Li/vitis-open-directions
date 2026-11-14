# AM02 · Read QC and trimming

## Tools

| Tool | Version | Role |
|---|---|---|
| fastp | 1.4.0 | trimming |
| MultiQC | 1.35 | report |
| seqkit | 2.14.0 | read statistics |

Each tool is listed once, at its latest release on 2026-11-14 (UTC+8): Bioconda or conda-forge unless the version says GitHub, PyPI or CRAN. Pin versions in one environment file per project. The Role column says which tool is the default, which is an alternative to it, and which is a later step. Older tools are listed in the catalogues linked below, not here.

## Steps

fastp per run with default adapter detection; MultiQC report per dataset; drop runs below a coverage or quality floor set per project.

## Command sketch

```bash
fastp -i R1.fq.gz -I R2.fq.gz -o t1.fq.gz -O t2.fq.gz -j run.json -h run.html -w 8
multiqc .
```

## Outputs

trimmed reads, MultiQC HTML

## HPC resources (rough)

8 CPU, 16 GB, 1–2 h per run; array over runs

## Used by projects

- [04. Virus discovery across public grape RNA-seq and unmapped reads](../../projects/04-virus-discovery-in-public-data/)
- [08. A harmonised identity table for public grape resequencing panels](../../projects/08-harmonised-sample-panel/)
- [11. Sequence-to-expression models and plant foundation models evaluated on grape](../../projects/11-sequence-to-function-models/)
- [13. Somatic mutation spectra across grape cultivars, with rates where clone dates are known](../../projects/13-somatic-mutation-spectra-across-cultivars/)
- [19. Public RNA-seq on PN_T2T: expression atlas, eQTL/sQTL and allele-specific expression](../../projects/19-public-rnaseq-on-t2t/)
