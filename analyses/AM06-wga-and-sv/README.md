# AM06 · Whole-genome alignment, synteny and SVs from assemblies

## Tools

| Tool | Version | Role |
|---|---|---|
| minimap2 | 2.31 | default whole-genome alignment |
| SyRI | 1.8.2 | rearrangements from alignments |
| AnchorWave | 1.3.1 | alternative aligner for diverged genomes |
| MUMmer | 4.0.1 | alternative aligner |

Each tool is listed once, at its latest release on 2026-11-14 (UTC+8): Bioconda or conda-forge unless the version says GitHub, PyPI or CRAN. Pin versions in one environment file per project. The Role column says which tool is the default, which is an alternative to it, and which is a later step. Older tools are listed in the catalogues linked below, not here.

## Steps

Align each haplotype to PN_T2T; call SVs, inversions and translocations with SyRI; use AnchorWave for divergent species.

## Command sketch

```bash
minimap2 -ax asm5 --eqx ref.fa hap.fa | samtools sort -o hap.bam
syri -c hap.bam -r ref.fa -q hap.fa -F B --prefix hap.
```

## Outputs

SV VCF and synteny blocks per haplotype

## HPC resources (rough)

16 CPU, 64 GB, 1–4 h per haplotype; array

## Catalogue entries

- [vitis-pangenome §6 synteny](https://github.com/Xuzhen-Li/vitis-pangenome#section-6)
- [§4 variant discovery](https://github.com/Xuzhen-Li/vitis-pangenome#section-4)

## Used by projects

- [03. Endogenous florendovirus insertions across grape haplotypes](../../projects/03-endogenous-florendoviruses/)
- [14. TE insertion polymorphisms in cultivated grape from graph genotyping](../../projects/14-te-insertion-polymorphisms-cultivated/)
- [17. Large inversions: discovery in assemblies, population genotyping and suppressed recombination](../../projects/17-large-inversions-in-populations/)
- [18. Centromeres of Vitis and Muscadinia, and a check of the chr7 fusion point](../../projects/18-vitis-muscadinia-centromeres/)
