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

**Background survey (literature read for this plan)**

Grapevine hosts many viruses, and most management still relies on clean planting material ([Fuchs 2020](https://doi.org/10.1007/s42161-020-00579-2)). High-throughput sequencing changed virus detection in grape early: total RNA from one Syrah vine with decline symptoms revealed a mixed infection with seven RNA genomes, including a new virus ([Al Rwahnih et al. 2009](https://doi.org/10.1016/j.virol.2009.02.028)). HTS is now used for routine plant virus diagnostics, with known limits on standards, controls and reporting ([Maree et al. 2018](https://doi.org/10.3389/fpls.2018.01082)). Grape-specific studies mined single transcriptome datasets, for example Tannat ([Jo et al. 2015](https://doi.org/10.1038/srep15841)), and compared library preparations for virome profiling ([Sidharthan et al. 2020](https://doi.org/10.3389/fmicb.2020.01232)).

Mining public archives at scale is now practical. Serratus aligned petabases of public reads to find RNA viruses ([Edgar et al. 2022](https://doi.org/10.1038/s41586-021-04332-2)); RdRp profile HMMs found many new RNA viruses in public transcriptomes ([Olendraite et al. 2023](https://doi.org/10.1093/molbev/msad060)); plant transcriptome mining extended known RNA viruses into basal plant lineages ([Mifsud et al. 2022](https://doi.org/10.1128/jvi.00260-22)). The RdRp palmprint gives a standard barcode for classifying new riboviruses ([Babaian and Edgar 2022](https://doi.org/10.7717/peerj.14055)), and CheckV estimates completeness of assembled viral genomes ([Nayfach et al. 2021](https://doi.org/10.1038/s41587-020-00774-7)).

**Specific gap.** These archive-scale screens are cross-host and do not report grape-specific detection by library type. No grape-focused screen of all public *Vitis* RNA-seq (and unmapped WGS reads) with library type, tissue, country and controls for index hopping was found [待确认].

## Question

Which viruses are detectable in public grape sequencing data, and how much does detection depend on library preparation?

## Hypotheses, planned figures and criteria

No results are given here. Each row says what would count as support; the exact thresholds go into the preregistration.

| Figure or table | Hypothesis or purpose | Criterion |
|---|---|---|
| Fig 1. Detection by library type | For viruses without a poly(A) tail, detection is higher in total-RNA libraries than in poly(A)-selected libraries; for polyadenylated viruses, library type matters less. | Mixed logistic model with library type × virus poly(A) status and read depth as fixed effects and study as a random effect; results stratified by virus family. |
| Fig 2. Known viruses by country, tissue and year | Descriptive. | Counts with study as a random effect; no prevalence claims beyond the sampled studies. |
| Table 1. Candidate new viruses | Candidates only. | RdRp-containing contigs with CheckV completeness; called candidates until confirmed independently. |

**Expected results and how they will be read**

- Fig 1: if detection of non-polyadenylated viruses is higher in total-RNA libraries, the paper gives a practical rule for which public data can be used for which virus families; if not, library type is not a limiting factor.
- Fig 2 is descriptive; it shows where public data are dense or thin and is never read as prevalence.
- Table 1 lists candidate new viruses with palmprint and CheckV completeness; every row stays a candidate until confirmed independently.

## Preregistration

Before any data are analysed, fill in [`docs/PREREGISTRATION.md`](../../../../templates/PREREGISTRATION.md) for this project: hypotheses, primary outcome, sample inclusion rules, thresholds, stop rules and what will be reported if a hypothesis fails. Commit it with a date. Criteria from any earlier attempt are reference only and are not carried over.

## Data

| Module | Dataset |
|---|---|
| [DS15](../../data/DS15-rnaseq-public-vitis/) | Public Vitis RNA-seq and the expression atlas |
| [DS10](../../data/DS10-reseq-472-vitis/) | Resequencing of 472 Vitis accessions (and the 2017 domestication panel) |
| [DS12](../../data/DS12-reseq-204-magris2021/) | Resequencing of 204 V. vinifera accessions (Magris et al. 2021) |
| [DS01](../../data/DS01-pn40024-references/) | PN40024 references: PN_T2T (v5), PN40024.v4 and 12X |

**How each dataset is used**

| Module | Role in this project |
|---|---|
| DS15 | All public *Vitis* RNA-seq runs with library, tissue and country metadata |
| DS10, DS12 | Unmapped reads from WGS panels (DNA viruses and integrated sequences) |
| DS01 | PN_T2T for host-read removal |

New public data: none needed. Reference virus sequences come from public virus databases [待确认: release used].

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

**Stepwise work plan with tools**

| Step | Work | Tools (paper) | Output |
|---|---|---|---|
| 1 | Build the run table with library type, strategy, tissue, country, year and study | SRA metadata, DS15 | Run sheet |
| 2 | Download, check and trim | AM01, AM02 | Clean reads |
| 3 | Remove host reads by mapping to PN_T2T | minimap2 or STAR | Unmapped reads |
| 4 | Screen known viruses by read classification and protein search | Kraken2, DIAMOND (AM16) | Known-virus hits per run |
| 5 | Assemble positive runs; find RdRp and palmprints | MEGAHIT, rnaviralSPAdes, palmscan | Contigs |
| 6 | Completeness and contamination of viral contigs | CheckV | Candidate table |
| 7 | Index-hopping and cross-study controls; mixed logistic model for Fig 1 | R lme4 | Fig 1 statistics |

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

## Suggested journal level (suggestion only)

**Specialty journal (plant virology), mid-field if many candidates are confirmed.** Grape HTS virus papers read here appeared in *Virology*, *Scientific Reports*, *Frontiers in Microbiology* and *Journal of Plant Pathology*; cross-host archive mining appeared in *Journal of Virology*, *Molecular Biology and Evolution* and *Nature*. A grape-only screen with a library-type analysis matches the specialty level. This is a suggestion, not a decision; impact factors are not used.

## Continue on HPC

Run each step as its own job, in this order. Every job writes `.DONE` or `.FAILED` and a log; the next step starts only after `.DONE`. Template and rules: [`docs/HPC_JOBS.md`](../../../../templates/HPC_JOBS.md).

| Order | Step | Main tools | Resources (rough) |
|---|---|---|---|
| 1 | [AM01](../../analyses/AM01-download-and-verify/) Download and verify | ncbi-datasets-cli, sra-tools, ENA FTP / Aspera | 1–4 CPU, 4 GB, network; array over files |
| 2 | [AM02](../../analyses/AM02-read-qc/) Read QC and trimming | fastp, MultiQC, seqkit | 8 CPU, 16 GB, 1–2 h per run; array over runs |
| 3 | [AM16](../../analyses/AM16-virus-and-eve-search/) Virus discovery in RNA-seq and endogenous viral elements in assemblies | DIAMOND, MEGAHIT, SPAdes (rnaviralSPAdes) | 16 CPU, 64 GB per run for assembly |

Public inputs: [DS15](../../data/DS15-rnaseq-public-vitis/), [DS10](../../data/DS10-reseq-472-vitis/), [DS12](../../data/DS12-reseq-204-magris2021/), [DS01](../../data/DS01-pn40024-references/).

## References

- Jo et al. 2015. In silico approach to reveal viral populations in grapevine cultivar Tannat using transcriptome data. *Scientific Reports*. [doi:10.1038/srep15841](https://doi.org/10.1038/srep15841)
- Sidharthan et al. 2020. Robust Virome Profiling and Whole Genome Reconstruction of Viruses and Viroids Enabled by Use of Available mRNA and sRNA-Seq Datasets in Grapevine (Vitis vinifera L.). *Frontiers in Microbiology*. [doi:10.3389/fmicb.2020.01232](https://doi.org/10.3389/fmicb.2020.01232)
- Al Rwahnih et al. 2009. Deep sequencing analysis of RNAs from a grapevine showing Syrah decline symptoms reveals a multiple virus infection that includes a novel virus. *Virology*. [doi:10.1016/j.virol.2009.02.028](https://doi.org/10.1016/j.virol.2009.02.028)
- Babaian et al. 2022. Ribovirus classification by a polymerase barcode sequence. *PeerJ*. [doi:10.7717/peerj.14055](https://doi.org/10.7717/peerj.14055)
- Edgar et al. 2022. Petabase-scale sequence alignment catalyses viral discovery. *Nature*. [doi:10.1038/s41586-021-04332-2](https://doi.org/10.1038/s41586-021-04332-2)
- Fuchs 2020. Grapevine viruses: a multitude of diverse species with simple but overall poorly adopted management solutions in the vineyard. *Journal of Plant Pathology*. [doi:10.1007/s42161-020-00579-2](https://doi.org/10.1007/s42161-020-00579-2)
- Maree et al. 2018. Application of HTS for Routine Plant Virus Diagnostics: State of the Art and Challenges. *Frontiers in Plant Science*. [doi:10.3389/fpls.2018.01082](https://doi.org/10.3389/fpls.2018.01082)
- Mifsud et al. 2022. Transcriptome Mining Expands Knowledge of RNA Viruses across the Plant Kingdom. *Journal of Virology*. [doi:10.1128/jvi.00260-22](https://doi.org/10.1128/jvi.00260-22)
- Nayfach et al. 2021. CheckV assesses the quality and completeness of metagenome-assembled viral genomes. *Nature Biotechnology*. [doi:10.1038/s41587-020-00774-7](https://doi.org/10.1038/s41587-020-00774-7)
- Olendraite et al. 2023. Identification of RNA Virus–Derived RdRp Sequences in Publicly Available Transcriptomic Data Sets. *Molecular Biology and Evolution*. [doi:10.1093/molbev/msad060](https://doi.org/10.1093/molbev/msad060)
