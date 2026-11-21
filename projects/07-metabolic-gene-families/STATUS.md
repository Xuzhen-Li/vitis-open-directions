# Status: Copy number and birth–death of stilbene and aroma gene families (STS, TPS, CCD, LOX)

**Status: Partly run** (as of 2026-11-20, UTC+8). Plan: [README.md](README.md). Entry file: [START_HERE.md](../../START_HERE.md).

## Where it stands

Three earlier lines sit under this project. (1) A test of whether stilbene synthase (STS) arrays turn over by birth and death or by replacement within a lineage ran on a very small set of genomes with little power, and was left exploratory. (2) A paper-style draft on CCD and LOX families was written and then paused; its power simulation was designed but not run. (3) Smaller candidate-gene tests and further families (LOX, MLO, PPO, CBF) were listed but their status was never confirmed [to confirm]. They used a local population panel that is not public, so everything restarts here on public haplotypes.

## Design settled earlier (reference only; write a new preregistration before running)

- STS statistic: for each pair, log2 of the cross-genome nearest-neighbour Ks divided by the Ks of the syntenic reference; test statistic is the median over between-genus pairs minus the median over within-genus between-species pairs.
- Test: an exact permutation at genome level. With 9 genomes of which 2 are outside the genus there are only 36 label assignments, so the smallest possible p is 1/36. This design has almost no power. Use many more genomes (DS02, DS03, DS07, DS08) and fix the genome list, the number of outside genomes and the statistic before the run. A leave-one-genome-out check is a sensitivity analysis only (one genome was an outlier).
- Adding *Muscadinia* assemblies after the first result was post-hoc and exploratory; decide inclusion in advance.
- Wording gate: p at most 0.05 and every between-genus pair that can be called is a replacement.
- CCD and LOX: identify family members per haplotype, rank diversity, and correct for multiple testing (Benjamini-Hochberg). A premature stop codon is only a structural inference; do not write loss of function without expression or function evidence.
- No phenotype data: no GWAS.

## Where it stopped and why

- The pre-set threshold for the STS test was not met, so the result stays exploratory.
- Gene names for CCD4 copies and LOX members were inconsistent between drafts; keep one mapping table.
- The power simulation for the aroma families passed a statistics check but was not run.

## Next steps

1. AM08 on the four families (STS, TPS, CCD, LOX) in DS02, DS03 and DS07 haplotypes; keep a gene naming table.
2. Check arrays for collapse with read depth where reads exist.
3. Build gene trees and run CAFE 5 with the background model from the README.
4. Write the preregistration with the genome list and test statistic before any tree or Ks result is opened.

## Open items

- Which of LOX, MLO, PPO and CBF to include, and who decides [to confirm].
- Exact definition of the candidate-gene (EVA) test used earlier [to confirm].
- Naming of CCD4a and CCD4b, and LOX display names [to confirm].

## Sources read

- Stilbene synthase family, Parage et al.: [doi:10.1104/pp.112.202705](https://doi.org/10.1104/pp.112.202705)
- Stilbene synthase family, Vannozzi et al.: [doi:10.1186/1471-2229-12-130](https://doi.org/10.1186/1471-2229-12-130)
- CCD family functions: [doi:10.1186/1471-2229-13-156](https://doi.org/10.1186/1471-2229-13-156)
- PN T2T reference: [doi:10.1093/hr/uhad061](https://doi.org/10.1093/hr/uhad061)
- Grape domestication genomics: [doi:10.1073/pnas.1709257114](https://doi.org/10.1073/pnas.1709257114)

## Public inputs

| Module | Dataset | Headline accessions (from the module) |
|---|---|---|
| [DS01](../../data/DS01-pn40024-references/) | PN40024 references: PN_T2T (v5), PN40024.v4 and 12X | GCF_030704535.1, GCA_030704535.1, PRJNA882193, PRJCA012093, PRJEB45423, GCF_000003745.3, PRJEA18785 |
| [DS02](../../data/DS02-grapepan-v1/) | Grapepan v1.0: T2T haplotypes, graphs and a 466-accession resequencing panel | Zenodo 10851547, Zenodo 10846425, PRJNA1018808, PRJNA1018809, PRJNA1029477, PRJNA1029480, PRJNA1130629, PRJNA1130651 (see the exact list in data/DOWNLOADS.md) |
| [DS03](../../data/DS03-vitis-super-pangenome-72/) | Vitis super-pangenome: 72 haplotype-resolved accessions | Zenodo 13982444, PRJNA1021789 |
| [DS07](../../data/DS07-cultivated-16-pangenome/) | Cultivated grapevine pangenome (16 cultivars, Plastivigne) | PRJEB100755, PRJEB95058, PRJEB107006 |
| [DS08](../../data/DS08-muscadinia-genomes/) | Muscadinia rotundifolia assemblies and reads | Zenodo 3866087, PRJNA593045, Zenodo 7944874, PRJNA935741, PRJNA780568 |
| [DS10](../../data/DS10-reseq-472-vitis/) | Resequencing of 472 Vitis accessions (and the 2017 domestication panel) | PRJNA393611, PRJNA388292 |

## Shared steps, in order

| Order | Step | Main tools |
|---|---|---|
| 1 | [AM01](../../analyses/AM01-download-and-verify/) Download and verify | ncbi-datasets-cli, sra-tools, ENA FTP / Aspera |
| 2 | [AM05](../../analyses/AM05-assembly-qc/) Assembly QC | compleasm, BUSCO, Merqury |
| 3 | [AM08](../../analyses/AM08-gene-family-annotation/) Gene-family search across haplotypes | miniprot, HMMER, InterProScan |
| 4 | [AM09](../../analyses/AM09-gene-pav-and-cnv/) Gene presence/absence and copy number | Liftoff, OrthoFinder, mosdepth |

## Before any run

- Fill in [docs/PREREGISTRATION.md](../../docs/PREREGISTRATION.md) and commit it with a date before looking at results. Every restart gets a new one; criteria from earlier attempts are reference only.
- Keep an evidence log (template: [docs/EVIDENCE_LOG_TEMPLATE.md](../../docs/EVIDENCE_LOG_TEMPLATE.md)). Add entries only; never edit an old entry.
- Cite only DOIs and URLs you opened yourself. Mark anything else [to confirm].
- Never overwrite outputs: one new run folder per run, ending in .DONE or .FAILED ([docs/HPC_JOBS.md](../../docs/HPC_JOBS.md)).
- Do not commit private data, sample details, results, host names or local paths.

## Update 2026-11-21 (UTC+8)

Added as appended lines; the text above is unchanged.

- The DS02 row in Public inputs abbreviates the accession list. Use the exact list in [data/DOWNLOADS.md](../../data/DOWNLOADS.md) and do not expand it as a range; PRJNA1130635 was not found there.
- Default for the gene families: STS, TPS, CCD and LOX, as in the project title; MLO, PPO and CBF stay out until the maintainer decides (see [docs/DEFAULTS.md](../../docs/DEFAULTS.md)).
