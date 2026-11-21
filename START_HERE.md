# Start here

For a new maintainer or model taking over this repository. [中文](START_HERE.zh.md)

This repository holds grapevine (*Vitis*) genomics projects that use public data only. Each project is a runnable plan. Some projects continue earlier attempts that stopped before a confirmed result; this page says where each one stands, what to do first, and the rules to follow. Nothing here contains results.

Status as of 2026-11-21 (UTC+8). Items marked [to confirm] were not verified; the older [待确认] tag in other files means the same.

## Read in this order

1. [README.md](README.md): what the repository is and how the projects are ranked.
2. This page: status table, restart order, rules, lessons.
3. [examples/vitis/EARLIER_LINES.md](examples/vitis/EARLIER_LINES.md): how earlier work maps to the project folders.
4. The project you will run: `projects/NN-.../README.md` (the plan), then `projects/NN-.../STATUS.md` (where it stands and what to do first).
5. The modules it uses: [examples/vitis/data/](examples/vitis/data/) (public datasets), [examples/vitis/analyses/](examples/vitis/analyses/) (tools, commands, resources).
6. [templates/PREREGISTRATION.md](templates/PREREGISTRATION.md), [templates/EVIDENCE_LOG_TEMPLATE.md](templates/EVIDENCE_LOG_TEMPLATE.md), [templates/HPC_JOBS.md](templates/HPC_JOBS.md), [templates/DATA_PREP.md](templates/DATA_PREP.md).
7. [examples/vitis/RANKING.md](examples/vitis/RANKING.md) and [examples/vitis/NOT_KEPT.md](examples/vitis/NOT_KEPT.md) for why the order is what it is and what was left out.

## Layout

| Folder | What it holds |
|---|---|
| [examples/vitis/data/](examples/vitis/data/) | DS01 to DS23: one public dataset per folder, with accessions, size, licence, download and QC |
| [examples/vitis/analyses/](examples/vitis/analyses/) | AM01 to AM26: reusable steps with tools, commands, outputs and rough resources |
| [examples/vitis/projects/](examples/vitis/projects/) | 26 projects, one folder each: README (the plan) and STATUS (where it stands). Projects 23 to 26 have a STATUS page only |
| [examples/vitis/](examples/vitis/) | ranking, index, preregistration template, job template, evidence log template, not-kept list |

## Status of the projects

Labels: **Not started** = plan only. **Plan fixed** = detailed design written earlier, no confirmed result. **Partly run** = an earlier version ran in part; it cannot be continued, restart as a new study. **Paused** = stopped on a technical block.

| # | Project | Status | One-line state |
|---|---|---|---|
| 01 | [Telomeres and ITS](examples/vitis/projects/01-telomere-and-interstitial-telomeric-repeats/STATUS.md) | Partly run | Earlier scan closed as descriptive after its decoy control failed; restart as a new study |
| 02 | [rDNA arrays](examples/vitis/projects/02-rdna-arrays/STATUS.md) | Partly run | Only metadata and part of a merge step ran; start with the descriptive closed/open catalogue |
| 03 | [Florendovirus insertions](examples/vitis/projects/03-endogenous-florendoviruses/STATUS.md) | Not started | Plan complete; pilot on two assemblies first |
| 04 | [Virus discovery in RNA-seq](examples/vitis/projects/04-virus-discovery-in-public-data/STATUS.md) | Not started | Plan complete; fix the index-hopping controls first |
| 05 | [Gene PAV audit](examples/vitis/projects/05-gene-pav-across-pangenomes/STATUS.md) | Plan fixed | Full design written, tools half installed, no result; keep one preregistration |
| 06 | [NLR catalogue](examples/vitis/projects/06-vitis-pan-nlrome/STATUS.md) | Plan fixed | Design written; count technical-replicate pairs first |
| 07 | [STS, TPS, CCD, LOX families](examples/vitis/projects/07-metabolic-gene-families/STATUS.md) | Partly run | Earlier STS test had too little power; aroma draft paused; restart on public haplotypes |
| 08 | [Harmonised sample table](examples/vitis/projects/08-harmonised-sample-panel/STATUS.md) | Partly run | Identity pipeline designed, formal run did not finish; rebuild on public panels |
| 09 | [Berry colour locus graph](examples/vitis/projects/09-berry-colour-locus-graph/STATUS.md) | Not started | Quick project; locate the locus and build a local graph |
| 10 | [ARG and domestication timing](examples/vitis/projects/10-arg-domestication-timing/STATUS.md) | Partly run | Calibration did not support direct dating; write the calibration plan first, methods paper as fallback |
| 11 | [Sequence-to-expression models](examples/vitis/projects/11-sequence-to-function-models/STATUS.md) | Not started | Needs project 19 tables and a GPU |
| 12 | [Cross-crop convergence](examples/vitis/projects/12-convergent-domestication-cross-crop/STATUS.md) | Not started | Choose crops and the null model first |
| 13 | [Somatic mutation spectra](examples/vitis/projects/13-somatic-mutation-spectra-across-cultivars/STATUS.md) | Not started | Clone list and masks first; one chromosome 2 LOH idea parked |
| 14 | [TE insertion polymorphisms](examples/vitis/projects/14-te-insertion-polymorphisms-cultivated/STATUS.md) | Plan fixed | Design and controls written, no output; annotation tooling failed; decide the split with vitis-te |
| 15 | [Graph introgression](examples/vitis/projects/15-graph-introgression/STATUS.md) | Not started | Pick donor panels first |
| 16 | [Graph SVs, inherited and clonal](examples/vitis/projects/16-graph-sv-load/STATUS.md) | Not started | Graph genotyping plus the trio; the ROH and load line is folded into AM12 |
| 17 | [Large inversions](examples/vitis/projects/17-large-inversions-in-populations/STATUS.md) | Partly run | Spanning-read test designed, code failed its check; needs the project 08 sample pool |
| 18 | [Centromeres](examples/vitis/projects/18-vitis-muscadinia-centromeres/STATUS.md) | Paused | TRASH never installed, ChIP download incomplete |
| 19 | [Public RNA-seq on T2T](examples/vitis/projects/19-public-rnaseq-on-t2t/STATUS.md) | Not started | Atlas first, QTL later |
| 20 | [Ancient seeds on a graph](examples/vitis/projects/20-ancient-seeds-on-graph/STATUS.md) | Not started | Check raw reads accession by accession first |
| 21 | [GWAS meta-analysis](examples/vitis/projects/21-gwas-meta-and-cross-ancestry-prediction/STATUS.md) | Not started | Inventory only; stop if the data are not public |
| 22 | [Sex region](examples/vitis/projects/22-sex-region-population-level/STATUS.md) | Not started | Demoted; check the sex records first |
| 23 | [Family parentage and relationship QC](examples/vitis/projects/23-family-parentage/STATUS.md) | Plan fixed | Design written, not run; public records only; the private families stay out; positive control is the DS18 trio |
| 24 | [Pedigree and LD recombination maps](examples/vitis/projects/24-recombination-maps/STATUS.md) | Plan fixed | Design written, not run; the pedigree quantity and the LD-based quantity are kept apart; public route through published maps and public panels |
| 25 | [TE annotation methods, curation and automation](examples/vitis/projects/25-te-annotation-methods/STATUS.md) | Plan fixed | Outline of a methods survey written; no manuscript in this repository; split with project 14 and vitis-te has a default in docs/DEFAULTS.md |
| 26 | [Mitochondrial genomes, NUMTs and heteroplasmy](examples/vitis/projects/26-mitochondrial-genomes/STATUS.md) | Not started | Proposed starting design and public inputs listed; the question that defines the project is still open |

## Suggested restart order

This is a suggestion from the ranking and the dependencies between projects, not a decision. Change it if the repository maintainer prefers.

1. **Groundwork.** AM01 (download with checksums) and AM05 (assembly QC) for DS01, DS02, DS03 and DS16. These feed projects 01, 02, 03, 05, 06, 07, 14, 17 and 18.
2. **Assembly-only, small compute:** 01, 02 and 18 together (they share AM10 and the chromosome 7 fusion check), then 03.
3. **Annotation and pangenome:** 05 with 06 (one paper, two sections), then 07 and 14.
4. **Sample table:** 08. Many population projects need its clone-free sample pool. Start with metadata and small panels before the largest downloads.
5. **Needs the sample table:** 09 (quick), then 17, 15, 16 and 13.
6. **Large or high risk:** 10 (calibrate first), 19 then 11, 12, 20, 21 (inventory first), and 22 (demoted).
7. **Method-level lines (added 2026-11-21).** 23 then 24 (public records first). 25 can be drafted in parallel from published sources. 26 needs its defining question fixed first.

## Working rules

- Write the criteria before looking at results. Fill in [templates/PREREGISTRATION.md](templates/PREREGISTRATION.md), commit it with a date, then run. Every restart gets a new preregistration; criteria from earlier attempts are reference only.
- Any change made after results are visible is post-hoc: write it in the log as post-hoc and treat the result as exploratory.
- Keep an evidence log for each project ([templates/EVIDENCE_LOG_TEMPLATE.md](templates/EVIDENCE_LOG_TEMPLATE.md)). Add entries only; never edit an old one. Correct a mistake with a new entry that points to the old one.
- Every citation must be a DOI or URL you opened yourself. Check DOIs against Crossref or DataCite. Anything else is marked [to confirm]. Do not invent references, accessions or numbers.
- Run positive and negative controls before reading any main result, with pass levels fixed in advance.
- The person or process that writes code does not check it. Use a different one for the check.
- Never overwrite or delete outputs. One new run folder per run, ending in .DONE or .FAILED ([templates/HPC_JOBS.md](templates/HPC_JOBS.md)). Use a manifest with sha256 for every downloaded file.
- Public data only. Do not commit private data, sample details, results, host names, local paths or keys.
- Write plain English. Do not name or criticise other groups; cite their papers neutrally.
- To update a STATUS.md, add a dated section at the end and keep the earlier text. Git history keeps the rest.

## Lessons from earlier attempts

- Decide thresholds and sample lists first. Changes after seeing results turned several earlier lines into exploratory work.
- A negative control that fails sends the work to a descriptive report; plan for that outcome in advance.
- With very few genomes an exact permutation test cannot reach a small p value (nine genomes give 36 assignments). Check power in the design.
- Clones and duplicate samples are common in grape. Run AM04 before any population analysis.
- Check that a read run really belongs to the genotype you think it does (BioSample and name) before using it as evidence.
- Tool installs failed more often than analyses: TRASH (dependencies), EDTA (missing database partition, RepeatMasker engine setup), and one data host that the compute site could not reach. Test installs and connectivity on a tiny input first, and name a fallback tool.
- Do not hard-code paths in scripts. Keep paths in a local config and use manifests.
- Many small addenda made one design hard to follow. Keep one preregistration per restart and put the final rules in it.

## Open items for the repository maintainer [to confirm]

- Which projects to run, and in which order.
- Whether project 14 and the vitis-te catalogue should be merged or split.
- Which of the families LOX, MLO, PPO and CBF belong in project 07.
- Sources for mutation rate and generation time. (The OMArk lineage data now has a recorded source; see data/DOWNLOADS.md and docs/DEFAULTS.md.)
- Whether public reads exist for the chromosome 2 LOH idea (project 13).
- Whether DS11 reads can be exported from NGDC by hand (projects 08, 10, 23, 24).
- The question that defines project 26, and whether project 25 stays a methods survey beside project 14 and the vitis-te catalogue.
- Whether PN_T2T is the public coordinate system for projects 23 and 24 [to confirm].

Every [to confirm] item is also listed in the STATUS.md of its project.

A checked list of public download links is in [examples/vitis/data/DOWNLOADS.md](examples/vitis/data/DOWNLOADS.md).

Status addendum, 2026-11-21 (UTC+8): projects 23 to 26 were added at method level. Defaults for open items are in [examples/vitis/DEFAULTS.md](examples/vitis/DEFAULTS.md). The four method lines are described in [examples/vitis/METHOD_LINES.md](examples/vitis/METHOD_LINES.md). Sources checked for the projects whose STATUS pages only point to the README are listed in [examples/vitis/SOURCES_CHECKED_20261121.md](examples/vitis/SOURCES_CHECKED_20261121.md). Where this addendum and an older sentence above disagree (for example the number of projects), this addendum is newer.

## Layout and reading order from 2026-11-21

On 2026-11-21 the grapevine material moved into [examples/vitis/](examples/vitis/), the general templates into [templates/](templates/), and a method that works for any species was added in [framework/](framework/). Links on this page were updated. Plain-text paths such as `projects/NN-.../README.md` now mean `examples/vitis/projects/NN-.../README.md`. In the Layout table above, the row for `examples/vitis/` stands for the former `docs/` folder: the ranking, index and not-kept list are in `examples/vitis/`, and the preregistration, job and evidence log templates are in `templates/`.

After [README.md](README.md) and this page, take one of two branches:

- **A. Another species.** Read [framework/GAP_FRAMEWORK.md](framework/GAP_FRAMEWORK.md) and [framework/EVALUATION_RUBRIC.md](framework/EVALUATION_RUBRIC.md), then follow [framework/SPECIES_TRANSFER_GUIDE.md](framework/SPECIES_TRANSFER_GUIDE.md) with the templates in [templates/](templates/). Without internet access, mark every untested accession and DOI [to confirm] and write out the queries to be run on a login node, as the guide describes.
- **B. A grapevine project.** Follow How to start on a grapevine project in [examples/vitis/README.md](examples/vitis/README.md). Projects 23 to 26 have no README and no scores: read [examples/vitis/METHOD_LINES.md](examples/vitis/METHOD_LINES.md) and the STATUS page of the project.

[examples/vitis/EARLIER_LINES.md](examples/vitis/EARLIER_LINES.md) is mainly useful for tracing where a project came from. The map that places projects 01 to 26 in the six dimensions, with suggested merges and downgrades marked [to confirm], is in [examples/vitis/README.md](examples/vitis/README.md).
