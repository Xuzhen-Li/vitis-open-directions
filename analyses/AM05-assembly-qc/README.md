# AM05 · Assembly QC

## Tools

| Tool | Version | Role |
|---|---|---|
| compleasm | 0.2.10 | default gene completeness |
| BUSCO | 6.1.0 | alternative to compleasm |
| Merqury | 1.4.1 | k-mer QV where reads exist |
| seqkit | 2.14.0 | length statistics |

Each tool is listed once, at its latest release on 2026-11-14 (UTC+8): Bioconda or conda-forge unless the version says GitHub, PyPI or CRAN. Pin versions in one environment file per project. The Role column says which tool is the default, which is an alternative to it, and which is a later step. Older tools are listed in the catalogues linked below, not here.

## Steps

Completeness with compleasm (eudicots_odb12 [待确认 lineage name]); k-mer QV with Merqury where reads exist; contiguity and gap counts; telomere ends via AM10.

## Command sketch

```bash
compleasm run -a hap.fa -o out -l eudicots -t 16
merqury.sh reads.meryl hap.fa out
```

## Outputs

per-assembly QC table

## HPC resources (rough)

16 CPU, 64 GB, 1–3 h per assembly; array

## Catalogue entries

- [gene-structure-annotation §1 assembly QC](https://github.com/Xuzhen-Li/gene-structure-annotation#section-1)
- [vitis-pangenome §3 assembly and graph QC](https://github.com/Xuzhen-Li/vitis-pangenome#section-3)

## Used by projects

- [01. Telomeres and interstitial telomeric repeats across near-complete grape haplotypes](../../projects/01-telomere-and-interstitial-telomeric-repeats/)
- [02. 45S and 5S rDNA arrays in near-complete grape assemblies](../../projects/02-rdna-arrays/)
- [03. Endogenous florendovirus insertions across grape haplotypes](../../projects/03-endogenous-florendoviruses/)
- [05. Gene presence/absence across grape pangenomes under one pipeline](../../projects/05-gene-pav-across-pangenomes/)
- [06. A genus-wide NLR catalogue with integrated domains and collapse checks](../../projects/06-vitis-pan-nlrome/)
- [07. Copy number and birth–death of stilbene and aroma gene families (STS, TPS, CCD, LOX)](../../projects/07-metabolic-gene-families/)
- [14. TE insertion polymorphisms in cultivated grape from graph genotyping](../../projects/14-te-insertion-polymorphisms-cultivated/)
- [17. Large inversions: discovery in assemblies, population genotyping and suppressed recombination](../../projects/17-large-inversions-in-populations/)
- [18. Centromeres of Vitis and Muscadinia, and a check of the chr7 fusion point](../../projects/18-vitis-muscadinia-centromeres/)
