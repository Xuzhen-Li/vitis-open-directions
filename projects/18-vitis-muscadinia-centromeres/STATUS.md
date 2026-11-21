# Status: Centromeres of Vitis and Muscadinia, and a check of the chr7 fusion point

**Status: Paused** (as of 2026-11-20, UTC+8). Plan: [README.md](README.md). Entry file: [START_HERE.md](../../START_HERE.md).

## Where it stopped

An earlier line stopped before its pilot. The satellite annotation tool TRASH was never installed successfully (two explanations were recorded: a missing R package, or a missing zlib header when building a dependency [to confirm which]). The CENH3 ChIP-seq download did not complete and no ChIP alignment exists. No satellite result exists.

## Design settled earlier (reference only; write a new preregistration before running)

- Genomes: 26 chromosome-level assemblies for the position question, plus a few long-contig genomes of another Vitaceae genus for the other two questions; one genome per species.
- H1 satellite turnover: treat the dominant satellite family of each chromosome as a discrete trait, reconstruct ancestral states, and relate the number of changes to collinear 1:1 Ks branch length.
- H2 position change: place the centromere between two collinear single-copy genes and use that as the trait.
- H3 CRM Gypsy invasion: enrichment in the centromere region tested with phylogenetic generalised least squares against root-to-tip Ks.
- H2b fusion point: check only the two anchor segments on *Vitis* chr7 (shared with project 01).
- Validation: CENH3 ChIP-seq (Bowtie2, MAPQ at least 30, MACS2 broad peaks); require agreement with published coordinates by Jaccard overlap. Species without ChIP data are called candidate repeats only; this applies to non-European grapes, *Muscadinia* and outgroups.

## Next steps

1. Try installing TRASH (AM10) in a clean environment; if it fails, use quarTeT as in the README.
2. Fetch the two CENH3 ChIP-seq runs in PRJNA1021789 and check file integrity before mapping.
3. Write the preregistration, then start with a pilot on a few genomes.

## Open items

- Why TRASH failed [to confirm].
- Whether public ChIP data exist for any species other than Chardonnay [to confirm].
- Size and checksum of the ChIP download [to confirm].

## Sources read

- Centromere tandem repeats across species: [doi:10.1186/gb-2013-14-1-r10](https://doi.org/10.1186/gb-2013-14-1-r10)
- Centromeric repeats in *Vitis vinifera*: [doi:10.1007/s00425-024-04374-6](https://doi.org/10.1007/s00425-024-04374-6)
- Cissus genome: [doi:10.1093/hr/uhac208](https://doi.org/10.1093/hr/uhac208)
- SRF satellite reconstruction: [doi:10.1101/gr.278005.123](https://doi.org/10.1101/gr.278005.123)
- Vitis super-pangenome: [doi:10.1038/s41588-025-02111-7](https://doi.org/10.1038/s41588-025-02111-7)
- Tandem Repeats Finder: [doi:10.1093/nar/27.2.573](https://doi.org/10.1093/nar/27.2.573)

## Public inputs

| Module | Dataset | Headline accessions (from the module) |
|---|---|---|
| [DS01](../../data/DS01-pn40024-references/) | PN40024 references: PN_T2T (v5), PN40024.v4 and 12X | GCF_030704535.1, GCA_030704535.1, PRJNA882193, PRJCA012093, PRJEB45423, GCF_000003745.3, PRJEA18785 |
| [DS02](../../data/DS02-grapepan-v1/) | Grapepan v1.0: T2T haplotypes, graphs and a 466-accession resequencing panel | Zenodo 10851547, Zenodo 10846425, PRJNA1018808, PRJNA1018809, PRJNA1029477, PRJNA1029480, PRJNA1130629, PRJNA1130651 |
| [DS03](../../data/DS03-vitis-super-pangenome-72/) | Vitis super-pangenome: 72 haplotype-resolved accessions | Zenodo 13982444, PRJNA1021789 |
| [DS05](../../data/DS05-vitaceae-family-genomes/) | Vitaceae family chromosome-level genomes | PRJEB88780, PRJNA1219332, PRJNA1021789, figshare 33329247, Zenodo 18590277 |
| [DS08](../../data/DS08-muscadinia-genomes/) | Muscadinia rotundifolia assemblies and reads | Zenodo 3866087, PRJNA593045, Zenodo 7944874, PRJNA935741, PRJNA780568 |

## Shared steps, in order

| Order | Step | Main tools |
|---|---|---|
| 1 | [AM01](../../analyses/AM01-download-and-verify/) Download and verify | ncbi-datasets-cli, sra-tools, ENA FTP / Aspera |
| 2 | [AM05](../../analyses/AM05-assembly-qc/) Assembly QC | compleasm, BUSCO, Merqury |
| 3 | [AM06](../../analyses/AM06-wga-and-sv/) Whole-genome alignment, synteny and SVs from assemblies | minimap2, SyRI, AnchorWave |
| 4 | [AM10](../../analyses/AM10-repeat-arrays/) Telomeres, centromeric satellites and rDNA arrays | tidk, TRF, TRASH |

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
- Suggested refinement of the validation step, not yet adopted [to confirm]: centromere arrays are tandem repeats, so a MAPQ cutoff of 30 may discard many reads that map to several array copies. Consider a main analysis that keeps one placement per read and measures enrichment against input, with MAPQ 30 kept as a separate layer for uniquely placed positions. The size of the loss has not been tested.
