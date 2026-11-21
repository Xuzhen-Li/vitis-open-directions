# Status: Convergent domestication: grape compared with other crops in one pipeline

**Status: Not started** (as of 2026-11-20, UTC+8). Plan: [README.md](README.md). Entry file: [START_HERE.md](../../START_HERE.md).

## Where it stands

No analysis has been run. The direction came out of a literature survey that compared grape with other crops; the hard parts are the null model and orthology.

## Next steps

1. Confirm accessions for each comparison crop in DS21 before choosing crops.
2. Choose crops and sample sizes first; downsample to equal sizes so scan power is comparable.
3. Run AM03 and AM11 the same way for each crop; map to orthogroups (AM23); define the null before testing overlap.

## Open items

- One-to-many orthology from lineage-specific duplications; decide how to count [to confirm].
- Repeat the novelty search before writing [to confirm].

## Sources read

- DOIs checked as Crossref records on 2026-11-21 (docs/SOURCES_CHECKED_20261121.md); full texts not read.

## Public inputs

| Module | Dataset | Headline accessions (from the module) |
|---|---|---|
| [DS10](../../data/DS10-reseq-472-vitis/) | Resequencing of 472 Vitis accessions (and the 2017 domestication panel) | PRJNA393611, PRJNA388292 |
| [DS12](../../data/DS12-reseq-204-magris2021/) | Resequencing of 204 V. vinifera accessions (Magris et al. 2021) | PRJNA373967, PRJNA390884, PRJNA385116, PRJNA321480 |
| [DS21](../../data/DS21-other-crop-population-genomes/) | Population genomes of other domesticated plants (comparison set) | see the module |
| [DS01](../../data/DS01-pn40024-references/) | PN40024 references: PN_T2T (v5), PN40024.v4 and 12X | GCF_030704535.1, GCA_030704535.1, PRJNA882193, PRJCA012093, PRJEB45423, GCF_000003745.3, PRJEA18785 |

## Shared steps, in order

| Order | Step | Main tools |
|---|---|---|
| 1 | [AM01](../../analyses/AM01-download-and-verify/) Download and verify | ncbi-datasets-cli, sra-tools, ENA FTP / Aspera |
| 2 | [AM03](../../analyses/AM03-short-read-variants/) Short-read mapping and small-variant calling | bwa-mem2, samtools, DeepVariant |
| 3 | [AM11](../../analyses/AM11-diversity-and-selection/) Diversity and selection scans | pixy, vcftools, RAiSD |
| 4 | [AM23](../../analyses/AM23-cross-crop-convergence/) Cross-crop orthology and convergence tests | OrthoFinder, MAFFT, IQ-TREE |

## Before any run

- Fill in [docs/PREREGISTRATION.md](../../docs/PREREGISTRATION.md) and commit it with a date before looking at results. Every restart gets a new one; criteria from earlier attempts are reference only.
- Keep an evidence log (template: [docs/EVIDENCE_LOG_TEMPLATE.md](../../docs/EVIDENCE_LOG_TEMPLATE.md)). Add entries only; never edit an old entry.
- Cite only DOIs and URLs you opened yourself. Mark anything else [to confirm].
- Never overwrite outputs: one new run folder per run, ending in .DONE or .FAILED ([docs/HPC_JOBS.md](../../docs/HPC_JOBS.md)).
- Do not commit private data, sample details, results, host names or local paths.

## Update 2026-11-21 (UTC+8)

Added as appended lines; the text above is unchanged.

- Sources read: the DOIs in the project README were each opened as a Crossref record on 2026-11-21; the list is in [docs/SOURCES_CHECKED_20261121.md](../../docs/SOURCES_CHECKED_20261121.md). The Sources read section above is unchanged.
