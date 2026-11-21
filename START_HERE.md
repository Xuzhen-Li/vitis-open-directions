# Start here

For a new maintainer or model taking over this repository. [中文](START_HERE.zh.md)

This repository holds grapevine (*Vitis*) genomics projects that use public data only. Each project is a runnable plan. Some projects continue earlier attempts that stopped before a confirmed result; this page says where each one stands, what to do first, and the rules to follow. Nothing here contains results.

Status as of 2026-11-21 (UTC+8). Items marked [to confirm] were not verified; the older [待确认] tag in other files means the same.

## Read in this order

1. [README.md](README.md): what the repository is and how the projects are ranked.
2. This page: status table, restart order, rules, lessons.
3. [docs/EARLIER_LINES.md](docs/EARLIER_LINES.md): how earlier work maps to the project folders.
4. The project you will run: `projects/NN-.../README.md` (the plan), then `projects/NN-.../STATUS.md` (where it stands and what to do first).
5. The modules it uses: [data/](data/) (public datasets), [analyses/](analyses/) (tools, commands, resources).
6. [docs/PREREGISTRATION.md](docs/PREREGISTRATION.md), [docs/EVIDENCE_LOG_TEMPLATE.md](docs/EVIDENCE_LOG_TEMPLATE.md), [docs/HPC_JOBS.md](docs/HPC_JOBS.md), [docs/DATA_PREP.md](docs/DATA_PREP.md).
7. [docs/RANKING.md](docs/RANKING.md) and [docs/NOT_KEPT.md](docs/NOT_KEPT.md) for why the order is what it is and what was left out.

## Layout

| Folder | What it holds |
|---|---|
| [data/](data/) | DS01 to DS23: one public dataset per folder, with accessions, size, licence, download and QC |
| [analyses/](analyses/) | AM01 to AM26: reusable steps with tools, commands, outputs and rough resources |
| [projects/](projects/) | 26 projects, one folder each: README (the plan) and STATUS (where it stands). Projects 23 to 26 have a STATUS page only |
| [docs/](docs/) | ranking, index, preregistration template, job template, evidence log template, not-kept list |

## Status of the projects

Labels: **Not started** = plan only. **Plan fixed** = detailed design written earlier, no confirmed result. **Partly run** = an earlier version ran in part; it cannot be continued, restart as a new study. **Paused** = stopped on a technical block.

| # | Project | Status | One-line state |
|---|---|---|---|
| 01 | [Telomeres and ITS](projects/01-telomere-and-interstitial-telomeric-repeats/STATUS.md) | Partly run | Earlier scan closed as descriptive after its decoy control failed; restart as a new study |
| 02 | [rDNA arrays](projects/02-rdna-arrays/STATUS.md) | Partly run | Only metadata and part of a merge step ran; start with the descriptive closed/open catalogue |
| 03 | [Florendovirus insertions](projects/03-endogenous-florendoviruses/STATUS.md) | Not started | Plan complete; pilot on two assemblies first |
| 04 | [Virus discovery in RNA-seq](projects/04-virus-discovery-in-public-data/STATUS.md) | Not started | Plan complete; fix the index-hopping controls first |
| 05 | [Gene PAV audit](projects/05-gene-pav-across-pangenomes/STATUS.md) | Plan fixed | Full design written, tools half installed, no result; keep one preregistration |
| 06 | [NLR catalogue](projects/06-vitis-pan-nlrome/STATUS.md) | Plan fixed | Design written; count technical-replicate pairs first |
| 07 | [STS, TPS, CCD, LOX families](projects/07-metabolic-gene-families/STATUS.md) | Partly run | Earlier STS test had too little power; aroma draft paused; restart on public haplotypes |
| 08 | [Harmonised sample table](projects/08-harmonised-sample-panel/STATUS.md) | Partly run | Identity pipeline designed, formal run did not finish; rebuild on public panels |
| 09 | [Berry colour locus graph](projects/09-berry-colour-locus-graph/STATUS.md) | Not started | Quick project; locate the locus and build a local graph |
| 10 | [ARG and domestication timing](projects/10-arg-domestication-timing/STATUS.md) | Partly run | Calibration did not support direct dating; write the calibration plan first, methods paper as fallback |
| 11 | [Sequence-to-expression models](projects/11-sequence-to-function-models/STATUS.md) | Not started | Needs project 19 tables and a GPU |
| 12 | [Cross-crop convergence](projects/12-convergent-domestication-cross-crop/STATUS.md) | Not started | Choose crops and the null model first |
| 13 | [Somatic mutation spectra](projects/13-somatic-mutation-spectra-across-cultivars/STATUS.md) | Not started | Clone list and masks first; one chromosome 2 LOH idea parked |
| 14 | [TE insertion polymorphisms](projects/14-te-insertion-polymorphisms-cultivated/STATUS.md) | Plan fixed | Design and controls written, no output; annotation tooling failed; decide the split with vitis-te |
| 15 | [Graph introgression](projects/15-graph-introgression/STATUS.md) | Not started | Pick donor panels first |
| 16 | [Graph SVs, inherited and clonal](projects/16-graph-sv-load/STATUS.md) | Not started | Graph genotyping plus the trio; the ROH and load line is folded into AM12 |
| 17 | [Large inversions](projects/17-large-inversions-in-populations/STATUS.md) | Partly run | Spanning-read test designed, code failed its check; needs the project 08 sample pool |
| 18 | [Centromeres](projects/18-vitis-muscadinia-centromeres/STATUS.md) | Paused | TRASH never installed, ChIP download incomplete |
| 19 | [Public RNA-seq on T2T](projects/19-public-rnaseq-on-t2t/STATUS.md) | Not started | Atlas first, QTL later |
| 20 | [Ancient seeds on a graph](projects/20-ancient-seeds-on-graph/STATUS.md) | Not started | Check raw reads accession by accession first |
| 21 | [GWAS meta-analysis](projects/21-gwas-meta-and-cross-ancestry-prediction/STATUS.md) | Not started | Inventory only; stop if the data are not public |
| 22 | [Sex region](projects/22-sex-region-population-level/STATUS.md) | Not started | Demoted; check the sex records first |
| 23 | [Family parentage and relationship QC](projects/23-family-parentage/STATUS.md) | Plan fixed | Design written, not run; public records only; the private families stay out; positive control is the DS18 trio |
| 24 | [Pedigree and LD recombination maps](projects/24-recombination-maps/STATUS.md) | Plan fixed | Design written, not run; the pedigree quantity and the LD-based quantity are kept apart; public route through published maps and public panels |
| 25 | [TE annotation methods, curation and automation](projects/25-te-annotation-methods/STATUS.md) | Plan fixed | Outline of a methods survey written; no manuscript in this repository; split with project 14 and vitis-te has a default in docs/DEFAULTS.md |
| 26 | [Mitochondrial genomes, NUMTs and heteroplasmy](projects/26-mitochondrial-genomes/STATUS.md) | Not started | Proposed starting design and public inputs listed; the question that defines the project is still open |

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

- Write the criteria before looking at results. Fill in [docs/PREREGISTRATION.md](docs/PREREGISTRATION.md), commit it with a date, then run. Every restart gets a new preregistration; criteria from earlier attempts are reference only.
- Any change made after results are visible is post-hoc: write it in the log as post-hoc and treat the result as exploratory.
- Keep an evidence log for each project ([docs/EVIDENCE_LOG_TEMPLATE.md](docs/EVIDENCE_LOG_TEMPLATE.md)). Add entries only; never edit an old one. Correct a mistake with a new entry that points to the old one.
- Every citation must be a DOI or URL you opened yourself. Check DOIs against Crossref or DataCite. Anything else is marked [to confirm]. Do not invent references, accessions or numbers.
- Run positive and negative controls before reading any main result, with pass levels fixed in advance.
- The person or process that writes code does not check it. Use a different one for the check.
- Never overwrite or delete outputs. One new run folder per run, ending in .DONE or .FAILED ([docs/HPC_JOBS.md](docs/HPC_JOBS.md)). Use a manifest with sha256 for every downloaded file.
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

A checked list of public download links is in [data/DOWNLOADS.md](data/DOWNLOADS.md).

Status addendum, 2026-11-21 (UTC+8): projects 23 to 26 were added at method level. Defaults for open items are in [docs/DEFAULTS.md](docs/DEFAULTS.md). The four method lines are described in [docs/METHOD_LINES.md](docs/METHOD_LINES.md). Sources checked for the projects whose STATUS pages only point to the README are listed in [docs/SOURCES_CHECKED_20261121.md](docs/SOURCES_CHECKED_20261121.md). Where this addendum and an older sentence above disagree (for example the number of projects), this addendum is newer.
