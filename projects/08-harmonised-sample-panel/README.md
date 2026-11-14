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

## Question

How many public grape samples are genetic duplicates across panels, and how many labels conflict with genetic identity?

## Hypotheses, planned figures and criteria

No results are given here. Each row says what would count as support; the exact thresholds go into the preregistration.

| Figure or table | Hypothesis or purpose | Criterion |
|---|---|---|
| Fig 1. Kinship among panels | Many accessions appear in more than one panel. | KING kinship thresholds fixed in advance; duplicates listed. |
| Fig 2. Label conflicts | A minority of labels conflict with genetic identity. | Conflicts checked against VIVC names; reported as counts by study. |
| Fig 3. Coordinate conversion | Most SNPs lift uniquely from 12X and v4 to PN_T2T. | Share of uniquely lifted sites; failures listed by region. |

## Preregistration

Before any data are analysed, fill in [`docs/PREREGISTRATION.md`](../../docs/PREREGISTRATION.md) for this project: hypotheses, primary outcome, sample inclusion rules, thresholds, stop rules and what will be reported if a hypothesis fails. Commit it with a date. Criteria from any earlier attempt are reference only and are not carried over.

## Data

| Module | Dataset |
|---|---|
| [DS10](../../data/DS10-reseq-472-vitis/) | Resequencing of 472 Vitis accessions (and the 2017 domestication panel) |
| [DS11](../../data/DS11-reseq-3525-dong2023/) | Resequencing of 3,525 grapevine accessions (Dong et al. 2023) |
| [DS12](../../data/DS12-reseq-204-magris2021/) | Resequencing of 204 V. vinifera accessions (Magris et al. 2021) |
| [DS02](../../data/DS02-grapepan-v1/) | Grapepan v1.0: T2T haplotypes, graphs and a 466-accession resequencing panel |
| [DS03](../../data/DS03-vitis-super-pangenome-72/) | Vitis super-pangenome: 72 haplotype-resolved accessions |
| [DS01](../../data/DS01-pn40024-references/) | PN40024 references: PN_T2T (v5), PN40024.v4 and 12X |

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

## Continue on HPC

Run each step as its own job, in this order. Every job writes `.DONE` or `.FAILED` and a log; the next step starts only after `.DONE`. Template and rules: [`docs/HPC_JOBS.md`](../../docs/HPC_JOBS.md).

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
