# 04. Virus discovery across public grape RNA-seq and unmapped reads

中文：在全部公开葡萄测序数据中找病毒

Rank 4 of 22 (score F 3 + N 2 + E 2 = 7; see docs/RANKING.md) · Tier: Medium (E = 2, effort range ending after 6 weeks and by 4 months) · Origin: new · Status: draft v0.3.2, 2026-11-14

## Gap

Single datasets have been mined for viruses. A systematic screen of all public *Vitis* RNA-seq (and unmapped WGS reads) with library type, tissue and country recorded was not found.

**Existing work**

- [Jo et al. 2015](https://doi.org/10.1038/srep15841): viral populations reconstructed from Tannat transcriptome data.
- [Sidharthan et al. 2020](https://doi.org/10.3389/fmicb.2020.01232): virus discovery in grape from high-throughput sequencing.

**How this project differs**

Covers every public run, records detection limits by library type, and separates known viruses from candidate new ones.

## Question

Which viruses are detectable in public grape sequencing data, and how much does detection depend on library preparation?

## Hypotheses, planned figures and criteria

No results are given here. Each row says what would count as support; the exact thresholds go into the preregistration.

| Figure or table | Hypothesis or purpose | Criterion |
|---|---|---|
| Fig 1. Detection by library type | For viruses without a poly(A) tail, detection is higher in total-RNA libraries than in poly(A)-selected libraries; for polyadenylated viruses, library type matters less. | Mixed logistic model with library type × virus poly(A) status and read depth as fixed effects and study as a random effect; results stratified by virus family. |
| Fig 2. Known viruses by country, tissue and year | Descriptive. | Counts with study as a random effect; no prevalence claims beyond the sampled studies. |
| Table 1. Candidate new viruses | Candidates only. | RdRp-containing contigs with CheckV completeness; called candidates until confirmed independently. |

## Preregistration

Before any data are analysed, fill in [`docs/PREREGISTRATION.md`](../../docs/PREREGISTRATION.md) for this project: hypotheses, primary outcome, sample inclusion rules, thresholds, stop rules and what will be reported if a hypothesis fails. Commit it with a date. Criteria from any earlier attempt are reference only and are not carried over.

## Data

| Module | Dataset |
|---|---|
| [DS15](../../data/DS15-rnaseq-public-vitis/) | Public Vitis RNA-seq and the expression atlas |
| [DS10](../../data/DS10-reseq-472-vitis/) | Resequencing of 472 Vitis accessions (and the 2017 domestication panel) |
| [DS12](../../data/DS12-reseq-204-magris2021/) | Resequencing of 204 V. vinifera accessions (Magris et al. 2021) |
| [DS01](../../data/DS01-pn40024-references/) | PN40024 references: PN_T2T (v5), PN40024.v4 and 12X |

## Analysis steps

Shared modules, in order:

1. [AM01 · Download and verify](../../analyses/AM01-download-and-verify/)
2. [AM02 · Read QC and trimming](../../analyses/AM02-read-qc/)
3. [AM16 · Virus discovery in RNA-seq and endogenous viral elements in assemblies](../../analyses/AM16-virus-and-eve-search/)

Project-specific steps:

- Build the run list from DS15 (and unmapped reads from DS10/DS12 WGS).
- Map to PN_T2T; keep unmapped reads.
- Screen with Kraken2 and DIAMOND against viral proteins; assemble positives (MEGAHIT, rnaviralSPAdes); assess with CheckV.
- Add blank-library and cross-study controls for index hopping.

## Paper design and split

| Paper | Working title | Type | Figures |
|---|---|---|---|
| D1 | Viruses in public grape sequencing data | resource paper | Fig 1–2, Table 1 |

Each paper: introduction from the gap above; one results section per figure; methods with tool versions from the modules; data availability listing every accession used and the derived tables.

## Risks and novelty check

- Risk: Index hopping and contamination create false positives.
- Risk: Metadata are incomplete for many runs.
- Novelty: checked against the existing work above (Crossref-verified DOIs). Repeat the search before writing; anything marked [待确认] is not yet verified.

## Rough estimates

- Compute: medium [draft]
- Effort: 1–2 months for one person [draft]
- Target: virology journal [draft]

## Continue on HPC

Run each step as its own job, in this order. Every job writes `.DONE` or `.FAILED` and a log; the next step starts only after `.DONE`. Template and rules: [`docs/HPC_JOBS.md`](../../docs/HPC_JOBS.md).

| Order | Step | Main tools | Resources (rough) |
|---|---|---|---|
| 1 | [AM01](../../analyses/AM01-download-and-verify/) Download and verify | ncbi-datasets-cli, sra-tools, ENA FTP / Aspera | 1–4 CPU, 4 GB, network; array over files |
| 2 | [AM02](../../analyses/AM02-read-qc/) Read QC and trimming | fastp, MultiQC, seqkit | 8 CPU, 16 GB, 1–2 h per run; array over runs |
| 3 | [AM16](../../analyses/AM16-virus-and-eve-search/) Virus discovery in RNA-seq and endogenous viral elements in assemblies | DIAMOND, MEGAHIT, SPAdes (rnaviralSPAdes) | 16 CPU, 64 GB per run for assembly |

Public inputs: [DS15](../../data/DS15-rnaseq-public-vitis/), [DS10](../../data/DS10-reseq-472-vitis/), [DS12](../../data/DS12-reseq-204-magris2021/), [DS01](../../data/DS01-pn40024-references/).

## References

- Jo et al. 2015. In silico approach to reveal viral populations in grapevine cultivar Tannat using transcriptome data. *Scientific Reports*. [doi:10.1038/srep15841](https://doi.org/10.1038/srep15841)
- Sidharthan et al. 2020. Robust Virome Profiling and Whole Genome Reconstruction of Viruses and Viroids Enabled by Use of Available mRNA and sRNA-Seq Datasets in Grapevine (Vitis vinifera L.). *Frontiers in Microbiology*. [doi:10.3389/fmicb.2020.01232](https://doi.org/10.3389/fmicb.2020.01232)
