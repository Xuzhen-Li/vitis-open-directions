# Status: Endogenous florendovirus insertions across grape haplotypes

**Status: Not started** (as of 2026-11-20, UTC+8). Plan: [README.md](README.md). Entry file: [START_HERE.md](../../../../START_HERE.md).

## Where it stands

No analysis has been run and there is no earlier line behind this project. The plan in the README is complete. Everything below is about how to start.

## Next steps

1. Fix the seed set: choose florendovirus protein sequences and record each accession in the preregistration [to confirm which accessions].
2. Pilot on two assemblies from DS01 and DS02: DIAMOND search (AM16), cluster hits into loci by flanking sequence (AM06), score present or absent per haplotype.
3. Check that flanks inside repeats do not make loci merge or split; keep a flag for uncertain orthology.
4. Scale to all haplotypes (DS01 to DS06) only after the pilot matrix looks stable.

## Open items

- Repeat the novelty search before writing [to confirm].
- Choice of seed proteins and distance cut-off [to confirm].

## Sources read

- DOIs checked as Crossref records on 2026-11-21 (docs/SOURCES_CHECKED_20261121.md); full texts not read.

## Public inputs

| Module | Dataset | Headline accessions (from the module) |
|---|---|---|
| [DS01](../../data/DS01-pn40024-references/) | PN40024 references: PN_T2T (v5), PN40024.v4 and 12X | GCF_030704535.1, GCA_030704535.1, PRJNA882193, PRJCA012093, PRJEB45423, GCF_000003745.3, PRJEA18785 |
| [DS02](../../data/DS02-grapepan-v1/) | Grapepan v1.0: T2T haplotypes, graphs and a 466-accession resequencing panel | Zenodo 10851547, Zenodo 10846425, PRJNA1018808, PRJNA1018809, PRJNA1029477, PRJNA1029480, PRJNA1130629, PRJNA1130651 (see the exact list in data/DOWNLOADS.md) |
| [DS03](../../data/DS03-vitis-super-pangenome-72/) | Vitis super-pangenome: 72 haplotype-resolved accessions | Zenodo 13982444, PRJNA1021789 |
| [DS04](../../data/DS04-na-vitis-super-pangenome/) | North American Vitis super-pangenome and wild resequencing | Zenodo 8065808, Zenodo 10206475, PRJNA984685, PRJNA731597, PRJNA842753 |
| [DS05](../../data/DS05-vitaceae-family-genomes/) | Vitaceae family chromosome-level genomes | PRJEB88780, PRJNA1219332, PRJNA1021789, figshare 33329247, Zenodo 18590277 |
| [DS06](../../data/DS06-vitis-amurensis-pangenome/) | Vitis amurensis haplotype assemblies and 330-sample resequencing | PRJNA1272278, PRJNA1272285, Zenodo 16534920, PRJNA1308837, PRJNA1089859, PRJCA046381 |

## Shared steps, in order

| Order | Step | Main tools |
|---|---|---|
| 1 | [AM01](../../analyses/AM01-download-and-verify/) Download and verify | ncbi-datasets-cli, sra-tools, ENA FTP / Aspera |
| 2 | [AM05](../../analyses/AM05-assembly-qc/) Assembly QC | compleasm, BUSCO, Merqury |
| 3 | [AM16](../../analyses/AM16-virus-and-eve-search/) Virus discovery in RNA-seq and endogenous viral elements in assemblies | DIAMOND, MEGAHIT, SPAdes (rnaviralSPAdes) |
| 4 | [AM06](../../analyses/AM06-wga-and-sv/) Whole-genome alignment, synteny and SVs from assemblies | minimap2, SyRI, AnchorWave |

## Before any run

- Fill in [docs/PREREGISTRATION.md](../../../../templates/PREREGISTRATION.md) and commit it with a date before looking at results. Every restart gets a new one; criteria from earlier attempts are reference only.
- Keep an evidence log (template: [docs/EVIDENCE_LOG_TEMPLATE.md](../../../../templates/EVIDENCE_LOG_TEMPLATE.md)). Add entries only; never edit an old entry.
- Cite only DOIs and URLs you opened yourself. Mark anything else [to confirm].
- Never overwrite outputs: one new run folder per run, ending in .DONE or .FAILED ([docs/HPC_JOBS.md](../../../../templates/HPC_JOBS.md)).
- Do not commit private data, sample details, results, host names or local paths.

## Update 2026-11-21 (UTC+8)

Added as appended lines; the text above is unchanged.

- The DS02 row in Public inputs abbreviates the accession list. Use the exact list in [data/DOWNLOADS.md](../../data/DOWNLOADS.md) and do not expand it as a range; PRJNA1130635 was not found there.
- The Geering 2014 supplementary table is a genome-organisation summary, and no accession set or sequence file for the 76 reconstructed genomes was found (data/DOWNLOADS.md). A default seed set is in [docs/DEFAULTS.md](../../DEFAULTS.md): sequences taken from the coordinates listed by Bertsch et al. 2009 on the 12X assembly. NCBI or ICTV reference sequences are a second source; record every accession in the preregistration [to confirm which].
- Sources read: the DOIs in the project README were each opened as a Crossref record on 2026-11-21; the list is in [docs/SOURCES_CHECKED_20261121.md](../../SOURCES_CHECKED_20261121.md). The Sources read section above is unchanged.
