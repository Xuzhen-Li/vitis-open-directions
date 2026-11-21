# Status: Family parentage and relationship QC on public grape records

**Status: Plan fixed** (as of 2026-11-21, UTC+8). Entry file: [START_HERE.md](../../START_HERE.md). Feeds [project 24](../24-recombination-maps/STATUS.md); uses the identity work of [project 08](../08-harmonised-sample-panel/STATUS.md).

## Where it stands

A detailed, conditional design for checking parent-offspring and pedigree relationships was written earlier. It has not been run. The design treats reported parent-offspring links as claims to be checked, not as already verified facts. It keeps five counting layers separate: candidate parent-offspring edges, offspring (zygotes), candidate meioses, distinguishable gamete transmissions, and informative meioses in non-overlapping intervals. Aliases, clones, repeat sequencing and somatic sports are kept in the records but do not add sexual meioses.

The earlier design also refers to a private genotype panel and a chosen private reference sequence. Those materials are not part of this repository: the panel size, sample list, and the reference accession and hash were not verified as public and are not given here. This page covers only what can be done from public records and public genotypes.

## Design settled earlier (reference only; write a new preregistration before running)

- First step: an identity and pedigree inventory (stable IDs, aliases, clone or duplicate flags, evidence for each relationship, missing parents, possible selfing). This inventory is a catalogue of sources, not an analysis of genotypes.
- Do not convert a count of candidate parent-offspring edges into a count of independent meioses or crossover maps.
- Shared parents, co-parents, grandparents, offspring and clones must stay linked in validation; parent-offspring edges must not be randomly split into cross-validation folds.
- Children used to fit a joint family model cannot be reused as an independent check of the same crossover calls.
- Selfed offspring with unresolved egg versus pollen roles stay as a joint record; they are not split into two fake gamete maps.

## Where it stopped and why

The design is complete as a conditional plan. No real genotypes were read for this line, and no relationship graph was verified.

## Next steps

1. Take the clone-collapsed sample table and the biallelic SNP set from project 08 (DS10, DS12, DS02; DS11 only after its run list can be exported, see below).
2. Fix depth and genotype-quality filters in the preregistration before computing IBS0, KING kinship and Mendelian error. Low depth can drop one heterozygous allele and mimic a Mendelian violation, so the filters must be set before any result is seen.
3. Use the phased Cabernet Sauvignon trio in DS18 as a positive control for the thresholds, and add literature-documented cultivar trios (VIVC and published papers) as further controls [to confirm which trios].
4. Compile public parentage and identity records (the published inventory in Laucou et al. 2018, plus VIVC) and compare them with the genotype-based calls. Flag conflicting labels; do not overwrite them.
5. Export one validated pedigree table, with the evidence for each edge, for projects 10, 15, 16, 21 and 24.
6. Keep private family tables, if they exist, off this repository; only methods belong here.

## Open items

- Minimum depth for reliable heterozygous calls in the public panels [to confirm].
- Which literature-documented trios form the positive-control set [to confirm].
- Accession and hash of the private reference used in the earlier design [to confirm].
- Whether any of those private families have a public deposit that can be used here [to confirm].
- How much of the Laucou et al. 2018 parentage list can be linked to public resequencing runs [to confirm].
- Repeat the novelty search on published grapevine parentage studies before writing [to confirm].

## Sources read

All entries below were opened as Crossref records on 2026-11-21 (abstract level; full text not read).

- Laucou et al. 2018, extended diversity analysis of cultivated grapevine with 10K genome-wide SNPs (the parentage assignments in it are used as an inventory; the count and the sample list are [to confirm] from the full text): [doi:10.1371/journal.pone.0192540](https://doi.org/10.1371/journal.pone.0192540)
- Manichaikul et al. 2010, robust relationship inference (KING-robust): [doi:10.1093/bioinformatics/btq559](https://doi.org/10.1093/bioinformatics/btq559)
- Magris et al. 2021, the genomes of 204 Vitis vinifera accessions (DS12): [doi:10.1038/s41467-021-27487-y](https://doi.org/10.1038/s41467-021-27487-y)
- Cochetel et al. 2025, phased epigenomics and methylation inheritance in a historical Vitis vinifera hybrid (the DS18 trio): [doi:10.1186/s13059-025-03858-2](https://doi.org/10.1186/s13059-025-03858-2)
- Vervalle et al. 2022, integrated grapevine map from three mapping populations: [doi:10.1007/s00122-022-04225-6](https://doi.org/10.1007/s00122-022-04225-6)
- OConnell et al. 2014, duoHMM: [doi:10.1371/journal.pgen.1004234](https://doi.org/10.1371/journal.pgen.1004234)
- Relationship-aware phasing notes already in [AM26](../../analyses/AM26-phasing-polarisation-recombination/)

## Public inputs

| Module | Dataset | Headline accessions (from the module) |
|---|---|---|
| [DS10](../../data/DS10-reseq-472-vitis/) | Resequencing of 472 Vitis accessions (and the 2017 domestication panel) | PRJNA393611, PRJNA388292 |
| [DS12](../../data/DS12-reseq-204-magris2021/) | Resequencing of 204 V. vinifera accessions (Magris et al. 2021) | PRJNA373967, PRJNA390884, PRJNA385116, PRJNA321480 |
| [DS02](../../data/DS02-grapepan-v1/) | Grapepan v1.0 resequencing panel (466 accessions genotyped in the paper) | PRJNA994294 (see the exact list in data/DOWNLOADS.md) |
| [DS18](../../data/DS18-methylome-and-trio/) | Phased Cabernet Sauvignon trio (positive control) | PRJNA1244791 |
| [DS11](../../data/DS11-reseq-3525-dong2023/) | Resequencing of 3,525 grapevine accessions (Dong et al. 2023); reads cannot be listed without an NGDC login, see data/DOWNLOADS.md | PRJCA009314, CRA006917 |
| [DS01](../../data/DS01-pn40024-references/) | PN40024 references: PN_T2T (v5), PN40024.v4 and 12X | GCF_030704535.1, PRJNA882193, PRJEB45423, GCF_000003745.3 |

The private panel from the earlier design is not listed here.

## Shared steps, in order

| Order | Step | Main tools |
|---|---|---|
| 1 | [AM01](../../analyses/AM01-download-and-verify/) Download selected public runs | ENA FTP, md5sum |
| 2 | [AM03](../../analyses/AM03-short-read-variants/) Mapping and calling if new calls are needed | bwa-mem2, DeepVariant, GLnexus |
| 3 | [AM04](../../analyses/AM04-sample-identity/) Identity, clones and relatedness | plink2, KING, VIVC |
| 4 | [AM26](../../analyses/AM26-phasing-polarisation-recombination/) Relationship-aware phasing and Mendelian consistency check, if used later by project 24 | SHAPEIT5 (AM26); bcftools (AM03) |

## Before any run

- Fill in [docs/PREREGISTRATION.md](../../docs/PREREGISTRATION.md) and commit it with a date before looking at results. Every restart gets a new one; criteria from earlier attempts are reference only.
- Keep an evidence log (template: [docs/EVIDENCE_LOG_TEMPLATE.md](../../docs/EVIDENCE_LOG_TEMPLATE.md)). Add entries only; never edit an old entry.
- Cite only DOIs and URLs you opened yourself. Mark anything else [to confirm].
- Never overwrite outputs: one new run folder per run, ending in .DONE or .FAILED ([docs/HPC_JOBS.md](../../docs/HPC_JOBS.md)).
- Do not commit private data, sample details, results, host names or local paths.
