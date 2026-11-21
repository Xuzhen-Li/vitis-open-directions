# Status: TE insertion polymorphisms in cultivated grape from graph genotyping

**Status: Plan fixed** (as of 2026-11-20, UTC+8). Plan: [README.md](README.md). Entry file: [START_HERE.md](../../../../START_HERE.md).

## Where it stands

A full design and a locked preregistration existed for an assembly-based version of this project. No main-set output was ever produced. The line stopped while fixing the annotation step and the rules for clones. Parts of the idea overlap with the TE catalogue repository (vitis-te); the default split is in docs/DEFAULTS.md [to confirm whether to merge].

## Design settled earlier (reference only; write a new preregistration before running)

- Unit of analysis: individuals (assemblies), after collapsing clones. Two haplotypes of one individual count as one layer. Without an outgroup the polarity is unknown, so call the result presence/absence polymorphism, not insertion.
- Alignment: minimap2 asm5 between haplotypes and asm10 for the outgroup (asm20 as sensitivity); keep indels of at least 300 bp. Present side: at least 80% of the fragment annotated by RepeatMasker as one family. Absent side: an empty gap with collinear 5 kb flanks, MAPQ at least 20 and no N.
- Classes: confirmed (4 to 6 bp target-site duplication), probable, solo-LTR, excision footprint, undetermined. Merge calls of the same family within 50 bp into one site.
- LTR age: only for intact LTR elements with a duplication; K2P distance d between 5 prime and 3 prime LTR; T = d / 2r, reported as a range with a source for r. State the unit of r: a generation time is needed only if r is per site per generation [to confirm].
- Primary endpoint (method check): difference in median d between polymorphic and shared LTR elements, one-sided Mann-Whitney plus a within-family permutation (10,000); supported if p below 0.01 and the direction agrees in at least two of three large families.
- Controls: plant 200 known elements with duplications (recall at least 90%, breakpoint error at most 50 bp), 100 solo-LTRs (recall at least 90%), duplicate-pair false sites at most 5% of the main median, simulated LTR pairs recovering the d slope between 0.95 and 1.05. If power is below 80% the endpoint becomes descriptive.
- Annotation: one EDTA run per assembly with a custom library only; prefix each library entry with the assembly name; cluster with cd-hit-est 80-80-80; no copy-number filter on full-length copies. panEDTA calls EDTA with annotation on and needs a RepeatMasker output per genome, which conflicts with this design.

## Where it stopped and why

- EDTA failed twice on the compute site: the FamDB root partition file was missing, and RepeatMasker lacked its RMBlast engine configuration. An offline fix (empty FAMDB_DIR in a fresh copy, library through -lib only) was planned but untested.
- A reference assembly entry was missing from the file manifest, so the reference check could not be done.
- Rules for the shared-versus-polymorphic definition and for target-site duplications were being tightened; keep them mechanical and fix them before any run.

## Next steps

1. Use the default split in docs/DEFAULTS.md: build the insertion library here; reuse vitis-te documents and scripts after reading them [to confirm].
2. AM01, AM05; build a manifest with sequence checksums and check them before the first run.
3. Test the EDTA fix on synthetic sequence only; then run the pilot on two assemblies to set parameters.
4. Run controls before the main set; use AM19 and AM07 for graph genotyping of insertions.

## Open items

- Outgroup species [to confirm].
- Candidate tools noted by a repository scan: GraffiTE, TIPMAP, McClintock 2 [to confirm fit and versions].
- Source for the substitution rate r and generation time [to confirm].

## Sources read

- Structural variants in grape domestication: [doi:10.1038/s41477-019-0507-8](https://doi.org/10.1038/s41477-019-0507-8)
- TE families from pangenome polymorphisms: [doi:10.1186/s13100-024-00323-y](https://doi.org/10.1186/s13100-024-00323-y)
- EDTA: [doi:10.1186/s13059-019-1905-y](https://doi.org/10.1186/s13059-019-1905-y)
- minimap2: [doi:10.1093/bioinformatics/bty191](https://doi.org/10.1093/bioinformatics/bty191)
- SyRI: [doi:10.1186/s13059-019-1911-0](https://doi.org/10.1186/s13059-019-1911-0)
- Vitis super-pangenome: [doi:10.1038/s41588-025-02111-7](https://doi.org/10.1038/s41588-025-02111-7)

## Public inputs

| Module | Dataset | Headline accessions (from the module) |
|---|---|---|
| [DS02](../../data/DS02-grapepan-v1/) | Grapepan v1.0: T2T haplotypes, graphs and a 466-accession resequencing panel | Zenodo 10851547, Zenodo 10846425, PRJNA1018808, PRJNA1018809, PRJNA1029477, PRJNA1029480, PRJNA1130629, PRJNA1130651 (see the exact list in data/DOWNLOADS.md) |
| [DS03](../../data/DS03-vitis-super-pangenome-72/) | Vitis super-pangenome: 72 haplotype-resolved accessions | Zenodo 13982444, PRJNA1021789 |
| [DS07](../../data/DS07-cultivated-16-pangenome/) | Cultivated grapevine pangenome (16 cultivars, Plastivigne) | PRJEB100755, PRJEB95058, PRJEB107006 |
| [DS10](../../data/DS10-reseq-472-vitis/) | Resequencing of 472 Vitis accessions (and the 2017 domestication panel) | PRJNA393611, PRJNA388292 |
| [DS12](../../data/DS12-reseq-204-magris2021/) | Resequencing of 204 V. vinifera accessions (Magris et al. 2021) | PRJNA373967, PRJNA390884, PRJNA385116, PRJNA321480 |
| [DS01](../../data/DS01-pn40024-references/) | PN40024 references: PN_T2T (v5), PN40024.v4 and 12X | GCF_030704535.1, GCA_030704535.1, PRJNA882193, PRJCA012093, PRJEB45423, GCF_000003745.3, PRJEA18785 |

## Shared steps, in order

| Order | Step | Main tools |
|---|---|---|
| 1 | [AM01](../../analyses/AM01-download-and-verify/) Download and verify | ncbi-datasets-cli, sra-tools, ENA FTP / Aspera |
| 2 | [AM05](../../analyses/AM05-assembly-qc/) Assembly QC | compleasm, BUSCO, Merqury |
| 3 | [AM06](../../analyses/AM06-wga-and-sv/) Whole-genome alignment, synteny and SVs from assemblies | minimap2, SyRI, AnchorWave |
| 4 | [AM19](../../analyses/AM19-te-insertion-polymorphism/) TE insertion polymorphisms among haplotypes | GraffiTE, McClintock 2, RepeatMasker |
| 5 | [AM07](../../analyses/AM07-graph-build-and-genotype/) Pangenome graph build and genotyping | Minigraph-Cactus, PGGB, vg |

## Before any run

- Fill in [docs/PREREGISTRATION.md](../../../../templates/PREREGISTRATION.md) and commit it with a date before looking at results. Every restart gets a new one; criteria from earlier attempts are reference only.
- Keep an evidence log (template: [docs/EVIDENCE_LOG_TEMPLATE.md](../../../../templates/EVIDENCE_LOG_TEMPLATE.md)). Add entries only; never edit an old entry.
- Cite only DOIs and URLs you opened yourself. Mark anything else [to confirm].
- Never overwrite outputs: one new run folder per run, ending in .DONE or .FAILED ([docs/HPC_JOBS.md](../../../../templates/HPC_JOBS.md)).
- Do not commit private data, sample details, results, host names or local paths.

## Update 2026-11-21 (UTC+8)

Added as appended lines; the text above is unchanged.

- The DS02 row in Public inputs abbreviates the accession list. Use the exact list in [data/DOWNLOADS.md](../../data/DOWNLOADS.md) and do not expand it as a range; PRJNA1130635 was not found there.
- Split with the vitis-te catalogue: by default this project builds its own insertion library from public assemblies and does not wait for a file from vitis-te, because the catalogue has no standalone TE library FASTA at the recorded commit (data/DOWNLOADS.md). The methods survey of TE annotation is [project 25](../25-te-annotation-methods/STATUS.md). The default is in [docs/DEFAULTS.md](../../DEFAULTS.md); merging the two projects is still the maintainer decision [to confirm].
- LTR age: state the unit of r. If r is per site per year, T = d / 2r is already in years and no generation time is needed. A generation time is needed only if r is per site per generation. For a perennial that is often propagated by cuttings, generation time needs its own definition. Prefer a published per-year rate range [to confirm the source].

## Note, 2026-11-21 (UTC+8): place in the six-dimension map

Dimension 3 (variation and mobile elements). Proposed on 2026-11-21: keep. Split from project 25: project 14 is the analysis and builds its own insertion library; project 25 is the methods survey. This is a proposal, not a decision: the score in RANKING.md is unchanged and the folder stays as it is. The full direction map is in [examples/vitis/README.md](../../README.md).
