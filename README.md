# vitis-open-directions

Research directions in grapevine (*Vitis*) genomics that can be done with public data only, each written as a runnable plan from download to planned figures. [中文](README.zh.md)

This repository is the analysis guide for three catalogue repositories. The catalogues list tools and methods; this repository says which public data to use, which steps to run, and what question each project answers. Tools are described in the catalogues and only linked from here.

| Repository | What it holds |
|---|---|
| [vitis-pangenome](https://github.com/Xuzhen-Li/vitis-pangenome) | Grape pangenome methods: assembly, graphs, SVs, population genomics |
| [gene-structure-annotation](https://github.com/Xuzhen-Li/gene-structure-annotation) | Gene structure annotation tools and workflows |
| [gene-function-annotation](https://github.com/Xuzhen-Li/gene-function-annotation) | Gene function annotation tools and workflows |
| vitis-open-directions (this one) | Public datasets, shared analysis steps and ranked projects |

Status: draft v0.3.2 (2026-11-14). Scores were frozen on 2026-11-14; later changes are logged in the ranking page. Novelty checks and estimates remain drafts. Pages and status tables were last updated on 2026-11-21.

## Ways in

- **By project**: [`examples/vitis/projects/`](examples/vitis/projects/) has one folder per project with the gap, existing work, question, hypotheses and criteria, data, steps, paper split, risks and a plan for a SLURM cluster.
- **By dataset**: [`examples/vitis/data/`](examples/vitis/data/) has one folder per public dataset: where it is, size, licence, download, preparation and QC.
- **By analysis step**: [`examples/vitis/analyses/`](examples/vitis/analyses/) has one folder per reusable step: tools at their latest release, commands, outputs and rough HPC resources.
- **By paper**: [`examples/vitis/INDEX.md`](examples/vitis/INDEX.md) shows which modules each project uses and how each project splits into papers.
- [`examples/vitis/RANKING.md`](examples/vitis/RANKING.md): scores and reasons for the order.
- [`examples/vitis/NOT_KEPT.md`](examples/vitis/NOT_KEPT.md): directions that were checked and left out, with the papers that already cover them.
- [`templates/PREREGISTRATION.md`](templates/PREREGISTRATION.md): the template to fill in before any analysis.
- [`templates/DATA_PREP.md`](templates/DATA_PREP.md) and [`templates/HPC_JOBS.md`](templates/HPC_JOBS.md): shared conventions and the job template.
- [`examples/vitis/CHECK.md`](examples/vitis/CHECK.md): link, DOI, accession and consistency checks.

## Projects

Ranked by the sum of public-data feasibility, novelty, and effort scores (see docs/RANKING.md). Tier follows the effort score, assigned by the upper end of each estimate: Quick = 6 weeks or less; Medium = more than 6 weeks, up to 4 months; Large = more than 4 months or a high-risk step. "continued" marks work started earlier and restarted here from public data under a new preregistration.

| # | Project | Tier | Papers | Origin |
|---|---|---|---|---|
| 01 | [Telomeres and interstitial telomeric repeats across near-complete grape haplotypes](examples/vitis/projects/01-telomere-and-interstitial-telomeric-repeats/) | Quick | 2 | continued |
| 02 | [45S and 5S rDNA arrays in near-complete grape assemblies](examples/vitis/projects/02-rdna-arrays/) | Quick | 1 | continued |
| 03 | [Endogenous florendovirus insertions across grape haplotypes](examples/vitis/projects/03-endogenous-florendoviruses/) | Medium | 1 | new |
| 04 | [Virus discovery across public grape RNA-seq and unmapped reads](examples/vitis/projects/04-virus-discovery-in-public-data/) | Medium | 1 | new |
| 05 | [Gene presence/absence across grape pangenomes under one pipeline](examples/vitis/projects/05-gene-pav-across-pangenomes/) | Medium | 2 | continued |
| 06 | [A genus-wide NLR catalogue with integrated domains and collapse checks](examples/vitis/projects/06-vitis-pan-nlrome/) | Medium | 1 | continued |
| 07 | [Copy number and birth–death of stilbene and aroma gene families (STS, TPS, CCD, LOX)](examples/vitis/projects/07-metabolic-gene-families/) | Medium | 2 | continued |
| 08 | [A harmonised identity table for public grape resequencing panels](examples/vitis/projects/08-harmonised-sample-panel/) | Medium | 1 | continued |
| 09 | [Graph genotyping of the berry colour locus](examples/vitis/projects/09-berry-colour-locus-graph/) | Quick | 1 | new |
| 10 | [Ancestral recombination graphs for hundreds of grape genomes and domestication timing](examples/vitis/projects/10-arg-domestication-timing/) | Large | 2 | continued |
| 11 | [Sequence-to-expression models and plant foundation models evaluated on grape](examples/vitis/projects/11-sequence-to-function-models/) | Large | 1 | new |
| 12 | [Convergent domestication: grape compared with other crops in one pipeline](examples/vitis/projects/12-convergent-domestication-cross-crop/) | Large | 1 | new |
| 13 | [Somatic mutation spectra across grape cultivars, with rates where clone dates are known](examples/vitis/projects/13-somatic-mutation-spectra-across-cultivars/) | Medium | 2 | continued |
| 14 | [TE insertion polymorphisms in cultivated grape from graph genotyping](examples/vitis/projects/14-te-insertion-polymorphisms-cultivated/) | Medium | 2 | continued |
| 15 | [Introgression on a graph pangenome: wild-to-cultivated and hybrid cultivars](examples/vitis/projects/15-graph-introgression/) | Medium | 2 | new |
| 16 | [Inherited and clonal structural variants on a graph: where hemizygous SVs sit and why](examples/vitis/projects/16-graph-sv-load/) | Medium | 1 | continued |
| 17 | [Large inversions: discovery in assemblies, population genotyping and suppressed recombination](examples/vitis/projects/17-large-inversions-in-populations/) | Medium | 1 | continued |
| 18 | [Centromeres of Vitis and Muscadinia, and a check of the chr7 fusion point](examples/vitis/projects/18-vitis-muscadinia-centromeres/) | Medium | 2 | continued |
| 19 | [Public RNA-seq on PN_T2T: expression atlas, eQTL/sQTL and allele-specific expression](examples/vitis/projects/19-public-rnaseq-on-t2t/) | Medium | 3 | new |
| 20 | [Archaeological grape seeds: graph mapping and low-coverage imputation](examples/vitis/projects/20-ancient-seeds-on-graph/) | Medium | 1 | new |
| 21 | [Meta-analysis of public GWAS, cross-ancestry genomic prediction and SV markers](examples/vitis/projects/21-gwas-meta-and-cross-ancestry-prediction/) | Medium | 3 | new |
| 22 | [Population-level evolution of the sex-determining region (demoted)](examples/vitis/projects/22-sex-region-population-level/) | Medium | 1 | new |
| 23 | [Family parentage and relationship QC on public grape records](examples/vitis/projects/23-family-parentage/STATUS.md) | [to confirm] | [to confirm] | continued |
| 24 | [Pedigree and linkage-disequilibrium recombination maps in grape](examples/vitis/projects/24-recombination-maps/STATUS.md) | [to confirm] | [to confirm] | continued |
| 25 | [Transposable-element annotation methods, library curation and automation](examples/vitis/projects/25-te-annotation-methods/STATUS.md) | [to confirm] | [to confirm] | continued |
| 26 | [Grapevine mitochondrial genomes, nuclear mitochondrial insertions and heteroplasmy](examples/vitis/projects/26-mitochondrial-genomes/STATUS.md) | [to confirm] | [to confirm] | new |

## Scope

Public data only: INSDC (NCBI, ENA, DDBJ), NGDC, GEO, Zenodo, figshare, and similar archives. No unpublished data or results are included, and the planned figures state hypotheses and criteria only. Organelle genomes, TE library construction, and population recombination maps have method-level pages in projects 23 to 26 (see docs/METHOD_LINES.md); project 10 uses published linkage maps, or LD-based rates only as an input.

Items marked [待确认] have not been verified yet.

## Licence

Text and tables: [CC BY 4.0](LICENSE). Datasets keep the licences stated in each data module.

**New here?** See [START_HERE.md](START_HERE.md) for the status of every project, a suggested restart order and the working rules. [中文](START_HERE.zh.md)

Status addendum, 2026-11-21 (UTC+8): projects 23 to 26 were added at method level and are listed in the table above. They cover parentage checks, recombination maps, TE annotation methods and mitochondrial genomes, which the Scope section above describes as handled elsewhere; see [examples/vitis/METHOD_LINES.md](examples/vitis/METHOD_LINES.md). Defaults for open items: [examples/vitis/DEFAULTS.md](examples/vitis/DEFAULTS.md). Current status of every project: [START_HERE.md](START_HERE.md), as of 2026-11-21. Scores in the ranking page are unchanged and were not set for projects 23 to 26.
