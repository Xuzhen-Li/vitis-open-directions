# AM17 · Ancient DNA processing

## Tools

| Tool | Version | Role |
|---|---|---|
| nf-core/eager | 2.5.3 |  |
| mapDamage2 | 2.2.3 |  |
| vg | 1.78.0 (GitHub release) |  |
| GLIMPSE2 | 2.0.1 (Bioconda glimpse-bio) |  |

Each tool is listed once, at its latest release on 2026-11-14 (UTC+8): Bioconda or conda-forge unless the version says GitHub, PyPI or CRAN. Pin versions in one environment file per project. The Role column says which tool is the default, which is an alternative to it, and which is a later step. Older tools are listed in the catalogues linked below, not here.

## Steps

Process with nf-core/eager; check damage; map to the linear reference and to the graph; compare allele balance at known heterozygous sites; impute with GLIMPSE2 using a modern reference panel, after testing accuracy on modern samples downsampled to ancient depths.

## Command sketch

```bash
mapDamage -i x.bam -r ref.fa
```

## Outputs

damage profiles, genotypes

## HPC resources (rough)

8 CPU, 32 GB per sample

## Catalogue entries

- [vitis-pangenome §14 ideas (ancient DNA on graphs)](https://github.com/Xuzhen-Li/vitis-pangenome#section-14)

## Used by projects

- [20. Archaeological grape seeds: graph mapping and low-coverage imputation](../../projects/20-ancient-seeds-on-graph/)
