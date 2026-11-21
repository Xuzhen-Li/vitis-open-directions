# Status: Somatic mutation spectra across grape cultivars, with rates where clone dates are known

**Status: Not started** (as of 2026-11-20, UTC+8). Plan: [README.md](README.md). Entry file: [START_HERE.md](../../START_HERE.md).

## Where it stands

No analysis has been run for this project. One related earlier idea exists: a possible copy-neutral loss of heterozygosity on chromosome 2 in one cultivar clone. It stayed at the plan stage, with three explanations kept side by side (a deletion, copy-neutral loss of heterozygosity, or an assembly problem). It needs raw reads from that clone, and whether public reads exist was never confirmed [to confirm]. If they exist, it fits here as a case study using the segment-level LOH calls in the README steps. Missing pieces: allele-fraction plus depth together, independent validation, and breakpoint mapping.

## Next steps

1. Assemble the clone list from DS13; confirm identity with AM04; keep cultivars with at least three clones for directional calls.
2. Build masks (mappability, repeats, centromeres) before calling.
3. Pilot on one cultivar; call with AM20; estimate callable bp and sensitivity.
4. Collect documented clone dates from the source papers; the rate is an upper bound only.

## Open items

- Clone dates may be undocumented; the rate paper runs only if enough dated, independent branches exist [to confirm].
- Whether public reads exist for the clone behind the chromosome 2 idea [to confirm].

## Sources read

- Clone methylome and genome study, Callipo et al.: [doi:10.1186/s13059-026-04184-x](https://doi.org/10.1186/s13059-026-04184-x)
- The other references listed in the project README.

## Public inputs

| Module | Dataset | Headline accessions (from the module) |
|---|---|---|
| [DS13](../../data/DS13-clone-somatic-variation/) | Clone resequencing across cultivars (Zinfandel, Chardonnay, Pinot noir, Malbec, Merlot and others) | PRJNA527006, PRJNA399599, PRJEB106155, PRJNA321480, PRJNA663442, PRJEB59893, PRJNA847341, PRJNA550461 |
| [DS01](../../data/DS01-pn40024-references/) | PN40024 references: PN_T2T (v5), PN40024.v4 and 12X | GCF_030704535.1, GCA_030704535.1, PRJNA882193, PRJCA012093, PRJEB45423, GCF_000003745.3, PRJEA18785 |
| [DS02](../../data/DS02-grapepan-v1/) | Grapepan v1.0: T2T haplotypes, graphs and a 466-accession resequencing panel | Zenodo 10851547, Zenodo 10846425, PRJNA1018808, PRJNA1018809, PRJNA1029477, PRJNA1029480, PRJNA1130629, PRJNA1130651 (see the exact list in data/DOWNLOADS.md) |

## Shared steps, in order

| Order | Step | Main tools |
|---|---|---|
| 1 | [AM01](../../analyses/AM01-download-and-verify/) Download and verify | ncbi-datasets-cli, sra-tools, ENA FTP / Aspera |
| 2 | [AM02](../../analyses/AM02-read-qc/) Read QC and trimming | fastp, MultiQC, seqkit |
| 3 | [AM03](../../analyses/AM03-short-read-variants/) Short-read mapping and small-variant calling | bwa-mem2, samtools, DeepVariant |
| 4 | [AM04](../../analyses/AM04-sample-identity/) Sample identity, clones and relatedness | plink2, KING, VIVC |
| 5 | [AM20](../../analyses/AM20-somatic-variants/) Somatic variants among clones and mutation spectra | DeepSomatic, GATK Mutect2, GenMap |

## Before any run

- Fill in [docs/PREREGISTRATION.md](../../docs/PREREGISTRATION.md) and commit it with a date before looking at results. Every restart gets a new one; criteria from earlier attempts are reference only.
- Keep an evidence log (template: [docs/EVIDENCE_LOG_TEMPLATE.md](../../docs/EVIDENCE_LOG_TEMPLATE.md)). Add entries only; never edit an old entry.
- Cite only DOIs and URLs you opened yourself. Mark anything else [to confirm].
- Never overwrite outputs: one new run folder per run, ending in .DONE or .FAILED ([docs/HPC_JOBS.md](../../docs/HPC_JOBS.md)).
- Do not commit private data, sample details, results, host names or local paths.

## Update 2026-11-21 (UTC+8)

Added as appended lines; the text above is unchanged.

- The DS02 row in Public inputs abbreviates the accession list. Use the exact list in [data/DOWNLOADS.md](../../data/DOWNLOADS.md) and do not expand it as a range; PRJNA1130635 was not found there.
