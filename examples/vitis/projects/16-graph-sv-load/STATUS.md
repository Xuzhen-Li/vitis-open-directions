# Status: Inherited and clonal structural variants on a graph: where hemizygous SVs sit and why

**Status: Not started** (as of 2026-11-20, UTC+8). Plan: [README.md](README.md). Entry file: [START_HERE.md](../../../../START_HERE.md).

## Where it stands

No analysis has been run for the graph SV question. A separate earlier line studied runs of homozygosity (ROH) and deleterious load on a local panel; it is not carried over as its own project because load on linear references has been published (docs/NOT_KEPT.md). Its method is kept in the AM12 module and summarised in docs/EARLIER_LINES.md.

## Next steps

1. Genotype SVs through the graph (AM07) and validate on long-read samples (AM18).
2. Use the trio in DS18 to separate inherited from new SVs, with the origin labels of Fig 2 in the README.
3. Take recombination rates from published linkage maps (AM26) and record the map source [to confirm].
4. Polarise and score variants (AM26, AM12); split by zygosity; fit the models.

## Open items

- Whether public long-read data from clones are enough for the clone-specific class [to confirm].
- Source of the linkage map [to confirm].

## Sources read

- DOIs checked as Crossref records on 2026-11-21 (docs/SOURCES_CHECKED_20261121.md); full texts not read.

## Public inputs

| Module | Dataset | Headline accessions (from the module) |
|---|---|---|
| [DS02](../../data/DS02-grapepan-v1/) | Grapepan v1.0: T2T haplotypes, graphs and a 466-accession resequencing panel | Zenodo 10851547, Zenodo 10846425, PRJNA1018808, PRJNA1018809, PRJNA1029477, PRJNA1029480, PRJNA1130629, PRJNA1130651 (see the exact list in data/DOWNLOADS.md) |
| [DS03](../../data/DS03-vitis-super-pangenome-72/) | Vitis super-pangenome: 72 haplotype-resolved accessions | Zenodo 13982444, PRJNA1021789 |
| [DS10](../../data/DS10-reseq-472-vitis/) | Resequencing of 472 Vitis accessions (and the 2017 domestication panel) | PRJNA393611, PRJNA388292 |
| [DS12](../../data/DS12-reseq-204-magris2021/) | Resequencing of 204 V. vinifera accessions (Magris et al. 2021) | PRJNA373967, PRJNA390884, PRJNA385116, PRJNA321480 |
| [DS13](../../data/DS13-clone-somatic-variation/) | Clone resequencing across cultivars (Zinfandel, Chardonnay, Pinot noir, Malbec, Merlot and others) | PRJNA527006, PRJNA399599, PRJEB106155, PRJNA321480, PRJNA663442, PRJEB59893, PRJNA847341, PRJNA550461 |
| [DS18](../../data/DS18-methylome-and-trio/) | Public grape methylomes and a phased Cabernet Sauvignon trio | PRJNA1244791, PRJEB101820, PRJEB55284, PRJNA381300 |
| [DS01](../../data/DS01-pn40024-references/) | PN40024 references: PN_T2T (v5), PN40024.v4 and 12X | GCF_030704535.1, GCA_030704535.1, PRJNA882193, PRJCA012093, PRJEB45423, GCF_000003745.3, PRJEA18785 |

## Shared steps, in order

| Order | Step | Main tools |
|---|---|---|
| 1 | [AM01](../../analyses/AM01-download-and-verify/) Download and verify | ncbi-datasets-cli, sra-tools, ENA FTP / Aspera |
| 2 | [AM03](../../analyses/AM03-short-read-variants/) Short-read mapping and small-variant calling | bwa-mem2, samtools, DeepVariant |
| 3 | [AM04](../../analyses/AM04-sample-identity/) Sample identity, clones and relatedness | plink2, KING, VIVC |
| 4 | [AM07](../../analyses/AM07-graph-build-and-genotype/) Pangenome graph build and genotyping | Minigraph-Cactus, PGGB, vg |
| 5 | [AM18](../../analyses/AM18-long-read-sv/) Long-read SV calling | Sniffles2, cuteSV, pbsv |
| 6 | [AM26](../../analyses/AM26-phasing-polarisation-recombination/) Phasing, ancestral states and recombination rates | SHAPEIT5, minimap2, est-sfs |
| 7 | [AM12](../../analyses/AM12-roh-and-load/) Runs of homozygosity and deleterious load | bcftools roh, SnpEff, PlantCaduceus |

## Before any run

- Fill in [docs/PREREGISTRATION.md](../../../../templates/PREREGISTRATION.md) and commit it with a date before looking at results. Every restart gets a new one; criteria from earlier attempts are reference only.
- Keep an evidence log (template: [docs/EVIDENCE_LOG_TEMPLATE.md](../../../../templates/EVIDENCE_LOG_TEMPLATE.md)). Add entries only; never edit an old entry.
- Cite only DOIs and URLs you opened yourself. Mark anything else [to confirm].
- Never overwrite outputs: one new run folder per run, ending in .DONE or .FAILED ([docs/HPC_JOBS.md](../../../../templates/HPC_JOBS.md)).
- Do not commit private data, sample details, results, host names or local paths.

## Update 2026-11-21 (UTC+8)

Added as appended lines; the text above is unchanged.

- The DS02 row in Public inputs abbreviates the accession list. Use the exact list in [data/DOWNLOADS.md](../../data/DOWNLOADS.md) and do not expand it as a range; PRJNA1130635 was not found there.
- Study PRJNA1178252 (which includes SRR31308326) now has its own module, [DS23](../../data/DS23-hemizygous-multiomics-vitis/). It was used here before but was not in the Public inputs table above.
- Sources read: the DOIs in the project README were each opened as a Crossref record on 2026-11-21; the list is in [docs/SOURCES_CHECKED_20261121.md](../../SOURCES_CHECKED_20261121.md). The Sources read section above is unchanged.

## Note, 2026-11-21 (UTC+8): place in the six-dimension map

Dimension 3 (variation and mobile elements). Proposed on 2026-11-21: keep. This is a proposal, not a decision: the score in RANKING.md is unchanged and the folder stays as it is. The full direction map is in [examples/vitis/README.md](../../README.md).
