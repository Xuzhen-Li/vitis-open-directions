# AM07 · Pangenome graph build and genotyping

## Tools

| Tool | Version | Role |
|---|---|---|
| Minigraph-Cactus | 4.0.0 (Cactus GitHub release) | default graph build |
| PGGB | 0.7.4 | alternative graph build |
| vg | 1.78.0 (GitHub release) | giraffe mapping + vg call (one route) |
| PanGenie | 4.2.2 (GitHub release) | alternative genotyping route |
| odgi | 0.9.4 | graph statistics |
| panacus | 0.5.3 | growth curves |

Each tool is listed once, at its latest release on 2026-11-14 (UTC+8): Bioconda or conda-forge unless the version says GitHub, PyPI or CRAN. Pin versions in one environment file per project. The Role column says which tool is the default, which is an alternative to it, and which is a later step. Older tools are listed in the catalogues linked below, not here.

## Steps

Reuse the published Grapepan graph where possible. For locus graphs, extract the region from each haplotype and run PGGB. Genotype short reads with vg giraffe + vg call or PanGenie.

## Command sketch

```bash
vg giraffe -Z graph.gbz -m graph.min -d graph.dist -f r1.fq.gz -f r2.fq.gz > x.gam
PanGenie-index ...; PanGenie-genotype ...
```

## Outputs

graph, per-sample SV genotypes

## HPC resources (rough)

32–64 CPU, 256–512 GB for graph builds; 16 CPU, 64 GB per sample for giraffe

## Catalogue entries

- [vitis-pangenome §2 graph construction](https://github.com/Xuzhen-Li/vitis-pangenome#section-2)
- [§5 genotyping](https://github.com/Xuzhen-Li/vitis-pangenome#section-5)

## Used by projects

- [09. Graph genotyping of the berry colour locus](../../projects/09-berry-colour-locus-graph/)
- [14. TE insertion polymorphisms in cultivated grape from graph genotyping](../../projects/14-te-insertion-polymorphisms-cultivated/)
- [15. Introgression on a graph pangenome: wild-to-cultivated and hybrid cultivars](../../projects/15-graph-introgression/)
- [16. Inherited and clonal structural variants on a graph: where hemizygous SVs sit and why](../../projects/16-graph-sv-load/)
- [17. Large inversions: discovery in assemblies, population genotyping and suppressed recombination](../../projects/17-large-inversions-in-populations/)
- [20. Archaeological grape seeds: graph mapping and low-coverage imputation](../../projects/20-ancient-seeds-on-graph/)
- [21. Meta-analysis of public GWAS, cross-ancestry genomic prediction and SV markers](../../projects/21-gwas-meta-and-cross-ancestry-prediction/)
