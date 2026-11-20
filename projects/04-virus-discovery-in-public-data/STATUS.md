# Status: Virus discovery across public grape RNA-seq and unmapped reads

**Status: Not started** (as of 2026-11-20, UTC+8). Plan: [README.md](README.md). Entry file: [START_HERE.md](../../START_HERE.md).

## Where it stands

No analysis has been run and there is no earlier line behind this project. The plan in the README is complete.

## Next steps

1. Build the run list from DS15 and note which studies lack library metadata.
2. Start with one study: map to PN_T2T, keep unmapped reads, screen with Kraken2 and DIAMOND, assemble positives, assess with CheckV.
3. Decide the blank-library and cross-study controls for index hopping before running the full set, and write them into the preregistration.
4. Pick a positive control (a library from a paper that reports a virus in grape) and record its accession [to confirm].

## Open items

- Metadata are incomplete for many runs; decide the exclusion rule first.
- Download volume of all public grape RNA-seq is large; estimate it from the ENA file report before starting [to confirm].

## Sources read

- The references listed in the project README.

## Public inputs

| Module | Dataset | Headline accessions (from the module) |
|---|---|---|
| [DS15](../../data/DS15-rnaseq-public-vitis/) | Public Vitis RNA-seq and the expression atlas | PRJNA565689, PRJNA434655, PRJEB107006, PRJNA260535, PRJNA674915, PRJNA915033, GSE36128 |
| [DS10](../../data/DS10-reseq-472-vitis/) | Resequencing of 472 Vitis accessions (and the 2017 domestication panel) | PRJNA393611, PRJNA388292 |
| [DS12](../../data/DS12-reseq-204-magris2021/) | Resequencing of 204 V. vinifera accessions (Magris et al. 2021) | PRJNA373967, PRJNA390884, PRJNA385116, PRJNA321480 |
| [DS01](../../data/DS01-pn40024-references/) | PN40024 references: PN_T2T (v5), PN40024.v4 and 12X | GCF_030704535.1, GCA_030704535.1, PRJNA882193, PRJCA012093, PRJEB45423, GCF_000003745.3, PRJEA18785 |

## Shared steps, in order

| Order | Step | Main tools |
|---|---|---|
| 1 | [AM01](../../analyses/AM01-download-and-verify/) Download and verify | ncbi-datasets-cli, sra-tools, ENA FTP / Aspera |
| 2 | [AM02](../../analyses/AM02-read-qc/) Read QC and trimming | fastp, MultiQC, seqkit |
| 3 | [AM16](../../analyses/AM16-virus-and-eve-search/) Virus discovery in RNA-seq and endogenous viral elements in assemblies | DIAMOND, MEGAHIT, SPAdes (rnaviralSPAdes) |

## Before any run

- Fill in [docs/PREREGISTRATION.md](../../docs/PREREGISTRATION.md) and commit it with a date before looking at results. Every restart gets a new one; criteria from earlier attempts are reference only.
- Keep an evidence log (template: [docs/EVIDENCE_LOG_TEMPLATE.md](../../docs/EVIDENCE_LOG_TEMPLATE.md)). Add entries only; never edit an old entry.
- Cite only DOIs and URLs you opened yourself. Mark anything else [to confirm].
- Never overwrite outputs: one new run folder per run, ending in .DONE or .FAILED ([docs/HPC_JOBS.md](../../docs/HPC_JOBS.md)).
- Do not commit private data, sample details, results, host names or local paths.
