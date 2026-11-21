# Status: Ancestral recombination graphs for hundreds of grape genomes and domestication timing

**Status: Partly run** (as of 2026-11-20, UTC+8). Plan: [README.md](README.md). Entry file: [START_HERE.md](../../../../START_HERE.md).

## Where it stands

An earlier line tried to date domestication-related alleles with ancestral recombination graph (ARG) methods. The calibration on simulated data did not support direct dating, so the line was kept as descriptive only. A later calibration rule was added after the first calibration was seen, which makes it post-hoc. The dating results of that later rule were never located. Everything here restarts on public data (DS10, DS11, DS12, DS04, DS06, DS08), as a new design.

## Design settled earlier (reference only; write a new preregistration before running)

- Calibrate first, on simulations with known ages (AM14: SLiM for clonal generations, recapitated with msprime), and decide only afterwards whether real data can be dated.
- Correct estimate bias with isotonic regression (PAVA) fitted to ln(true age) against ln(estimated age), then refit the scale.
- Pass rule, written once: in the young and middle age strata the median absolute ln bias is at most 0.1 and the 95% interval coverage is at least 0.90; the oldest stratum is reported only. Stratum limits are given in years at a stated generation time [to confirm values].
- Sensitivity to the mutation rate and the recombination rate is large in the oldest stratum under some scenarios; carry both as intervals.
- Never publish a date as a result unless calibration passes; otherwise write the methods paper (K1 in docs/INDEX.md).
- Outgroup for polarisation: *Muscadinia* plus a North American or East Asian *Vitis*; never one outgroup alone.

## Where it stopped and why

- Calibration did not pass, and the second rule was set after seeing it.
- Real-data dating output could not be found.

## Next steps

1. AM04 to remove clones; AM03 to call variants; phase with SHAPEIT5; polarise (AM26). Start with the panels that can be downloaded (DS10, DS12, DS04); add DS11 only after a run list is exported by hand (data/DOWNLOADS.md).
2. Write the calibration plan and pass rule in the preregistration before any real-data ARG run.
3. Run the simulations (AM14) and compare ARG methods (Relate and tsdate) on them.
4. Only if calibration passes, date alleles on real data; otherwise go to the methods paper.

## Open items

- Published domestication time points to compare with, and their primary sources [to confirm].
- Mutation rate and generation time intervals and their sources [to confirm].
- Support for non-contemporaneous samples in tsdate and Relate [to confirm].

## Sources read

- Relate: [doi:10.1038/s41588-019-0484-x](https://doi.org/10.1038/s41588-019-0484-x)
- Unified genealogy (tsdate): [doi:10.1126/science.abi8264](https://doi.org/10.1126/science.abi8264)
- Grape domestication genomics: [doi:10.1073/pnas.1709257114](https://doi.org/10.1073/pnas.1709257114)
- Dual domestications: [doi:10.1126/science.add8655](https://doi.org/10.1126/science.add8655)

## Public inputs

| Module | Dataset | Headline accessions (from the module) |
|---|---|---|
| [DS10](../../data/DS10-reseq-472-vitis/) | Resequencing of 472 Vitis accessions (and the 2017 domestication panel) | PRJNA393611, PRJNA388292 |
| [DS11](../../data/DS11-reseq-3525-dong2023/) | Resequencing of 3,525 grapevine accessions (Dong et al. 2023) | CRA006917, PRJCA009314, CRA006898 |
| [DS12](../../data/DS12-reseq-204-magris2021/) | Resequencing of 204 V. vinifera accessions (Magris et al. 2021) | PRJNA373967, PRJNA390884, PRJNA385116, PRJNA321480 |
| [DS08](../../data/DS08-muscadinia-genomes/) | Muscadinia rotundifolia assemblies and reads | Zenodo 3866087, PRJNA593045, Zenodo 7944874, PRJNA935741, PRJNA780568 |
| [DS04](../../data/DS04-na-vitis-super-pangenome/) | North American Vitis super-pangenome and wild resequencing | Zenodo 8065808, Zenodo 10206475, PRJNA984685, PRJNA731597, PRJNA842753 |
| [DS06](../../data/DS06-vitis-amurensis-pangenome/) | Vitis amurensis haplotype assemblies and 330-sample resequencing | PRJNA1272278, PRJNA1272285, Zenodo 16534920, PRJNA1308837, PRJNA1089859, PRJCA046381 |
| [DS01](../../data/DS01-pn40024-references/) | PN40024 references: PN_T2T (v5), PN40024.v4 and 12X | GCF_030704535.1, GCA_030704535.1, PRJNA882193, PRJCA012093, PRJEB45423, GCF_000003745.3, PRJEA18785 |

## Shared steps, in order

| Order | Step | Main tools |
|---|---|---|
| 1 | [AM01](../../analyses/AM01-download-and-verify/) Download selected runs | ENA FTP, md5sum |
| 2 | [AM04](../../analyses/AM04-sample-identity/) Sample selection on public genotypes | plink2, KING |
| 3 | [AM03](../../analyses/AM03-short-read-variants/) Mapping and calling | bwa-mem2, DeepVariant, GLnexus |
| 4 | [AM04](../../analyses/AM04-sample-identity/) Identity check and deduplication on the new calls | plink2, KING |
| 5 | [AM26](../../analyses/AM26-phasing-polarisation-recombination/) Outgroup alignment and per-site outgroup bases | minimap2, paftools.js |
| 6 | [AM26](../../analyses/AM26-phasing-polarisation-recombination/) Phasing, ancestral states, recombination input | SHAPEIT5, est-sfs, pyrho |
| 7 | [AM14](../../analyses/AM14-ancestral-recombination-graph/) Simulation calibration (Fig 1) | SLiM, pyslim, msprime, stdpopsim |
| 8 | [AM14](../../analyses/AM14-ancestral-recombination-graph/) ARG inference and dating | tsinfer, tsdate, Relate, SINGER |

## Before any run

- Fill in [docs/PREREGISTRATION.md](../../../../templates/PREREGISTRATION.md) and commit it with a date before looking at results. Every restart gets a new one; criteria from earlier attempts are reference only.
- Keep an evidence log (template: [docs/EVIDENCE_LOG_TEMPLATE.md](../../../../templates/EVIDENCE_LOG_TEMPLATE.md)). Add entries only; never edit an old entry.
- Cite only DOIs and URLs you opened yourself. Mark anything else [to confirm].
- Never overwrite outputs: one new run folder per run, ending in .DONE or .FAILED ([docs/HPC_JOBS.md](../../../../templates/HPC_JOBS.md)).
- Do not commit private data, sample details, results, host names or local paths.

## Update 2026-11-21 (UTC+8)

Added as appended lines; the text above is unchanged.

- DS11 reads cannot be listed without an NGDC login (see data/DOWNLOADS.md; on 2026-11-21 the directory https://download.cncb.ac.cn/gsa/CRA006917/ returned HTTP 404). Run the first pass on DS10, DS12 and the DS02 resequencing panel, and treat DS11 as an extension queue that is added when a run list for PRJCA009314 has been exported by hand.
- Project 24 states how LD-based rates would be produced on public panels; this project keeps using published linkage maps, and LD-based rates only as an input.
