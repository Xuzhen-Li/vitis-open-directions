# AM18 · Long-read SV calling

## Tools

| Tool | Version | Role |
|---|---|---|
| Sniffles2 | 2.8.1 | default caller |
| cuteSV | 2.1.4 | alternative caller |
| pbsv | 2.11.0 | alternative for PacBio |
| Jasmine | 1.1 | merging after calling |

Each tool is listed once, at its latest release on 2026-11-14 (UTC+8): Bioconda or conda-forge unless the version says GitHub, PyPI or CRAN. Pin versions in one environment file per project. The Role column says which tool is the default, which is an alternative to it, and which is a later step. Older tools are listed in the catalogues linked below, not here.

## Steps

Map HiFi/ONT reads, call SVs per sample, merge across samples, cross-check with assembly SVs (AM06).

## Command sketch

```bash
minimap2 -ax map-hifi ref.fa reads.fq.gz | samtools sort -o x.bam
sniffles --input x.bam --vcf x.vcf.gz
```

## Outputs

SV VCF per sample, merged set

## HPC resources (rough)

16 CPU, 64 GB per sample

## Catalogue entries

- [vitis-pangenome §4b SVs](https://github.com/Xuzhen-Li/vitis-pangenome#section-4)

## Used by projects

- [06. A genus-wide NLR catalogue with integrated domains and collapse checks](../../projects/06-vitis-pan-nlrome/)
- [15. Introgression on a graph pangenome: wild-to-cultivated and hybrid cultivars](../../projects/15-graph-introgression/)
- [16. Inherited and clonal structural variants on a graph: where hemizygous SVs sit and why](../../projects/16-graph-sv-load/)
- [17. Large inversions: discovery in assemblies, population genotyping and suppressed recombination](../../projects/17-large-inversions-in-populations/)
