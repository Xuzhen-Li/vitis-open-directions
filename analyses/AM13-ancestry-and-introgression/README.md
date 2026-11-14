# AM13 · Ancestry and introgression

## Tools

| Tool | Version | Role |
|---|---|---|
| ADMIXTURE | 1.3.0 | ancestry proportions |
| Dsuite | [待确认: no tagged release] | D, f4, f_dM with block jackknife |
| ADMIXTOOLS 2 | 2.0.1 (GitHub release) | f-statistics, alternative |
| SHAPEIT5 | 5.1.1 | phasing before local ancestry |
| RFMix | 2.03.r0.9505bfa | local ancestry |

Each tool is listed once, at its latest release on 2026-11-14 (UTC+8): Bioconda or conda-forge unless the version says GitHub, PyPI or CRAN. Pin versions in one environment file per project. The Role column says which tool is the default, which is an alternative to it, and which is a later step. Older tools are listed in the catalogues linked below, not here.

## Steps

Ancestry proportions; Compute D and f4 statistics with block-jackknife Z scores (with block size fixed in advance and larger than the LD-decay distance), using *Muscadinia* or distant *Vitis* as outgroup; compute windowed f_dM for local signals; phase with SHAPEIT5; infer local ancestry along chromosomes with RFMix, using reference panels chosen before the run. Separate introgression from incomplete lineage sorting using tract-length tests against coalescent simulations without introgression.

## Command sketch

```bash
admixture --cv x.bed K
Dsuite Dtrios x.vcf.gz sets.txt
Dsuite Dinvestigate -w 50,25 x.vcf.gz sets.txt trios.txt
```

## Outputs

Q matrices, D/f4 tables, introgressed windows

## HPC resources (rough)

8 CPU, 32 GB

## Catalogue entries

- [vitis-pangenome §11](https://github.com/Xuzhen-Li/vitis-pangenome#section-11)

## Used by projects

- [15. Introgression on a graph pangenome: wild-to-cultivated and hybrid cultivars](../../projects/15-graph-introgression/)
- [20. Archaeological grape seeds: graph mapping and low-coverage imputation](../../projects/20-ancient-seeds-on-graph/)
