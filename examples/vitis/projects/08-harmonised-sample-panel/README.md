# 08. A harmonised identity table for public grape resequencing panels

中文：公开重测序群体的统一样本身份表

Rank 8 of 22 (score F 3 + N 2 + E 2 = 7; see docs/RANKING.md) · Tier: Medium (E = 2, effort range ending after 6 weeks and by 4 months) · Origin: continued: started earlier and restarted here from public data under a new preregistration · Status: draft v0.3.2, 2026-11-14

## Gap

Public panels share accessions under different names and contain clones. A cross-panel identity table with genetic duplicates, label conflicts and coordinate conversion was not found.

**Existing work**

- [Urra et al. 2023](https://doi.org/10.1093/g3journal/jkad145): clone identification by amplicon sequencing.
- [Tello et al. 2025](https://doi.org/10.1093/hr/uhaf237): resequencing and genotyping trace cultivar origins.
- [Magris et al. 2021](https://doi.org/10.1038/s41467-021-27487-y): 204 cultivars resequenced.
- [Dong et al. 2023](https://doi.org/10.1126/science.add8655): 3,525 accessions resequenced.

**How this project differs**

Covers all large public panels at once, uses preregistered kinship thresholds, and releases the table and liftover chains.

**Background survey (literature read for this plan)**

Grape cultivars carry many synonyms and homonyms after centuries of vegetative propagation and exchange. The Vitis International Variety Catalogue (VIVC) assigns accessions to prime names using a standard set of nine SSR markers ([Maul and Töpfer 2015](https://doi.org/10.1051/bioconf/20150501009)); SSR profiles of 1,005 accessions uncovered new synonyms and parentages ([Cipriani et al. 2010](https://doi.org/10.1007/s00122-010-1411-9)); a 48-SNP set was proposed for cultivar identification ([Cabezas et al. 2011](https://doi.org/10.1186/1471-2229-11-153)); and high-throughput genotyping was used to manage a large germplasm collection ([Laucou et al. 2011](https://doi.org/10.1007/s00122-010-1527-y)), followed by large-scale parentage analysis ([Lacombe et al. 2013](https://doi.org/10.1007/s00122-012-1988-2)) and a 10K-SNP diversity analysis ([Laucou et al. 2018](https://doi.org/10.1371/journal.pone.0192540)). Clone-level identity needs more markers: amplicon sequencing was tested to tell clones apart ([Urra et al. 2023](https://doi.org/10.1093/g3journal/jkad145)), and somatic variants from resequencing traced the dissemination of Tempranillo Tinto clones ([Tello et al. 2025](https://doi.org/10.1093/hr/uhaf237)).

Public resequencing panels are large but overlapping: over 1,000 samples from the USDA collection were genotyped for domestication history ([Myles et al. 2011](https://doi.org/10.1073/pnas.1009363108)), 472 *Vitis* accessions were resequenced ([Liang et al. 2019](https://doi.org/10.1038/s41467-019-09135-8)), 204 *V. vinifera* accessions in a European study ([Magris et al. 2021](https://doi.org/10.1038/s41467-021-27487-y)) and 3,525 accessions for the dual-domestication study ([Dong et al. 2023](https://doi.org/10.1126/science.add8655)). Other crops released harmonised panels with stable IDs, such as the 1,135 *Arabidopsis* genomes ([Alonso-Blanco et al. 2016](https://doi.org/10.1016/j.cell.2016.05.063)) and the 3,000 rice genomes ([3,000 rice genomes project 2014](https://doi.org/10.1186/2047-217x-3-7)). Robust relatedness estimators (KING) handle population structure ([Manichaikul et al. 2010](https://doi.org/10.1093/bioinformatics/btq559)), PLINK 2 scales to large call sets ([Chang et al. 2015](https://doi.org/10.1186/s13742-015-0047-8)), and Somalier checks sample identity directly from alignments ([Pedersen et al. 2020](https://doi.org/10.1186/s13073-020-00761-2)).

**Specific gap.** No cross-panel identity table for public grape resequencing was found that links run IDs to genetic identity groups, flags clones, duplicates and label conflicts with VIVC names, and gives coordinate conversion between 12X, v4 and PN_T2T [待确认].

## Question

How many public grape samples are genetic duplicates across panels, and how many labels conflict with genetic identity?

## Hypotheses, planned figures and criteria

No results are given here. Each row says what would count as support; the exact thresholds go into the preregistration.

| Figure or table | Hypothesis or purpose | Criterion |
|---|---|---|
| Fig 1. Kinship among panels | Many accessions appear in more than one panel. | KING kinship thresholds fixed in advance; duplicates listed. |
| Fig 2. Label conflicts | A minority of labels conflict with genetic identity. | Conflicts checked against VIVC names; reported as counts by study. |
| Fig 3. Coordinate conversion | Most SNPs lift uniquely from 12X and v4 to PN_T2T. | Share of uniquely lifted sites; failures listed by region. |

**Expected results and how they will be read**

- Fig 1: the number of genetic identity groups shared between panels sets the effective sample size for every downstream project; it is reported per panel pair.
- Fig 2: each label conflict is listed with its evidence; conflicts are flagged, never overwritten, and are not called errors without a VIVC record.
- Fig 3: the share of SNPs lifting uniquely to PN_T2T decides whether older call sets can be reused or must be re-called.
- The main product is the released identity table and chain files, which projects 10, 13, 15, 16, 19, 21, 23 and 24 use.

## Preregistration

Before any data are analysed, fill in [`docs/PREREGISTRATION.md`](../../../../templates/PREREGISTRATION.md) for this project: hypotheses, primary outcome, sample inclusion rules, thresholds, stop rules and what will be reported if a hypothesis fails. Commit it with a date. Criteria from any earlier attempt are reference only and are not carried over.

## Data

| Module | Dataset |
|---|---|
| [DS10](../../data/DS10-reseq-472-vitis/) | Resequencing of 472 Vitis accessions (and the 2017 domestication panel) |
| [DS11](../../data/DS11-reseq-3525-dong2023/) | Resequencing of 3,525 grapevine accessions (Dong et al. 2023) |
| [DS12](../../data/DS12-reseq-204-magris2021/) | Resequencing of 204 V. vinifera accessions (Magris et al. 2021) |
| [DS02](../../data/DS02-grapepan-v1/) | Grapepan v1.0: T2T haplotypes, graphs and a 466-accession resequencing panel |
| [DS03](../../data/DS03-vitis-super-pangenome-72/) | Vitis super-pangenome: 72 haplotype-resolved accessions |
| [DS01](../../data/DS01-pn40024-references/) | PN40024 references: PN_T2T (v5), PN40024.v4 and 12X |

**How each dataset is used**

| Module | Role in this project |
|---|---|
| DS10 | 472-accession panel and the 2017 domestication panel |
| DS11 | 3,525-accession panel (only after its run list can be exported) |
| DS12 | 204-accession European panel |
| DS02, DS03 | Pangenome resequencing panels and haplotype donors |
| DS01 | 12X, v4 and PN_T2T for chain files |

New public data: none needed. VIVC records are read from the public catalogue page by page [待确认: terms of reuse].

## Analysis steps

Shared modules, in order:

1. [AM01 · Download and verify](../../analyses/AM01-download-and-verify/)
2. [AM02 · Read QC and trimming](../../analyses/AM02-read-qc/)
3. [AM03 · Short-read mapping and small-variant calling](../../analyses/AM03-short-read-variants/)
4. [AM04 · Sample identity, clones and relatedness](../../analyses/AM04-sample-identity/)

Project-specific steps:

- Build one sample sheet per panel.
- Genotype a shared site set (AM03).
- Run KING and plink2 (AM04).
- Compare with VIVC names; build liftover chains (DS01).

**Stepwise work plan with tools**

| Step | Work | Tools (paper) | Output |
|---|---|---|---|
| 1 | One sample sheet per panel with run IDs, given names and source collection | SRA/ENA metadata | Sample sheets |
| 2 | Genotype a shared biallelic SNP set on PN_T2T (no full re-call needed) | bwa-mem2, bcftools (AM03) | Shared-site VCF |
| 3 | Identity and kinship with preregistered thresholds; cross-check with alignment-based identity | KING, PLINK 2, Somalier (AM04) | Pairwise table |
| 4 | Cluster into identity groups; flag clones, duplicates and first-degree pairs | igraph | Identity groups |
| 5 | Compare names with VIVC prime names; list conflicts with evidence | VIVC | Conflict table |
| 6 | Build and test chain files 12X to v4 to PN_T2T | minimap2, CrossMap or bcftools liftover | Chain files and lift rates |

## Paper design and split

| Paper | Working title | Type | Figures |
|---|---|---|---|
| I1 | A harmonised identity table for public grape resequencing | resource paper | Fig 1–3 |

Each paper: introduction from the gap above; one results section per figure; methods with tool versions from the modules; data availability listing every accession used and the derived tables.

## Risks and novelty check

- Risk: Download of the largest panel from NGDC may be slow [待确认].
- Risk: Name matching to VIVC is manual.
- Novelty: checked against the existing work above (Crossref-verified DOIs). Repeat the search before writing; anything marked [待确认] is not yet verified.

## Rough estimates

- Compute: medium to large (downloads) [draft]
- Effort: 1–3 months for one person [draft]
- Target: data or genetics journal [draft]

## Suggested journal level (suggestion only)

**Specialty journal (data or genetic resources).** Grape identity and parentage resources read here appeared in *Theoretical and Applied Genetics*, *BMC Plant Biology*, *PLOS ONE*, *G3* and *BIO Web of Conferences*; harmonised panels in other crops appeared in *GigaScience* and *Cell* when they were new sequencing. A cross-panel identity table without new sequencing fits a data or resource journal. This is a suggestion, not a decision; impact factors are not used.

## Continue on HPC

Run each step as its own job, in this order. Every job writes `.DONE` or `.FAILED` and a log; the next step starts only after `.DONE`. Template and rules: [`docs/HPC_JOBS.md`](../../../../templates/HPC_JOBS.md).

| Order | Step | Main tools | Resources (rough) |
|---|---|---|---|
| 1 | [AM01](../../analyses/AM01-download-and-verify/) Download and verify | ncbi-datasets-cli, sra-tools, ENA FTP / Aspera | 1–4 CPU, 4 GB, network; array over files |
| 2 | [AM02](../../analyses/AM02-read-qc/) Read QC and trimming | fastp, MultiQC, seqkit | 8 CPU, 16 GB, 1–2 h per run; array over runs |
| 3 | [AM03](../../analyses/AM03-short-read-variants/) Short-read mapping and small-variant calling | bwa-mem2, samtools, DeepVariant | 16 CPU, 64 GB, 6–24 h per sample (DeepVariant); joint step 32 CPU, 128 GB |
| 4 | [AM04](../../analyses/AM04-sample-identity/) Sample identity, clones and relatedness | plink2, KING, VIVC | 8 CPU, 32 GB, < 2 h |

Public inputs: [DS10](../../data/DS10-reseq-472-vitis/), [DS11](../../data/DS11-reseq-3525-dong2023/), [DS12](../../data/DS12-reseq-204-magris2021/), [DS02](../../data/DS02-grapepan-v1/), [DS03](../../data/DS03-vitis-super-pangenome-72/), [DS01](../../data/DS01-pn40024-references/).

## References

- Urra et al. 2023. Identification of grapevine clones via high-throughput amplicon sequencing: a proof-of-concept study. *G3: Genes, Genomes, Genetics*. [doi:10.1093/g3journal/jkad145](https://doi.org/10.1093/g3journal/jkad145)
- Tello et al. 2025. Genome resequencing and custom genotyping elucidates the origin and dissemination history of an emblematic grapevine cultivar, ‘Tempranillo Tinto’. *Horticulture Research*. [doi:10.1093/hr/uhaf237](https://doi.org/10.1093/hr/uhaf237)
- Magris et al. 2021. The genomes of 204 Vitis vinifera accessions reveal the origin of European wine grapes. *Nature Communications*. [doi:10.1038/s41467-021-27487-y](https://doi.org/10.1038/s41467-021-27487-y)
- Dong et al. 2023. Dual domestications and origin of traits in grapevine evolution. *Science*. [doi:10.1126/science.add8655](https://doi.org/10.1126/science.add8655)
- 3,000 rice genomes project 2014. The 3,000 rice genomes project. *Gigascience*. [doi:10.1186/2047-217x-3-7](https://doi.org/10.1186/2047-217x-3-7)
- Alonso-Blanco et al. 2016. 1,135 Genomes Reveal the Global Pattern of Polymorphism in Arabidopsis thaliana. *Cell*. [doi:10.1016/j.cell.2016.05.063](https://doi.org/10.1016/j.cell.2016.05.063)
- Cabezas et al. 2011. A 48 SNP set for grapevine cultivar identification. *BMC Plant Biology*. [doi:10.1186/1471-2229-11-153](https://doi.org/10.1186/1471-2229-11-153)
- Chang et al. 2015. Second-generation PLINK: rising to the challenge of larger and richer datasets. *Gigascience*. [doi:10.1186/s13742-015-0047-8](https://doi.org/10.1186/s13742-015-0047-8)
- Cipriani et al. 2010. The SSR-based molecular profile of 1005 grapevine (Vitis vinifera L.) accessions uncovers new synonymy and parentages, and reveals a large admixture amongst varieties of different geographic origin. *Theoretical and Applied Genetics*. [doi:10.1007/s00122-010-1411-9](https://doi.org/10.1007/s00122-010-1411-9)
- Lacombe et al. 2013. Large-scale parentage analysis in an extended set of grapevine cultivars (Vitis vinifera L.). *Theoretical and Applied Genetics*. [doi:10.1007/s00122-012-1988-2](https://doi.org/10.1007/s00122-012-1988-2)
- Laucou et al. 2011. High throughput analysis of grape genetic diversity as a tool for germplasm collection management. *Theoretical and Applied Genetics*. [doi:10.1007/s00122-010-1527-y](https://doi.org/10.1007/s00122-010-1527-y)
- Laucou et al. 2018. Extended diversity analysis of cultivated grapevine Vitis vinifera with 10K genome-wide SNPs. *PLOS ONE*. [doi:10.1371/journal.pone.0192540](https://doi.org/10.1371/journal.pone.0192540)
- Liang et al. 2019. Whole-genome resequencing of 472 Vitis accessions for grapevine diversity and demographic history analyses. *Nature Communications*. [doi:10.1038/s41467-019-09135-8](https://doi.org/10.1038/s41467-019-09135-8)
- Manichaikul et al. 2010. Robust relationship inference in genome-wide association studies. *Bioinformatics*. [doi:10.1093/bioinformatics/btq559](https://doi.org/10.1093/bioinformatics/btq559)
- Maul et al. 2015. VitisInternational Variety Catalogue (VIVC): A cultivar database referenced by genetic profiles and morphology. *BIO Web of Conferences*. [doi:10.1051/bioconf/20150501009](https://doi.org/10.1051/bioconf/20150501009)
- Myles et al. 2011. Genetic structure and domestication history of the grape. *Proceedings of the National Academy of Sciences*. [doi:10.1073/pnas.1009363108](https://doi.org/10.1073/pnas.1009363108)
- Pedersen et al. 2020. Somalier: rapid relatedness estimation for cancer and germline studies using efficient genome sketches. *Genome Medicine*. [doi:10.1186/s13073-020-00761-2](https://doi.org/10.1186/s13073-020-00761-2)
