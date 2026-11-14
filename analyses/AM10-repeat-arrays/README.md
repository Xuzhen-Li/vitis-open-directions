# AM10 · Telomeres, centromeric satellites and rDNA arrays

## Tools

| Tool | Version | Role |
|---|---|---|
| tidk | 0.3.2 |  |
| TRF | 4.10.0rc2 |  |
| TRASH | [待确认: no tagged release] |  |
| quarTeT | 1.3.1 (GitHub release) |  |
| BLASTN / nhmmer | with rDNA and 5S seeds |  |

Each tool is listed once, at its latest release on 2026-11-14 (UTC+8): Bioconda or conda-forge unless the version says GitHub, PyPI or CRAN. Pin versions in one environment file per project. The Role column says which tool is the default, which is an alternative to it, and which is a later step. Older tools are listed in the catalogues linked below, not here.

## Steps

Telomere motif runs at chromosome ends and inside chromosomes; satellite discovery and monomer clustering in centromere windows; 45S and 5S rDNA unit search and array length per haplotype.

## Command sketch

```bash
tidk search -s TTTAGGG -o hap -d out hap.fa
nhmmer --tblout rdna.tbl rDNA_45S.hmm hap.fa
```

## Outputs

per-haplotype tables of telomere, satellite and rDNA arrays

## HPC resources (rough)

8 CPU, 16 GB per assembly

## Catalogue entries

- [vitis-pangenome §3 QC](https://github.com/Xuzhen-Li/vitis-pangenome#section-3)

## Used by projects

- [01. Telomeres and interstitial telomeric repeats across near-complete grape haplotypes](../../projects/01-telomere-and-interstitial-telomeric-repeats/)
- [02. 45S and 5S rDNA arrays in near-complete grape assemblies](../../projects/02-rdna-arrays/)
- [18. Centromeres of Vitis and Muscadinia, and a check of the chr7 fusion point](../../projects/18-vitis-muscadinia-centromeres/)
