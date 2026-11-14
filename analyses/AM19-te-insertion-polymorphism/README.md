# AM19 · TE insertion polymorphisms among haplotypes

## Tools

| Tool | Version | Role |
|---|---|---|
| GraffiTE | 1.1.0.0 (GitHub release) |  |
| McClintock 2 | 2.0.0 (GitHub release) |  |
| RepeatMasker | 4.2.4 |  |
| minimap2 | 2.31 |  |

Each tool is listed once, at its latest release on 2026-11-14 (UTC+8): Bioconda or conda-forge unless the version says GitHub, PyPI or CRAN. Pin versions in one environment file per project. The Role column says which tool is the default, which is an alternative to it, and which is a later step. Older tools are listed in the catalogues linked below, not here.

## Steps

Use a curated Vitis TE library (built in vitis-te, not here). Call insertion presence/absence among haplotype assemblies from assembly alignments, then genotype the insertions in short-read panels through a graph.

## Command sketch

```bash
GraffiTE --assemblies asm.tsv --TE_library vitis_te.fa --reference ref.fa --out tip  # option names [待确认]
```

## Outputs

TE insertion VCF across haplotypes and samples

## HPC resources (rough)

16–32 CPU, 128 GB

## Catalogue entries

- [vitis-pangenome §4b SVs and TE insertions](https://github.com/Xuzhen-Li/vitis-pangenome#section-4)
- [vitis-te (TE library)](https://github.com/Xuzhen-Li/vitis-te)

## Used by projects

- [14. TE insertion polymorphisms in cultivated grape from graph genotyping](../../projects/14-te-insertion-polymorphisms-cultivated/)
