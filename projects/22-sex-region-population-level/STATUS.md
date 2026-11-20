# Status: Population-level evolution of the sex-determining region (demoted)

**Status: Not started** (as of 2026-11-20, UTC+8). Plan: [README.md](README.md). Entry file: [START_HERE.md](../../START_HERE.md).

## Where it stopped

No analysis has been run. The project is demoted in the ranking: the cross-genus comparison is already done, and what remains needs reliable sex records in wild panels.

## Next steps

1. Check first whether public wild samples with recorded sex exist [to confirm].
2. Check whether flower small-RNA libraries by sex type exist (DS20) before the optional phasiRNA part [to confirm].
3. Genotype the region (AM03) and build haplotype networks only if the sex records are enough.

## Open items

- Sex records are sparse; decide the minimum sample size first.

## Sources read

- The references listed in the project README and docs/NOT_KEPT.md.

## Public inputs

| Module | Dataset | Headline accessions (from the module) |
|---|---|---|
| [DS09](../../data/DS09-sex-locus-haplotypes/) | Sex-determination region haplotypes and reads | Zenodo 3827985, PRJNA593045, PRJNA1151724 |
| [DS10](../../data/DS10-reseq-472-vitis/) | Resequencing of 472 Vitis accessions (and the 2017 domestication panel) | PRJNA393611, PRJNA388292 |
| [DS20](../../data/DS20-small-rna-public/) | Public grape small-RNA data | GSE59802 |
| [DS01](../../data/DS01-pn40024-references/) | PN40024 references: PN_T2T (v5), PN40024.v4 and 12X | GCF_030704535.1, GCA_030704535.1, PRJNA882193, PRJCA012093, PRJEB45423, GCF_000003745.3, PRJEA18785 |

## Shared steps, in order

| Order | Step | Main tools |
|---|---|---|
| 1 | [AM01](../../analyses/AM01-download-and-verify/) Download and verify | ncbi-datasets-cli, sra-tools, ENA FTP / Aspera |
| 2 | [AM03](../../analyses/AM03-short-read-variants/) Short-read mapping and small-variant calling | bwa-mem2, samtools, DeepVariant |
| 3 | [AM25](../../analyses/AM25-small-rna-phasirna/) Small-RNA and phasiRNA loci | fastp, ShortStack, samtools |

## Before any run

- Fill in [docs/PREREGISTRATION.md](../../docs/PREREGISTRATION.md) and commit it with a date before looking at results. Every restart gets a new one; criteria from earlier attempts are reference only.
- Keep an evidence log (template: [docs/EVIDENCE_LOG_TEMPLATE.md](../../docs/EVIDENCE_LOG_TEMPLATE.md)). Add entries only; never edit an old entry.
- Cite only DOIs and URLs you opened yourself. Mark anything else [to confirm].
- Never overwrite outputs: one new run folder per run, ending in .DONE or .FAILED ([docs/HPC_JOBS.md](../../docs/HPC_JOBS.md)).
- Do not commit private data, sample details, results, host names or local paths.
