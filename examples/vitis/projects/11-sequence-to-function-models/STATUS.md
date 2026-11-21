# Status: Sequence-to-expression models and plant foundation models evaluated on grape

**Status: Not started** (as of 2026-11-20, UTC+8). Plan: [README.md](README.md). Entry file: [START_HERE.md](../../../../START_HERE.md).

## Where it stands

No analysis has been run and there is no earlier line behind this project. It is a large project and depends on project 19 for expression tables.

## Next steps

1. Wait for the project 19 expression tables, or rebuild them with AM01, AM02 and AM15; do not mix the two.
2. Fix splits by chromosome and by gene family before training anything, to stop leakage between paralogues.
3. Start with the k-mer baseline and the grape-only model; add other-plant models only after the baseline is stable.
4. Confirm GPU access and the cost estimate first.

## Open items

- Tissue mixing in public RNA-seq adds noise; decide which tissues to keep [to confirm].
- Repeat the novelty search before writing [to confirm].

## Sources read

- DOIs checked as Crossref records on 2026-11-21 (docs/SOURCES_CHECKED_20261121.md); full texts not read.

## Public inputs

| Module | Dataset | Headline accessions (from the module) |
|---|---|---|
| [DS01](../../data/DS01-pn40024-references/) | PN40024 references: PN_T2T (v5), PN40024.v4 and 12X | GCF_030704535.1, GCA_030704535.1, PRJNA882193, PRJCA012093, PRJEB45423, GCF_000003745.3, PRJEA18785 |
| [DS15](../../data/DS15-rnaseq-public-vitis/) | Public Vitis RNA-seq and the expression atlas | PRJNA565689, PRJNA434655, PRJEB107006, PRJNA260535, PRJNA674915, PRJNA915033, GSE36128 |
| [DS02](../../data/DS02-grapepan-v1/) | Grapepan v1.0: T2T haplotypes, graphs and a 466-accession resequencing panel | Zenodo 10851547, Zenodo 10846425, PRJNA1018808, PRJNA1018809, PRJNA1029477, PRJNA1029480, PRJNA1130629, PRJNA1130651 (see the exact list in data/DOWNLOADS.md) |

## Shared steps, in order

| Order | Step | Main tools |
|---|---|---|
| 1 | [AM01](../../analyses/AM01-download-and-verify/) Download and verify | ncbi-datasets-cli, sra-tools, ENA FTP / Aspera |
| 2 | [AM02](../../analyses/AM02-read-qc/) Read QC and trimming | fastp, MultiQC, seqkit |
| 3 | [AM15](../../analyses/AM15-rnaseq-quant-and-ase/) RNA-seq quantification and allele-specific expression | salmon, STAR, gffread |
| 4 | [AM22](../../analyses/AM22-sequence-to-function-models/) Sequence-to-expression models and plant foundation models | PyTorch, PlantCaduceus, AgroNT |

## Before any run

- Fill in [docs/PREREGISTRATION.md](../../../../templates/PREREGISTRATION.md) and commit it with a date before looking at results. Every restart gets a new one; criteria from earlier attempts are reference only.
- Keep an evidence log (template: [docs/EVIDENCE_LOG_TEMPLATE.md](../../../../templates/EVIDENCE_LOG_TEMPLATE.md)). Add entries only; never edit an old entry.
- Cite only DOIs and URLs you opened yourself. Mark anything else [to confirm].
- Never overwrite outputs: one new run folder per run, ending in .DONE or .FAILED ([docs/HPC_JOBS.md](../../../../templates/HPC_JOBS.md)).
- Do not commit private data, sample details, results, host names or local paths.

## Update 2026-11-21 (UTC+8)

Added as appended lines; the text above is unchanged.

- The DS02 row in Public inputs abbreviates the accession list. Use the exact list in [data/DOWNLOADS.md](../../data/DOWNLOADS.md) and do not expand it as a range; PRJNA1130635 was not found there.
- Sources read: the DOIs in the project README were each opened as a Crossref record on 2026-11-21; the list is in [docs/SOURCES_CHECKED_20261121.md](../../SOURCES_CHECKED_20261121.md). The Sources read section above is unchanged.
