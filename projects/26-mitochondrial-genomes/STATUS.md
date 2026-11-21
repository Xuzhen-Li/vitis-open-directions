# Status: Grapevine mitochondrial genomes, nuclear mitochondrial insertions and heteroplasmy

**Status: Not started** (as of 2026-11-21, UTC+8). Entry file: [START_HERE.md](../../START_HERE.md). Related public chloroplast catalogue: [grapevine-plastid](https://github.com/Xuzhen-Li/grapevine-plastid).

## Where it stands

This line was set later as a mitochondrial-genome project, in place of expanding chloroplast pangenome work. No design document from earlier work was found, so the question, tools and pass rules below are a proposed starting design, not a fixed plan. What published work already listed in [docs/NOT_KEPT.md](../../docs/NOT_KEPT.md) says: nuclear insertions of mitochondrial and plastid DNA (NUMTs and NUPTs) have been described, including in grape, and both organelle genomes of at least one public rootstock cultivar have been deposited. A systematic treatment on the T2T nuclear reference together with organelle heteroplasmy is still open in that note; any such work must first remove NUMT and NUPT reads and allow for recombination-derived mitochondrial configurations.

No analysis has been run for this project in this repository. The grapevine-plastid catalogue covers chloroplast assembly and plastid pangenome methods, not mitochondrion-specific plans.

## Proposed starting design (to be fixed in a preregistration)

- Plant mitochondrial genomes often hold large repeats that recombine, so one circular sequence may not describe the molecules in a cell. The design must keep assembly graphs and alternative configurations, not only one circle.
- Candidate question set: (a) a catalogue of complete mitochondrial genomes across Vitis and Muscadinia from public long reads; (b) NUMT and plastid-to-mitochondrion transfer masks on PN_T2T, so organelle-derived sequence does not contaminate nuclear variant calls; (c) a maternal phylogeny from the organelle sequences; (d) heteroplasmy, only after (a) to (b) work. Which of these is the project is [to confirm].
- Positive control: the RefSeq grape mitochondrial genome NC_012119.1 (Vitis vinifera mitochondrion, complete genome, 773,279 bp; NCBI record read 2026-11-21).
- Candidate assembly tools with published papers: Oatk, PMAT, and Flye with graph inspection. Which are installable on the compute site is [to confirm].

## Next steps

1. Inventory public mitochondrial sequences (RefSeq and INSDC organelle records, and organelle sequence released with the T2T and pangenome papers) from the Vitaceae index in DS16 and the modules below; confirm each accession [to confirm: complete public list].
2. Write the preregistration: coverage thresholds, NUMT exclusion rules (read depth and nuclear synteny checks), annotation standards, and the pass rule for the positive control.
3. Pilot on a small number of public long-read sets (for example PN40024 reads in DS01 and two accessions in DS02) and compare with NC_012119.1.
4. If the pilot passes, scale to the other public long-read sets, annotate genes, tRNAs, rRNAs, repeats and plastid-derived transfers, and export PN_T2T NUMT masks for the nuclear projects.
5. Do not commit private organelle assemblies.

## Open items

- The question that defines the project, among (a) to (d) above [to confirm].
- The software list and versions [to confirm].
- Whether mitochondrial sequences travel with the public PN_T2T or pangenome deposits already in DS01 to DS03 [to confirm].
- How this project should share methods with the grapevine-plastid catalogue [to confirm].
- A complete list of public Vitis mitochondrial genome accessions [to confirm].
- Repeat the novelty search on recent Vitis mitochondrial genome papers before writing [to confirm].

## Sources read

Papers below were opened as Crossref records on 2026-11-21 (abstract level; full text not read). The RefSeq record was read from NCBI on the same date.

- Hou et al. 2025, cytonuclear interactions during grapevine domestication: [doi:10.1111/jipb.13968](https://doi.org/10.1111/jipb.13968)
- Frommer et al. 2020, genome sequences of both organelles of the grapevine rootstock cultivar Borner: [doi:10.1128/mra.01471-19](https://doi.org/10.1128/mra.01471-19)
- Michalovova et al. 2013, NUPTs and NUMTs in six plant species: [doi:10.1038/hdy.2013.51](https://doi.org/10.1038/hdy.2013.51)
- Zhou et al. 2025, Oatk, a de novo assembly tool for complex plant organelle genomes: [doi:10.1186/s13059-025-03676-6](https://doi.org/10.1186/s13059-025-03676-6)
- Bi et al. 2024, PMAT, a plant mitogenome assembly toolkit: [doi:10.1093/hr/uhae023](https://doi.org/10.1093/hr/uhae023)
- Kolmogorov et al. 2019, Flye: [doi:10.1038/s41587-019-0072-8](https://doi.org/10.1038/s41587-019-0072-8)
- RefSeq NC_012119.1: [https://www.ncbi.nlm.nih.gov/nuccore/NC_012119.1](https://www.ncbi.nlm.nih.gov/nuccore/NC_012119.1)
- [docs/NOT_KEPT.md](../../docs/NOT_KEPT.md) in this repository (organelle row)
- [grapevine-plastid README](https://github.com/Xuzhen-Li/grapevine-plastid) (chloroplast catalogue; opened 2026-11-21)

## Public inputs

| Module or source | What it provides | Headline accessions or URL |
|---|---|---|
| [DS01](../../data/DS01-pn40024-references/) | Public nuclear T2T and v4 references and PN40024 reads | GCF_030704535.1, PRJNA882193, PRJEB45423, GCF_000003745.3 |
| [DS02](../../data/DS02-grapepan-v1/) | Grapepan v1.0 long reads and Hi-C | PRJNA1048106 |
| [DS03](../../data/DS03-vitis-super-pangenome-72/) | Vitis super-pangenome, 72 haplotype-resolved accessions | PRJNA1021789 |
| [DS04](../../data/DS04-na-vitis-super-pangenome/) | North American Vitis super-pangenome and reads | PRJNA984685, PRJNA731597, PRJNA842753 |
| [DS06](../../data/DS06-vitis-amurensis-pangenome/) | Vitis amurensis reads | PRJNA1308837 |
| [DS08](../../data/DS08-muscadinia-genomes/) | Muscadinia assemblies and reads | PRJNA593045, PRJNA935741, PRJNA780568 |
| [DS16](../../data/DS16-vitaceae-assembly-index/) | Index of all Vitaceae assemblies in NCBI | assemblies_vitaceae_ncbi_20261114.tsv |
| NCBI RefSeq | Grape mitochondrial reference (positive control) | NC_012119.1 |
| Frommer et al. 2020 | Mitochondrial and plastid genomes of a rootstock cultivar | doi:10.1128/mra.01471-19 |
| [grapevine-plastid](https://github.com/Xuzhen-Li/grapevine-plastid) | Chloroplast methods only, for shared assembly practice | GitHub repository |

Whether each of these deposits holds reads that cover the mitochondrial genome is [to confirm] before a pilot.

## Shared steps, in order

| Order | Step | Main tools |
|---|---|---|
| 1 | [AM01](../../analyses/AM01-download-and-verify/) Download public organelle and nuclear references and reads | ncbi-datasets-cli, sra-tools, ENA FTP |
| 2 | Organelle assembly and graph inspection, only after the preregistration | Oatk, PMAT or Flye; tools to pin [to confirm] |
| 3 | NUMT and NUPT screening on PN_T2T, if that question is locked | BLAST-type search and read depth; tools to pin [to confirm] |
| 4 | [AM23](../../analyses/AM23-cross-crop-convergence/) Shared tree tools for a maternal phylogeny, if locked | MAFFT, IQ-TREE |

## Before any run

- Fill in [docs/PREREGISTRATION.md](../../docs/PREREGISTRATION.md) and commit it with a date before looking at results. Every restart gets a new one; criteria from earlier attempts are reference only.
- Keep an evidence log (template: [docs/EVIDENCE_LOG_TEMPLATE.md](../../docs/EVIDENCE_LOG_TEMPLATE.md)). Add entries only; never edit an old entry.
- Cite only DOIs and URLs you opened yourself. Mark anything else [to confirm].
- Never overwrite outputs: one new run folder per run, ending in .DONE or .FAILED ([docs/HPC_JOBS.md](../../docs/HPC_JOBS.md)).
- Do not commit private data, sample details, results, host names or local paths.
