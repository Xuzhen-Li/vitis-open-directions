# Status: Gene presence/absence across grape pangenomes under one pipeline

**Status: Plan fixed** (as of 2026-11-20, UTC+8). Plan: [README.md](README.md). Entry file: [START_HERE.md](../../../../START_HERE.md).

## Where it stands

A full design was written and tools were being installed on a compute site. No main result exists. The earlier design grew into many small addenda; a restart should hold one preregistration that contains the final rules.

## Design settled earlier (reference only; write a new preregistration before running)

- Data: use one consistent source of haplotype assemblies as the main set; other sources only as sensitivity. Treat two assemblies as the same if coverage is at least 0.95 and divergence is at most 0.1 per kb. Choose pairs of different individuals with a fixed random seed (at least 20 pairs; with fewer than 12 pairs the project becomes descriptive). Add two same-individual hap1/hap2 pairs as a control layer.
- Method: for each gene take the longest CDS transcript, extract proteins (gffread), project proteins from assembly A onto genome B with miniprot (Liftoff as sensitivity), in both directions. Call a gene absent in the other assembly if no gene model overlaps the projected region by at least 50% of the CDS, or there is no projection. Draw 100 random candidates per pair and direction.
- Classes, applied in this order, stop at the first hit: M missed annotation (protein coverage and identity at least 90%, no frameshift or stop); P partial or pseudogene; G assembly gap (20 kb flanks collinear but N or a contig break in between); U unresolved; R candidate true absence. T (TE-related) is a separate label.
- Primary endpoint: the share of artefacts among non-T cases, (M+G) over all including U, with the more conservative of a BCa bootstrap and a logit random-effects interval. Lower bound above 10% means annotation-type PAV is clearly overestimated; upper bound below 5% means negligible; otherwise uncertain.
- Controls before unblinding: 200 planted cases per class M, G, R, P, T with recall at least 90%; 500 homologous genes present in both assemblies as a negative control with the upper 95% limit of wrong "absent" calls at most 8%.
- Pair with project 06 as one paper with two sections (F2 in docs/INDEX.md).

## Where it stopped and why

- Tool installation and some data preparation steps were unfinished. The lineage reference used by OMArk (a gene-set completeness tool) could not be reached from the compute site at the time; a source is now recorded in data/DOWNLOADS.md (Zenodo record 10.5281/zenodo.20814376). Check connectivity first.
- Some controls are correlated with the TE label; this is a known limitation and should be stated.

## Next steps

1. AM01 and AM05 on DS02, DS03, DS04, DS06, DS07; build an inventory of annotation files.
2. Deduplicate assemblies and fix the pair list with the seed.
3. Run miniprot projection and the class rules on two pairs to set parameters only; do not look at the primary endpoint.
4. Run the controls; unblind only if all pass.

## Open items

- Which OMArk lineage file to use for grape (default in docs/DEFAULTS.md) [to confirm].
- Final count of distinct-individual pairs after deduplication [to confirm].
- Whether any published PAV claims can be re-tested directly (the earlier line collected a list of published claims; rebuild it from the papers) [to confirm].

## Sources read

- Brassica oleracea pangenome: [doi:10.1038/ncomms13390](https://doi.org/10.1038/ncomms13390)
- Grapevine pangenome: [doi:10.1038/s41588-024-01967-5](https://doi.org/10.1038/s41588-024-01967-5)
- Vitis super-pangenome: [doi:10.1038/s41588-025-02111-7](https://doi.org/10.1038/s41588-025-02111-7)
- miniprot: [doi:10.1093/bioinformatics/btad014](https://doi.org/10.1093/bioinformatics/btad014)
- minimap2: [doi:10.1093/bioinformatics/bty191](https://doi.org/10.1093/bioinformatics/bty191)

## Public inputs

| Module | Dataset | Headline accessions (from the module) |
|---|---|---|
| [DS01](../../data/DS01-pn40024-references/) | PN40024 references: PN_T2T (v5), PN40024.v4 and 12X | GCF_030704535.1, GCA_030704535.1, PRJNA882193, PRJCA012093, PRJEB45423, GCF_000003745.3, PRJEA18785 |
| [DS02](../../data/DS02-grapepan-v1/) | Grapepan v1.0: T2T haplotypes, graphs and a 466-accession resequencing panel | Zenodo 10851547, Zenodo 10846425, PRJNA1018808, PRJNA1018809, PRJNA1029477, PRJNA1029480, PRJNA1130629, PRJNA1130651 (see the exact list in data/DOWNLOADS.md) |
| [DS03](../../data/DS03-vitis-super-pangenome-72/) | Vitis super-pangenome: 72 haplotype-resolved accessions | Zenodo 13982444, PRJNA1021789 |
| [DS04](../../data/DS04-na-vitis-super-pangenome/) | North American Vitis super-pangenome and wild resequencing | Zenodo 8065808, Zenodo 10206475, PRJNA984685, PRJNA731597, PRJNA842753 |
| [DS06](../../data/DS06-vitis-amurensis-pangenome/) | Vitis amurensis haplotype assemblies and 330-sample resequencing | PRJNA1272278, PRJNA1272285, Zenodo 16534920, PRJNA1308837, PRJNA1089859, PRJCA046381 |
| [DS07](../../data/DS07-cultivated-16-pangenome/) | Cultivated grapevine pangenome (16 cultivars, Plastivigne) | PRJEB100755, PRJEB95058, PRJEB107006 |

## Shared steps, in order

| Order | Step | Main tools |
|---|---|---|
| 1 | [AM01](../../analyses/AM01-download-and-verify/) Download and verify | ncbi-datasets-cli, sra-tools, ENA FTP / Aspera |
| 2 | [AM05](../../analyses/AM05-assembly-qc/) Assembly QC | compleasm, BUSCO, Merqury |
| 3 | [AM09](../../analyses/AM09-gene-pav-and-cnv/) Gene presence/absence and copy number | Liftoff, OrthoFinder, mosdepth |
| 4 | [AM08](../../analyses/AM08-gene-family-annotation/) Gene-family search across haplotypes | miniprot, HMMER, InterProScan |

## Before any run

- Fill in [docs/PREREGISTRATION.md](../../../../templates/PREREGISTRATION.md) and commit it with a date before looking at results. Every restart gets a new one; criteria from earlier attempts are reference only.
- Keep an evidence log (template: [docs/EVIDENCE_LOG_TEMPLATE.md](../../../../templates/EVIDENCE_LOG_TEMPLATE.md)). Add entries only; never edit an old entry.
- Cite only DOIs and URLs you opened yourself. Mark anything else [to confirm].
- Never overwrite outputs: one new run folder per run, ending in .DONE or .FAILED ([docs/HPC_JOBS.md](../../../../templates/HPC_JOBS.md)).
- Do not commit private data, sample details, results, host names or local paths.

## Update 2026-11-21 (UTC+8)

Added as appended lines; the text above is unchanged.

- The DS02 row in Public inputs abbreviates the accession list. Use the exact list in [data/DOWNLOADS.md](../../data/DOWNLOADS.md) and do not expand it as a range; PRJNA1130635 was not found there.
- OMArk lineage data: a source is recorded in data/DOWNLOADS.md (Zenodo record 10.5281/zenodo.20814376, files Viridiplantae.h5 and LUCA.h5). The default is in [docs/DEFAULTS.md](../../DEFAULTS.md). This replaces the open item that says the source was unknown, except for which file OMArk expects for grape [to confirm].
- Projects 05 and 06 form one paper with two sections. Run one assembly de-duplication and one pairwise distance matrix, and write two tables from it: pairs of different individuals (for this project) and same-genotype technical-replicate pairs (for project 06). The thresholds in the two pages differ (here: coverage at least 0.95 and divergence at most 0.1 per kb to call two assemblies the same; in project 06: divergence below 1 per kb for a technical-replicate pair). Fix both in one preregistration [to confirm that one script can serve both].
