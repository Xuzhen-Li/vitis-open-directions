# Status: 45S and 5S rDNA arrays in near-complete grape assemblies

**Status: Partly run** (as of 2026-11-20, UTC+8). Plan: [README.md](README.md). Entry file: [START_HERE.md](../../START_HERE.md).

## Where it stands

An earlier line listed metadata for a very large set of near-complete angiosperm assemblies and started the merge step. It dropped the planned technology-by-recall comparison to a descriptive one, because technology metadata were missing for most assemblies and the missing data were not random. The main test was narrowed to assemblies that have long reads from the same BioSample. The planned pilot never ran, and no confirmatory result exists. This project restarts from the public assemblies of project 01 as a new study.

## Design settled earlier (reference only; write a new preregistration before running)

- Three measures: (1) site recall, compared with FISH site counts from the Plant rDNA database for species that have them; (2) collapse ratio, the assembled 45S copy number divided by a read-depth estimate (needs raw reads); (3) site position: on a chromosome, unplaced, or next to a gap.
- Classify each array as closed (unique flank on both sides) or open, as in the project README.
- The main test is limited to the subset with matched long reads. Fix that subset rule before the pilot.
- Positive control: telomere-to-telomere assemblies where the arrays are known to be closed. Ribotin can assemble rDNA morphs as an optional step.
- Pilot first: about 16 assemblies plus a few with a read-depth copy-number check, then the full set.

## Where it stopped and why

- Metadata gaps: technology and read availability are missing for most assemblies.
- The pilot was queued behind other projects and never ran.

## Next steps

1. Rebuild the assembly list from DS16 and DS17 (NCBI), with a manifest and checksums.
2. Run AM10 for 45S and 5S search; produce the descriptive closed/open catalogue first.
3. Add the long-read subset only for species where matched reads are confirmed public, accession by accession.
4. Write the preregistration before the pilot.

## Open items

- Whether partial downloads of reads are enough for the depth estimate [to confirm].
- Which minimap2 long-read preset suits rDNA depth [to confirm].
- Repeat the novelty search before writing [to confirm].

## Sources read

- Plant rDNA database: [doi:10.1111/tpj.13442](https://doi.org/10.1111/tpj.13442)
- Arabidopsis nucleolus organiser regions: [doi:10.1126/sciadv.adj4509](https://doi.org/10.1126/sciadv.adj4509)
- Maize T2T genome: [doi:10.1038/s41588-023-01419-6](https://doi.org/10.1038/s41588-023-01419-6)
- Merqury: [doi:10.1186/s13059-020-02134-9](https://doi.org/10.1186/s13059-020-02134-9)
- Ribotin: [doi:10.1093/bioinformatics/btae124](https://doi.org/10.1093/bioinformatics/btae124)
- T2T-Hub: [doi:10.1093/nar/gkag423](https://doi.org/10.1093/nar/gkag423)

## Public inputs

| Module | Dataset | Headline accessions (from the module) |
|---|---|---|
| [DS01](../../data/DS01-pn40024-references/) | PN40024 references: PN_T2T (v5), PN40024.v4 and 12X | GCF_030704535.1, GCA_030704535.1, PRJNA882193, PRJCA012093, PRJEB45423, GCF_000003745.3, PRJEA18785 |
| [DS02](../../data/DS02-grapepan-v1/) | Grapepan v1.0: T2T haplotypes, graphs and a 466-accession resequencing panel | Zenodo 10851547, Zenodo 10846425, PRJNA1018808, PRJNA1018809, PRJNA1029477, PRJNA1029480, PRJNA1130629, PRJNA1130651 |
| [DS03](../../data/DS03-vitis-super-pangenome-72/) | Vitis super-pangenome: 72 haplotype-resolved accessions | Zenodo 13982444, PRJNA1021789 |
| [DS05](../../data/DS05-vitaceae-family-genomes/) | Vitaceae family chromosome-level genomes | PRJEB88780, PRJNA1219332, PRJNA1021789, figshare 33329247, Zenodo 18590277 |
| [DS08](../../data/DS08-muscadinia-genomes/) | Muscadinia rotundifolia assemblies and reads | Zenodo 3866087, PRJNA593045, Zenodo 7944874, PRJNA935741, PRJNA780568 |
| [DS16](../../data/DS16-vitaceae-assembly-index/) | Index of all Vitaceae assemblies in NCBI | see the module |
| [DS17](../../data/DS17-angiosperm-near-complete-assemblies/) | Near-complete angiosperm assemblies (comparison set) | see the module |

## Shared steps, in order

| Order | Step | Main tools |
|---|---|---|
| 1 | [AM01](../../analyses/AM01-download-and-verify/) Download and verify | ncbi-datasets-cli, sra-tools, ENA FTP / Aspera |
| 2 | [AM05](../../analyses/AM05-assembly-qc/) Assembly QC | compleasm, BUSCO, Merqury |
| 3 | [AM10](../../analyses/AM10-repeat-arrays/) Telomeres, centromeric satellites and rDNA arrays | tidk, TRF, TRASH |

## Before any run

- Fill in [docs/PREREGISTRATION.md](../../docs/PREREGISTRATION.md) and commit it with a date before looking at results. Every restart gets a new one; criteria from earlier attempts are reference only.
- Keep an evidence log (template: [docs/EVIDENCE_LOG_TEMPLATE.md](../../docs/EVIDENCE_LOG_TEMPLATE.md)). Add entries only; never edit an old entry.
- Cite only DOIs and URLs you opened yourself. Mark anything else [to confirm].
- Never overwrite outputs: one new run folder per run, ending in .DONE or .FAILED ([docs/HPC_JOBS.md](../../docs/HPC_JOBS.md)).
- Do not commit private data, sample details, results, host names or local paths.
