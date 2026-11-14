# AM11 · Diversity and selection scans

## Tools

| Tool | Version | Role |
|---|---|---|
| pixy | 2.2.4 (conda-forge) |  |
| vcftools | 0.1.17 |  |
| RAiSD | [待确认] |  |
| XP-CLR | 1.1.2 |  |

Each tool is listed once, at its latest release on 2026-11-14 (UTC+8): Bioconda or conda-forge unless the version says GitHub, PyPI or CRAN. Pin versions in one environment file per project. The Role column says which tool is the default, which is an alternative to it, and which is a later step. Older tools are listed in the catalogues linked below, not here.

## Steps

pi, dxy and Fst from all-sites VCF in windows; selection scans contrasting wild and cultivated groups after clone removal (AM04).

## Command sketch

```bash
pixy --stats pi fst dxy --vcf allsites.vcf.gz --populations pops.txt --window_size 50000
```

## Outputs

window statistics, outlier regions

## HPC resources (rough)

8 CPU, 32 GB per chromosome

## Catalogue entries

- [vitis-pangenome §11 evolution and ancestry](https://github.com/Xuzhen-Li/vitis-pangenome#section-11)

## Used by projects

- [12. Convergent domestication: grape compared with other crops in one pipeline](../../projects/12-convergent-domestication-cross-crop/)
