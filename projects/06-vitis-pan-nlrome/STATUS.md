# Status: A genus-wide NLR catalogue with integrated domains and collapse checks

**Status: Plan fixed** (as of 2026-11-20, UTC+8). Plan: [README.md](README.md). Entry file: [START_HERE.md](../../START_HERE.md).

## Where it stands

The design was written and the NLR tools were being installed. No main result exists. It was planned as a second section of the same paper as project 05.

## Design settled earlier (reference only; write a new preregistration before running)

- Samples: deduplicated as in project 05. Use technical-replicate pairs (the same genotype assembled twice, divergence below 1 per kb); with fewer than 5 such pairs the strong-evidence criterion becomes descriptive. Two pairs are used only to set parameters.
- Identification: method a NLR-Annotator; method b hmmsearch with PF00931 at E at most 1e-5. A cluster is adjacent NLRs at most 200 kb apart with at most 8 non-NLR genes between (sensitivity: 100 kb with 4, and 400 kb with 12). Pair homologous clusters by three single-copy anchor genes on each side.
- Decision order, stop at the first hit: gap; suspected collapse (the low-copy side has a shorter cluster than expected and the high-copy side has copies at least 99.5% identical); U; real candidate. Tool disagreement is a separate label. Where HiFi reads exist, check depth.
- Primary endpoint: in the layer where both methods agree, the share of technical cases, (gap + suspected collapse) over all pairs with a copy-number difference. Lower 95% bound above 10% means assembly-type overestimation; upper bound below 5% means negligible. Strong evidence: the ratio of the mismatch rate in replicate pairs to the rate in different-individual pairs, with the lower 95% bound at least 0.5.
- Controls: simulate deleted copies, merged copies and N insertions (200 each) with recall at least 90%; 500 single-copy NB-ARC loci with a false difference rate at most 8%. With fewer than 150 pairs showing a difference, report descriptively.

## Where it stopped and why

- Tools were not yet confirmed as installed; the number of technical-replicate pairs was never counted.
- A motif-scan step for NLR promoters had open errors and was not finished [to confirm what it was for].

## Next steps

1. Count technical-replicate pairs from DS03 and the other haplotype sources first; the answer decides whether the strong-evidence part is possible.
2. AM08 and AM18 as in the README; HiFi reads from the DS03 BioProject can be fetched on demand.
3. Run the simulation controls before any real comparison.

## Open items

- Number of replicate pairs [to confirm].
- Whether HiFi depth is available for enough samples [to confirm].

## Sources read

- NLR-Annotator: [doi:10.1104/pp.19.01273](https://doi.org/10.1104/pp.19.01273)
- Vitis super-pangenome: [doi:10.1038/s41588-025-02111-7](https://doi.org/10.1038/s41588-025-02111-7)
- Grapevine pangenome: [doi:10.1038/s41588-024-01967-5](https://doi.org/10.1038/s41588-024-01967-5)
- minimap2: [doi:10.1093/bioinformatics/bty191](https://doi.org/10.1093/bioinformatics/bty191)

## Public inputs

| Module | Dataset | Headline accessions (from the module) |
|---|---|---|
| [DS01](../../data/DS01-pn40024-references/) | PN40024 references: PN_T2T (v5), PN40024.v4 and 12X | GCF_030704535.1, GCA_030704535.1, PRJNA882193, PRJCA012093, PRJEB45423, GCF_000003745.3, PRJEA18785 |
| [DS02](../../data/DS02-grapepan-v1/) | Grapepan v1.0: T2T haplotypes, graphs and a 466-accession resequencing panel | Zenodo 10851547, Zenodo 10846425, PRJNA1018808, PRJNA1018809, PRJNA1029477, PRJNA1029480, PRJNA1130629, PRJNA1130651 |
| [DS03](../../data/DS03-vitis-super-pangenome-72/) | Vitis super-pangenome: 72 haplotype-resolved accessions | Zenodo 13982444, PRJNA1021789 |
| [DS04](../../data/DS04-na-vitis-super-pangenome/) | North American Vitis super-pangenome and wild resequencing | Zenodo 8065808, Zenodo 10206475, PRJNA984685, PRJNA731597, PRJNA842753 |
| [DS06](../../data/DS06-vitis-amurensis-pangenome/) | Vitis amurensis haplotype assemblies and 330-sample resequencing | PRJNA1272278, PRJNA1272285, Zenodo 16534920, PRJNA1308837, PRJNA1089859, PRJCA046381 |
| [DS08](../../data/DS08-muscadinia-genomes/) | Muscadinia rotundifolia assemblies and reads | Zenodo 3866087, PRJNA593045, Zenodo 7944874, PRJNA935741, PRJNA780568 |

## Shared steps, in order

| Order | Step | Main tools |
|---|---|---|
| 1 | [AM01](../../analyses/AM01-download-and-verify/) Download and verify | ncbi-datasets-cli, sra-tools, ENA FTP / Aspera |
| 2 | [AM05](../../analyses/AM05-assembly-qc/) Assembly QC | compleasm, BUSCO, Merqury |
| 3 | [AM08](../../analyses/AM08-gene-family-annotation/) Gene-family search across haplotypes | miniprot, HMMER, InterProScan |
| 4 | [AM09](../../analyses/AM09-gene-pav-and-cnv/) Gene presence/absence and copy number | Liftoff, OrthoFinder, mosdepth |
| 5 | [AM18](../../analyses/AM18-long-read-sv/) Long-read SV calling | Sniffles2, cuteSV, pbsv |

## Before any run

- Fill in [docs/PREREGISTRATION.md](../../docs/PREREGISTRATION.md) and commit it with a date before looking at results. Every restart gets a new one; criteria from earlier attempts are reference only.
- Keep an evidence log (template: [docs/EVIDENCE_LOG_TEMPLATE.md](../../docs/EVIDENCE_LOG_TEMPLATE.md)). Add entries only; never edit an old entry.
- Cite only DOIs and URLs you opened yourself. Mark anything else [to confirm].
- Never overwrite outputs: one new run folder per run, ending in .DONE or .FAILED ([docs/HPC_JOBS.md](../../docs/HPC_JOBS.md)).
- Do not commit private data, sample details, results, host names or local paths.
