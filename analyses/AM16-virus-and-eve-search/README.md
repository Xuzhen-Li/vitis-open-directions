# AM16 · Virus discovery in RNA-seq and endogenous viral elements in assemblies

## Tools

| Tool | Version | Role |
|---|---|---|
| DIAMOND | 2.2.8 | protein search |
| MEGAHIT | 1.2.9 | default assembler |
| SPAdes (rnaviralSPAdes) | 4.3.0 | alternative assembler |
| CheckV | 1.1.1 | completeness |
| Kraken2 | 2.17.2 | first screen |

Each tool is listed once, at its latest release on 2026-11-14 (UTC+8): Bioconda or conda-forge unless the version says GitHub, PyPI or CRAN. Pin versions in one environment file per project. The Role column says which tool is the default, which is an alternative to it, and which is a later step. Older tools are listed in the catalogues linked below, not here.

## Steps

Remove host reads, assemble the rest, search viral proteins with DIAMOND, check completeness; for EVEs search caulimovirid proteins against each haplotype and cluster loci across haplotypes.

## Command sketch

```bash
diamond blastx -d viral.dmnd -q contigs.fa -o hits.tsv --sensitive
checkv end_to_end contigs.fa out
```

## Outputs

virus contigs per run, EVE locus table per haplotype

## HPC resources (rough)

16 CPU, 64 GB per run for assembly

## Used by projects

- [03. Endogenous florendovirus insertions across grape haplotypes](../../projects/03-endogenous-florendoviruses/)
- [04. Virus discovery across public grape RNA-seq and unmapped reads](../../projects/04-virus-discovery-in-public-data/)
