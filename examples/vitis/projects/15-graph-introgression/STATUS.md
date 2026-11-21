# Status: Introgression on a graph pangenome: wild-to-cultivated and hybrid cultivars

**Status: Not started** (as of 2026-11-20, UTC+8). Plan: [README.md](README.md). Entry file: [START_HERE.md](../../../../START_HERE.md).

## Where it stands

No analysis has been run and there is no earlier line behind this project. The plan in the README is complete.

## Next steps

1. Choose donor panels for each hybrid cultivar before any painting, and write them into the preregistration.
2. Genotype SVs through the graph (AM07); validate a subset against long reads or assemblies (AM18).
3. Run D, f4, f_dM and local ancestry (AM13); simulate the null where only incomplete lineage sorting acts.
4. Use the sample pool from project 08 to remove clones first.

## Open items

- Donor panels may be incomplete for some species [to confirm which species].
- Repeat the novelty search before writing [to confirm].

## Sources read

- DOIs checked as Crossref records on 2026-11-21 (docs/SOURCES_CHECKED_20261121.md); full texts not read.

## Public inputs

| Module | Dataset | Headline accessions (from the module) |
|---|---|---|
| [DS02](../../data/DS02-grapepan-v1/) | Grapepan v1.0: T2T haplotypes, graphs and a 466-accession resequencing panel | Zenodo 10851547, Zenodo 10846425, PRJNA1018808, PRJNA1018809, PRJNA1029477, PRJNA1029480, PRJNA1130629, PRJNA1130651 (see the exact list in data/DOWNLOADS.md) |
| [DS03](../../data/DS03-vitis-super-pangenome-72/) | Vitis super-pangenome: 72 haplotype-resolved accessions | Zenodo 13982444, PRJNA1021789 |
| [DS04](../../data/DS04-na-vitis-super-pangenome/) | North American Vitis super-pangenome and wild resequencing | Zenodo 8065808, Zenodo 10206475, PRJNA984685, PRJNA731597, PRJNA842753 |
| [DS19](../../data/DS19-wild-vitis-extra-panels/) | Extra wild Vitis panels (V. riparia, V. californica, 40 Vitis species) | PRJNA910315, PRJCA016655, PRJNA512170, PRJNA490319 |
| [DS10](../../data/DS10-reseq-472-vitis/) | Resequencing of 472 Vitis accessions (and the 2017 domestication panel) | PRJNA393611, PRJNA388292 |
| [DS12](../../data/DS12-reseq-204-magris2021/) | Resequencing of 204 V. vinifera accessions (Magris et al. 2021) | PRJNA373967, PRJNA390884, PRJNA385116, PRJNA321480 |
| [DS01](../../data/DS01-pn40024-references/) | PN40024 references: PN_T2T (v5), PN40024.v4 and 12X | GCF_030704535.1, GCA_030704535.1, PRJNA882193, PRJCA012093, PRJEB45423, GCF_000003745.3, PRJEA18785 |

## Shared steps, in order

| Order | Step | Main tools |
|---|---|---|
| 1 | [AM01](../../analyses/AM01-download-and-verify/) Download and verify | ncbi-datasets-cli, sra-tools, ENA FTP / Aspera |
| 2 | [AM03](../../analyses/AM03-short-read-variants/) Short-read mapping and small-variant calling | bwa-mem2, samtools, DeepVariant |
| 3 | [AM07](../../analyses/AM07-graph-build-and-genotype/) Pangenome graph build and genotyping | Minigraph-Cactus, PGGB, vg |
| 4 | [AM13](../../analyses/AM13-ancestry-and-introgression/) Ancestry and introgression | ADMIXTURE, Dsuite, ADMIXTOOLS 2 |
| 5 | [AM18](../../analyses/AM18-long-read-sv/) Long-read SV calling | Sniffles2, cuteSV, pbsv |

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
