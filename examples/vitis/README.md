# Grapevine (*Vitis*) worked example

Written 2026-11-21 (UTC+8). [中文](README.zh.md)

This folder applies the [six-dimension gap framework](../../framework/GAP_FRAMEWORK.md) to grapevine from start to finish. It holds all grapevine material in the repository: public datasets, reusable analysis steps, 26 projects, and the pages that rank, index and check them. Working rules for every project are in [START_HERE.md](../../START_HERE.md).

## What is here

| Path | What it holds | Earlier path |
|---|---|---|
| [data/](data/) | DS01 to DS23: one public dataset per folder; [data/DOWNLOADS.md](data/DOWNLOADS.md) lists checked download links | `data/` |
| [analyses/](analyses/) | AM01 to AM26: reusable steps with tools, commands, outputs and rough resources | `analyses/` |
| [projects/](projects/) | 26 projects; 01 to 22 have a README (the plan) and a STATUS page, 23 to 26 have a STATUS page only | `projects/` |
| [INDEX.md](INDEX.md) | which modules each project uses, and how projects split into papers | `docs/INDEX.md` |
| [RANKING.md](RANKING.md) | frozen scores, independent re-scoring and the adjustment register | `docs/RANKING.md` |
| [RISKS.md](RISKS.md) | risks shared by many projects and the largest risk for each project, with checks (added 2026-11-26) | none (new) |
| [REFERENCE_STUDIES.md](REFERENCE_STUDIES.md) | reference studies in other species for each project, the Q1-level bar, and the projects whose scope changed (added 2026-11-26) | none (new) |
| [DEFAULTS.md](DEFAULTS.md) | defaults for open items | `docs/DEFAULTS.md` |
| [NOT_KEPT.md](NOT_KEPT.md) | directions checked and left out, with the papers that cover them | `docs/NOT_KEPT.md` |
| [METHOD_LINES.md](METHOD_LINES.md) | the four method lines (projects 23 to 26) | `docs/METHOD_LINES.md` |
| [SOURCES_CHECKED_20261121.md](SOURCES_CHECKED_20261121.md) | Crossref checks of 2026-11-21 | `docs/SOURCES_CHECKED_20261121.md` |
| [EARLIER_LINES.md](EARLIER_LINES.md) | how earlier attempts map to the project folders; mainly useful for tracing where a project came from | `docs/EARLIER_LINES.md` |
| [CHECK.md](CHECK.md) | link, DOI, accession and consistency checks of 2026-11-14, with a note added on 2026-11-21 | `CHECK.md` |

Paths written as plain text inside these pages (for example `docs/DEFAULTS.md` or `data/DOWNLOADS.md`) refer to the earlier layout, in which `data/`, `analyses/`, `projects/` and `docs/` sat at the top of the repository. Read `docs/X.md` as `examples/vitis/X.md`, except PREREGISTRATION, EVIDENCE_LOG_TEMPLATE, DATA_PREP and HPC_JOBS, which are now in [templates/](../../templates/). Links have been updated.

## Direction map

The table places the 26 projects in the six dimensions. It is a proposal written on 2026-11-21. No folder was merged, renamed or removed, and the frozen scores in [RANKING.md](RANKING.md) are unchanged. The suggested merges, the downgrade of projects 21 and 26, and the proposal for project 09 wait for the maintainer [to confirm]. Project 22 was already demoted in RANKING.md.

| Dimension | Keep | Suggested merge or link | Downgraded (start only when a condition is met) | Proposed out of the main line |
|---|---|---|---|---|
| 1. Data and resources | [08](projects/08-harmonised-sample-panel/) harmonised sample identity table, the base for every population project; [23](projects/23-family-parentage/STATUS.md) parentage and relationship QC, right after 08 | 08 and 23 share the de-duplicated sample pool and SNP set and can run as upstream and downstream steps | none | none |
| 2. Genome structure and organelles | [01](projects/01-telomere-and-interstitial-telomeric-repeats/) telomeres and ITS; [02](projects/02-rdna-arrays/) rDNA arrays; [07](projects/07-metabolic-gene-families/) STS, TPS, CCD and LOX families; [18](projects/18-vitis-muscadinia-centromeres/) centromeres and the chr7 fusion, in parallel with 01 and 02 once it is no longer paused | [05](projects/05-gene-pav-across-pangenomes/) + [06](projects/06-vitis-pan-nlrome/) as one paper in two parts (shared de-duplication and distance matrix) [to confirm]; 01 + 02 as one repeat-array paper (A2 in [INDEX.md](INDEX.md)), optional [to confirm] | [26](projects/26-mitochondrial-genomes/STATUS.md) mitochondrial genomes, NUMTs and heteroplasmy, until its core question is fixed [to confirm] | none |
| 3. Variation and mobile elements | [03](projects/03-endogenous-florendoviruses/) endogenous florendoviruses; [13](projects/13-somatic-mutation-spectra-across-cultivars/) somatic spectra across cultivars (the chr2 LOH idea stays parked); [14](projects/14-te-insertion-polymorphisms-cultivated/) TE insertion polymorphisms on a graph; [16](projects/16-graph-sv-load/) inherited and clonal hemizygous SVs; [17](projects/17-large-inversions-in-populations/) large inversions | [25](projects/25-te-annotation-methods/STATUS.md) stays beside 14 with a clear split: 25 is a methods survey, 14 is the analysis; no second insertion library | none | The linear-reference load direction is in [NOT_KEPT.md](NOT_KEPT.md); its methods stay in AM12 |
| 4. Population, domestication and reproductive system | [10](projects/10-arg-domestication-timing/) ARGs and domestication timing, calibration first, with methods paper K1 as fallback; [15](projects/15-graph-introgression/) SV introgression on a graph; [20](projects/20-ancient-seeds-on-graph/) ancient seeds on a graph | [24](projects/24-recombination-maps/STATUS.md) as a method line linked to 23 and 10; LD-based and pedigree recombination rates are kept apart | [22](projects/22-sex-region-population-level/) sex-determining region, stays demoted unless enough wild sex records are found | none |
| 5. Expression, regulation and epigenetics | [19](projects/19-public-rnaseq-on-t2t/) public RNA-seq on PN_T2T, atlas (S1) first, then QTL and ASE (S2, S3); [11](projects/11-sequence-to-function-models/) sequence-to-expression models, depends on 19 | none | none | Population WGBS, single-cell regulation, Hi-C/TAD and mobile mRNA stay in [NOT_KEPT.md](NOT_KEPT.md) |
| 6. Phenotype, function and cross-species comparison | [04](projects/04-virus-discovery-in-public-data/) virus discovery in public data; [12](projects/12-convergent-domestication-cross-crop/) convergent domestication across crops | none | [21](projects/21-gwas-meta-and-cross-ancestry-prediction/) GWAS meta-analysis and prediction, start only after the public phenotype inventory passes [to confirm] | [09](projects/09-berry-colour-locus-graph/) berry colour locus: proposed to become a teaching and test example for graph genotyping (AM07) instead of a main-line project [to confirm]; until the maintainer decides, it stays a Quick project |

Possible directions outside these 26 (plastid pangenome with cytonuclear interaction; protein structure evolution across haplotypes) are listed in the framework as [to confirm] and have no folder.

## Notes

- **Projects 23 to 26** have a STATUS page only: no README, no F/N/E scores in RANKING.md, and no row in the INDEX.md matrix. For these projects read [METHOD_LINES.md](METHOD_LINES.md) and the STATUS page instead of a README. Whether to add a README and scores, or to give the method lines their own section in INDEX.md, is [to confirm].
- **ITS** in this example means interstitial telomeric repeats (projects 01 and 18). It does not mean the transcribed spacers ITS1 and ITS2 of the rDNA unit, which belongs to the rDNA topic of project 02. Write the meaning out in full where both could be read.
- **CHECK.md** was generated on 2026-11-14 and covers projects 01 to 22, DS01 to DS22 and 103 DOIs. It does not cover projects 23 to 26, DS23, or the roughly 150 distinct DOI strings present on 2026-11-21. A full rerun on the new layout is [to confirm]; see the note at the end of [CHECK.md](CHECK.md).

## How to start on a grapevine project

1. Read [INDEX.md](INDEX.md), [RANKING.md](RANKING.md) and [DEFAULTS.md](DEFAULTS.md) to see whether the project is suggested for a merge, is downgraded, or has a default for an open item (for example DS11 left out of the first pass, and the exact DS02 list).
2. Read the project README and STATUS page; where a STATUS page has dated addenda, the latest one applies. For projects 23 to 26 read METHOD_LINES.md and the STATUS page. Read [NOT_KEPT.md](NOT_KEPT.md) so as not to repeat published work.
3. Read [data/DOWNLOADS.md](data/DOWNLOADS.md) and the DS and AM modules the project uses, and confirm that each input is `available`.
4. Fill in [templates/PREREGISTRATION.md](../../templates/PREREGISTRATION.md): sample list, control pass lines, statistical tests and stop rules. Do not look at main results before the preregistration is committed and the controls have passed.
5. Use [templates/HPC_JOBS.md](../../templates/HPC_JOBS.md) and [templates/DATA_PREP.md](../../templates/DATA_PREP.md) for a small pilot and a checksum list, and append every step to the project evidence log ([templates/EVIDENCE_LOG_TEMPLATE.md](../../templates/EVIDENCE_LOG_TEMPLATE.md)).
