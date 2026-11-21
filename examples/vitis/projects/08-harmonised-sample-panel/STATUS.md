# Status: A harmonised identity table for public grape resequencing panels

**Status: Partly run** (as of 2026-11-20, UTC+8). Plan: [README.md](README.md). Entry file: [START_HERE.md](../../../../START_HERE.md).

## Where it stands

An earlier line built genotypes for a panel of assemblies and wrote the decision rules, but its formal run did not finish. Its reference-set rule was changed after a positive control failed, which makes that change post-hoc. A population-structure step (PCA and ancestry on a local variant set) was a side line that fed other projects. Restart on the public resequencing panels (DS10, DS11, DS12) as a new study.

## Design settled earlier (reference only; write a new preregistration before running)

Assembly-only variant, useful when a panel has haplotype assemblies but no reads:

- Align each haplotype to PN40024 v4 with minimap2 -cx asm5 and call variants with paftools.js; keep biallelic SNPs covered uniquely by both haplotypes (aligned blocks of at least 10 kb); merge into a multi-sample VCF.
- Filters: missing rate at most 10%, MAF at least 0.05; prune with plink2 --indep-pairwise 50 5 0.2; kinship with plink2 --make-king-table. Fall back to IBS0 or Mash only if fewer than 10,000 SNPs remain, and report that choice.
- Rule: within the reference set, phi above 0.0625 excludes the later-ranked sample; fill up if fewer than 8; stop if fewer than 5.
- Order: KING table, a positive triangle of samples known to be related (three samples known to be related [to confirm which]), validation pairs, three merges, then a heterozygosity check.
- Define the reference set and the control triangle before the run; never adjust them after seeing a control fail.

For resequencing panels follow the project README (AM03 shared site set, AM04 with plink2 and KING, compare with VIVC names, liftover chains).

## Where it stopped and why

- The formal run failed; the first rules were adjusted after a control failed.
- Assemblies came from mixed source versions (for example a GWH and an NCBI copy of the same genome), which complicates identity.
- A VIVC SNP file with 110 markers was requested but not obtained [to confirm].

## Next steps

1. Build one sample sheet per panel from ENA reports (DS10, DS12, DS02 resequencing panel) with checksums. DS11 reads cannot be listed without an NGDC login; add DS11 after a run list is exported by hand (data/DOWNLOADS.md).
2. Genotype a shared site set (AM03); run AM04.
3. Compare with VIVC names; mark duplicates and conflicting labels.
4. Publish the table as the sample pool used by projects 09, 10, 13, 15, 16 and 17.

## Open items

- Download speed of the largest panel from NGDC [to confirm].
- Whether PCA and ancestry background figures belong here or in projects 10 and 15 [to confirm].
- Repeat the novelty search before writing [to confirm].

## Sources read

- KING-robust: [doi:10.1093/bioinformatics/btq559](https://doi.org/10.1093/bioinformatics/btq559)
- minimap2: [doi:10.1093/bioinformatics/bty191](https://doi.org/10.1093/bioinformatics/bty191)
- Grape domestication genomics: [doi:10.1073/pnas.1709257114](https://doi.org/10.1073/pnas.1709257114)
- PN T2T reference: [doi:10.1093/hr/uhad061](https://doi.org/10.1093/hr/uhad061)

## Public inputs

| Module | Dataset | Headline accessions (from the module) |
|---|---|---|
| [DS10](../../data/DS10-reseq-472-vitis/) | Resequencing of 472 Vitis accessions (and the 2017 domestication panel) | PRJNA393611, PRJNA388292 |
| [DS11](../../data/DS11-reseq-3525-dong2023/) | Resequencing of 3,525 grapevine accessions (Dong et al. 2023) | CRA006917, PRJCA009314, CRA006898 |
| [DS12](../../data/DS12-reseq-204-magris2021/) | Resequencing of 204 V. vinifera accessions (Magris et al. 2021) | PRJNA373967, PRJNA390884, PRJNA385116, PRJNA321480 |
| [DS02](../../data/DS02-grapepan-v1/) | Grapepan v1.0: T2T haplotypes, graphs and a 466-accession resequencing panel | Zenodo 10851547, Zenodo 10846425, PRJNA1018808, PRJNA1018809, PRJNA1029477, PRJNA1029480, PRJNA1130629, PRJNA1130651 (see the exact list in data/DOWNLOADS.md) |
| [DS03](../../data/DS03-vitis-super-pangenome-72/) | Vitis super-pangenome: 72 haplotype-resolved accessions | Zenodo 13982444, PRJNA1021789 |
| [DS01](../../data/DS01-pn40024-references/) | PN40024 references: PN_T2T (v5), PN40024.v4 and 12X | GCF_030704535.1, GCA_030704535.1, PRJNA882193, PRJCA012093, PRJEB45423, GCF_000003745.3, PRJEA18785 |

## Shared steps, in order

| Order | Step | Main tools |
|---|---|---|
| 1 | [AM01](../../analyses/AM01-download-and-verify/) Download and verify | ncbi-datasets-cli, sra-tools, ENA FTP / Aspera |
| 2 | [AM02](../../analyses/AM02-read-qc/) Read QC and trimming | fastp, MultiQC, seqkit |
| 3 | [AM03](../../analyses/AM03-short-read-variants/) Short-read mapping and small-variant calling | bwa-mem2, samtools, DeepVariant |
| 4 | [AM04](../../analyses/AM04-sample-identity/) Sample identity, clones and relatedness | plink2, KING, VIVC |

## Before any run

- Fill in [docs/PREREGISTRATION.md](../../../../templates/PREREGISTRATION.md) and commit it with a date before looking at results. Every restart gets a new one; criteria from earlier attempts are reference only.
- Keep an evidence log (template: [docs/EVIDENCE_LOG_TEMPLATE.md](../../../../templates/EVIDENCE_LOG_TEMPLATE.md)). Add entries only; never edit an old entry.
- Cite only DOIs and URLs you opened yourself. Mark anything else [to confirm].
- Never overwrite outputs: one new run folder per run, ending in .DONE or .FAILED ([docs/HPC_JOBS.md](../../../../templates/HPC_JOBS.md)).
- Do not commit private data, sample details, results, host names or local paths.

## Update 2026-11-21 (UTC+8)

Added as appended lines; the text above is unchanged.

- The DS02 row in Public inputs abbreviates the accession list. Use the exact list in [data/DOWNLOADS.md](../../data/DOWNLOADS.md) and do not expand it as a range; PRJNA1130635 was not found there.
- DS11 reads cannot be listed without an NGDC login (see data/DOWNLOADS.md; on 2026-11-21 the directory https://download.cncb.ac.cn/gsa/CRA006917/ returned HTTP 404). Run the first pass on DS10, DS12 and the DS02 resequencing panel, and treat DS11 as an extension queue that is added when a run list for PRJCA009314 has been exported by hand.
- Projects 23 and 24 use the clone-collapsed sample table from this project; see [project 23](../23-family-parentage/STATUS.md).
