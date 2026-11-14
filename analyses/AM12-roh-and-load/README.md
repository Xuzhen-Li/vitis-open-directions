# AM12 · Runs of homozygosity and deleterious load

## Tools

| Tool | Version | Role |
|---|---|---|
| bcftools roh | 1.25 | ROH |
| SnpEff | 5.4.0c | annotation with the DS01 annotation |
| PlantCaduceus | [GitHub](https://github.com/plantcad/plantcad), version [待确认] | optional variant-effect scores |

Each tool is listed once, at its latest release on 2026-11-14 (UTC+8): Bioconda or conda-forge unless the version says GitHub, PyPI or CRAN. Pin versions in one environment file per project. The Role column says which tool is the default, which is an alternative to it, and which is a later step. Older tools are listed in the catalogues linked below, not here.

## Steps

Estimate ROH per sample with bcftools roh using allele frequencies estimated per population after removing clones (AM04), rather than a default frequency. Annotate variants with SnpEff using a database built from the DS01 annotation. Count load on derived alleles (polarised in AM26), rather than on non-reference alleles, because PN_T2T comes from the nearly homozygous PN40024. Report load with and without ROH as a covariate.

## Command sketch

```bash
bcftools roh -G30 --AF-file pop_af.tab.gz x.vcf.gz -o roh.txt
snpEff ann PN_T2T_RS2023_09 x.vcf.gz > x.ann.vcf
```

## Outputs

ROH tables, load per sample

## HPC resources (rough)

4 CPU, 16 GB per chromosome

## Catalogue entries

- [vitis-pangenome §14 ideas (variant-effect models)](https://github.com/Xuzhen-Li/vitis-pangenome#section-14)

## Used by projects

- [16. Inherited and clonal structural variants on a graph: where hemizygous SVs sit and why](../../projects/16-graph-sv-load/)
