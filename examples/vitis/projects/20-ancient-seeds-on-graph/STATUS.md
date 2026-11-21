# Status: Archaeological grape seeds: graph mapping and low-coverage imputation

**Status: Not started** (as of 2026-11-20, UTC+8). Plan: [README.md](README.md). Entry file: [START_HERE.md](../../../../START_HERE.md).

## Where it stopped

No analysis has been run and there is no earlier line behind this project.

## Next steps

1. Check each ancient-seed accession in DS14 for raw reads, one by one [to confirm which have reads].
2. Process with nf-core/eager (AM17); map to the linear and the graph reference; measure bias.
3. Downsample modern samples to seed depths; test GLIMPSE2; then impute seeds.

## Open items

- Coverage may be too low for any analysis; set a minimum depth in the preregistration.
- Repeat the novelty search before writing [to confirm].

## Sources read

- DOIs checked as Crossref records on 2026-11-21 (docs/SOURCES_CHECKED_20261121.md); full texts not read.

## Public inputs

| Module | Dataset | Headline accessions (from the module) |
|---|---|---|
| [DS14](../../data/DS14-ancient-grape-seeds/) | Archaeological grape seed sequencing | PRJNA489970, figshare 7610987, PRJEB89110, PRJEB94459, PRJNA999173 |
| [DS02](../../data/DS02-grapepan-v1/) | Grapepan v1.0: T2T haplotypes, graphs and a 466-accession resequencing panel | Zenodo 10851547, Zenodo 10846425, PRJNA1018808, PRJNA1018809, PRJNA1029477, PRJNA1029480, PRJNA1130629, PRJNA1130651 (see the exact list in data/DOWNLOADS.md) |
| [DS10](../../data/DS10-reseq-472-vitis/) | Resequencing of 472 Vitis accessions (and the 2017 domestication panel) | PRJNA393611, PRJNA388292 |
| [DS12](../../data/DS12-reseq-204-magris2021/) | Resequencing of 204 V. vinifera accessions (Magris et al. 2021) | PRJNA373967, PRJNA390884, PRJNA385116, PRJNA321480 |

## Shared steps, in order

| Order | Step | Main tools |
|---|---|---|
| 1 | [AM01](../../analyses/AM01-download-and-verify/) Download and verify | ncbi-datasets-cli, sra-tools, ENA FTP / Aspera |
| 2 | [AM17](../../analyses/AM17-ancient-dna/) Ancient DNA processing | nf-core/eager, mapDamage2, vg |
| 3 | [AM07](../../analyses/AM07-graph-build-and-genotype/) Pangenome graph build and genotyping | Minigraph-Cactus, PGGB, vg |
| 4 | [AM13](../../analyses/AM13-ancestry-and-introgression/) Ancestry and introgression | ADMIXTURE, Dsuite, ADMIXTOOLS 2 |

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
