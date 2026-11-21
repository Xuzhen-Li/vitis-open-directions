# Status: Public RNA-seq on PN_T2T: expression atlas, eQTL/sQTL and allele-specific expression

**Status: Not started** (as of 2026-11-20, UTC+8). Plan: [README.md](README.md). Entry file: [START_HERE.md](../../START_HERE.md).

## Where it stopped

No analysis has been run and there is no earlier line behind this project. The plan in the README is complete; the atlas part is the quick one, sQTL and eQTL are riskier.

## Next steps

1. Curate metadata (DS15) and assign each run to a genotype with AM04; record which runs cannot be assigned.
2. Fix the annotation (DS01 RefSeq by default) and build transcripts, tx2gene and a gene ID map to v4 and 12X.
3. Atlas first: salmon and tximport (AM15). Then splicing and ASE with STAR and WASP.
4. Map eQTL and sQTL only within study by tissue subsets (AM21); use the trio in DS18 to estimate residual allele bias.

## Open items

- Study, tissue and genotype are collinear in public data; decide the minimum design for QTL before running [to confirm].
- Gene ID differences between the default annotation and the Grapedia release [to confirm].

## Sources read

- DOIs checked as Crossref records on 2026-11-21 (docs/SOURCES_CHECKED_20261121.md); full texts not read.

## Public inputs

| Module | Dataset | Headline accessions (from the module) |
|---|---|---|
| [DS15](../../data/DS15-rnaseq-public-vitis/) | Public Vitis RNA-seq and the expression atlas | PRJNA565689, PRJNA434655, PRJEB107006, PRJNA260535, PRJNA674915, PRJNA915033, GSE36128 |
| [DS01](../../data/DS01-pn40024-references/) | PN40024 references: PN_T2T (v5), PN40024.v4 and 12X | GCF_030704535.1, GCA_030704535.1, PRJNA882193, PRJCA012093, PRJEB45423, GCF_000003745.3, PRJEA18785 |
| [DS02](../../data/DS02-grapepan-v1/) | Grapepan v1.0: T2T haplotypes, graphs and a 466-accession resequencing panel | Zenodo 10851547, Zenodo 10846425, PRJNA1018808, PRJNA1018809, PRJNA1029477, PRJNA1029480, PRJNA1130629, PRJNA1130651 (see the exact list in data/DOWNLOADS.md) |
| [DS10](../../data/DS10-reseq-472-vitis/) | Resequencing of 472 Vitis accessions (and the 2017 domestication panel) | PRJNA393611, PRJNA388292 |
| [DS18](../../data/DS18-methylome-and-trio/) | Public grape methylomes and a phased Cabernet Sauvignon trio | PRJNA1244791, PRJEB101820, PRJEB55284, PRJNA381300 |

## Shared steps, in order

| Order | Step | Main tools |
|---|---|---|
| 1 | [AM01](../../analyses/AM01-download-and-verify/) Download and verify | ncbi-datasets-cli, sra-tools, ENA FTP / Aspera |
| 2 | [AM02](../../analyses/AM02-read-qc/) Read QC and trimming | fastp, MultiQC, seqkit |
| 3 | [AM04](../../analyses/AM04-sample-identity/) Sample identity, clones and relatedness | plink2, KING, VIVC |
| 4 | [AM03](../../analyses/AM03-short-read-variants/) Short-read mapping and small-variant calling (DNA) | bwa-mem2, samtools, DeepVariant |
| 5 | [AM26](../../analyses/AM26-phasing-polarisation-recombination/) Phasing only, then per-sample heterozygous VCFs | SHAPEIT5, bcftools |
| 6 | [AM15](../../analyses/AM15-rnaseq-quant-and-ase/) RNA-seq quantification and allele-specific expression | salmon, STAR, gffread |
| 7 | [AM21](../../analyses/AM21-eqtl-and-sqtl/) eQTL and splicing QTL | tensorQTL, LeafCutter, regtools |

## Before any run

- Fill in [docs/PREREGISTRATION.md](../../docs/PREREGISTRATION.md) and commit it with a date before looking at results. Every restart gets a new one; criteria from earlier attempts are reference only.
- Keep an evidence log (template: [docs/EVIDENCE_LOG_TEMPLATE.md](../../docs/EVIDENCE_LOG_TEMPLATE.md)). Add entries only; never edit an old entry.
- Cite only DOIs and URLs you opened yourself. Mark anything else [to confirm].
- Never overwrite outputs: one new run folder per run, ending in .DONE or .FAILED ([docs/HPC_JOBS.md](../../docs/HPC_JOBS.md)).
- Do not commit private data, sample details, results, host names or local paths.

## Update 2026-11-21 (UTC+8)

Added as appended lines; the text above is unchanged.

- The DS02 row in Public inputs abbreviates the accession list. Use the exact list in [data/DOWNLOADS.md](../../data/DOWNLOADS.md) and do not expand it as a range; PRJNA1130635 was not found there.
- Study PRJNA1178252 (which includes SRR31308326) now has its own module, [DS23](../../data/DS23-hemizygous-multiomics-vitis/). It was used here before but was not in the Public inputs table above.
- Sources read: the DOIs in the project README were each opened as a Crossref record on 2026-11-21; the list is in [docs/SOURCES_CHECKED_20261121.md](../../docs/SOURCES_CHECKED_20261121.md). The Sources read section above is unchanged.
