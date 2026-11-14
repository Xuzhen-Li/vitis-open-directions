# AM23 · Cross-crop orthology and convergence tests

## Tools

| Tool | Version | Role |
|---|---|---|
| OrthoFinder | 3.2 |  |
| MAFFT | 7.526 (conda-forge) |  |
| IQ-TREE | 3.1.4 |  |
| HyPhy | 2.5.104 |  |

Each tool is listed once, at its latest release on 2026-11-14 (UTC+8): Bioconda or conda-forge unless the version says GitHub, PyPI or CRAN. Pin versions in one environment file per project. The Role column says which tool is the default, which is an alternative to it, and which is a later step. Older tools are listed in the catalogues linked below, not here.

## Steps

Run the same selection scan (AM11) on each crop. Map genes to orthogroups; handle one-to-many orthologues from lineage-specific duplications (the gamma triplication is shared by all core eudicots). Build a null by permuting genes within matched bins (length, family size, recombination proxy).

## Command sketch

```bash
orthofinder -f proteomes/ -t 32
```

## Outputs

Orthogroup table; per-crop selected-gene sets; overlap statistics against the null

## HPC resources (rough)

32 CPU, 128 GB for OrthoFinder

## Catalogue entries

- [gene-function-annotation §9](https://github.com/Xuzhen-Li/gene-function-annotation#section-9)

## Used by projects

- [12. Convergent domestication: grape compared with other crops in one pipeline](../../projects/12-convergent-domestication-cross-crop/)
