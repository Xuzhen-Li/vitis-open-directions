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

## Risks and how to handle them

Added 2026-11-26. Each row names a risk, the evidence behind it, and a concrete check or fallback. Sources cited here were read for this section and their DOIs were checked on Crossref; preprints are marked.

| Area | Risk | Check or mitigation |
|---|---|---|
| Data access and licence | The broad RNA-seq set (DS15) is an open ENA query, not a closed list ([data/DOWNLOADS.md](../../data/DOWNLOADS.md)). INSDC data are free and open ([INSDC 2024](https://doi.org/10.1093/nar/gkae1058)). | Freeze the run list with the query date; keep run, BioSample and study IDs with every detection. |
| False positives | Contamination is a named hurdle for sequencing-based virus detection, shown in an interlaboratory validation that included grapevine ([Abrahamian et al. 2025](https://doi.org/10.1094/phytofr-03-25-0025-r)); guidelines ask for controls at each step ([Massart et al. 2022](https://doi.org/10.24072/pcjournal.181)). | Require a minimum read count and genome breadth; flag any virus seen at low counts in many libraries of one sequencing run (index hopping); use the sensitivity and specificity criteria measured for grapevine ([Stevens et al. 2024](https://doi.org/10.3390/v16121957)). |
| Host attribution | Viruses in grape libraries need not infect grape: a re-analysis of metatranscriptomes from downy mildew leaf lesions completed genomes of splipalmiviruses, orfanplasmoviruses and new ambiviruses and found a viroid-like RNA, all reported as lesion-associated ([Daghino et al. 2026](https://doi.org/10.1016/j.virusres.2026.199780)). | Classify each hit by the known host range of its family; report non-plant families as associated, not as grape viruses. |
| Library preparation | Detection depends on nucleic acid type and library strategy ([Kutnjak et al. 2021](https://doi.org/10.3390/microorganisms9040841)). | Code library type (poly-A, total RNA, small RNA, DNA) for every run; compare detection rates within the same tissue and study where possible. |
| Sample size and power | Metadata are incomplete, so the library-type comparison may have few runs per class. | Fix a minimum number of runs per class before testing; otherwise report the comparison descriptively. |
| Clones, synonyms and pedigree | The same vine or clone can appear in several studies, so infections are not independent observations. | Collapse runs by BioSample and genotype before prevalence estimates. |
| Computing cost | Thousands of runs make download and host-read removal the main cost. | Stream runs, keep only unmapped reads, and time 50 runs first. |
| Alternative methods and sensitivity | Read-mapping and assembly-based detection find different things. | Run both on a random subset and report agreement. |

**Recent and competing work (search of 2024 to 2026 literature on 2026-11-26)**

- Large re-analyses of public plant data are now common: 2,789 public orchid RNA-seq sets gave 163 viruses ([Pérez et al. 2026](https://doi.org/10.1128/jvi.00624-26)), and mining of plant SRA libraries found 22 putative new closterovirids, including ampeloviruses ([Sidharthan 2026](https://doi.org/10.1007/s00705-026-06537-0)). Some grape runs have likely been searched already for some families.
- Before calling any virus new, compare it with the latest GenBank release and with the sequences from these papers.

**What would end the idea, and the fallback.** If almost every confident hit is a known grape virus or a contaminant pattern, discovery adds little. The fallback is a data note that maps virus presence in public grape data, as a warning for people who reuse those data for expression studies.

**Journal-level realism.** Archive-mining papers appear in *Journal of Virology*, *Archives of Virology* and *Viruses*. A grape-only screen fits that specialty level; mid-field only if several new viruses are confirmed with assembled genomes.

## Reference study in another species

Added 2026-11-26. Published studies that already did this kind of work in another species, to plan the grape version against. Every DOI was checked on Crossref. Figures are described, not copied; a figure redrawn for a grape paper would be marked "Redrawn after" its source. The last bullet for each study lists what a grape results section would need; it is a planning suggestion, not a finding of that study.

### Edgar et al. 2022

- **Paper:** [Edgar et al. 2022](https://doi.org/10.1038/s41586-021-04332-2), *Nature*.
- **Species:** All of the Sequence Read Archive (animals, plants, fungi and environmental samples).
- **What was done:** The cloud alignment platform Serratus searched 5.7 million SRA runs for RNA-dependent RNA polymerase (RdRP) sequences, found new RNA viruses on the order of one hundred thousand, and released a public database.
- **Figures:** Fig. 1 the searched data (bases by sample type, run release dates, geography of RdRP-positive samples); Fig. 2 RdRP in the SRA (palmprints and species-like units); Fig. 3 expansion of Coronaviridae; Fig. 4 expansion of deltaviruses and large phages; Extended Data Fig. 1 platform architecture and Extended Data Fig. 2 palmprint contig analysis (other Extended Data figures were not listed).
- **What a grape results section would need:** a list of searched samples with metadata (library type, tissue, country); virus hit counts and new species-like units; phylogenetic placement; a discussion of host attribution (contamination and non-infecting sources).

### Gilbert et al. 2019

- **Paper:** [Gilbert et al. 2019](https://doi.org/10.1371/journal.pone.0219207), *PLOS ONE*.
- **Note:** Method reference only: the journal is not first-quartile.
- **Species:** Fungi (public transcriptomes).
- **What was done:** Fungal public transcriptomes in the SRA were screened systematically with an RdRP-based workflow, and new mycovirus genomes were found and annotated.
- **Figures:** Fig. 1 Sankey diagram of fungal hosts and virus status; Fig. 2 dsRNA virus RdRP tree; Fig. 3 a new non-segmented RNA virus compared with Amalgaviridae and Partitiviridae; Fig. 4 an alternavirus; Fig. 5 two proposed partitivirus genera; Fig. 6 trees of three (+)ssRNA families; Fig. 7 tobamo-like viruses; Fig. 8 four new (+)ssRNA viruses; Fig. 9 a yadokarivirus genome; Fig. 10 the discovery workflow.
- **What a grape results section would need:** a screening flow chart and a sample and host summary; a tree and genome structure per virus family; the basis for naming and classifying new viruses.

### Jiang et al. 2019

- **Paper:** [Jiang et al. 2019](https://doi.org/10.1186/s12985-019-1257-y), *Virology Journal* (PMC6902351). Licence CC BY 4.0: figures may be reused with credit; none are copied here.
- **Species:** alfalfa (*Medicago sativa*), with *M. truncatula* datasets.
- **What was done:** public *Medicago* transcriptomes from the Sequence Read Archive (655 datasets in Fig. 1) were mapped to the host references; unmapped reads were aligned to viral genomes and assembled with SPAdes; some assemblies were confirmed by RACE and RT-PCR; 23 viruses were found, several not reported in alfalfa before, with coding-complete genomes for two cnidium vein yellowing virus strains, lychnis mottle virus and Cactus virus X.
- **Figures:** Fig. 1 virus presence across the datasets; Fig. 2 read coverage of a new amalgavirus; Fig. 3 RACE products; Fig. 4 genome organisation; Fig. 5 pairwise identity of RdRp sequences; Fig. 6 phylogeny; Fig. 7 to 10 genome organisation, identity and phylogenies of the other viruses.
- **What its results section needed:** a dataset-by-virus presence matrix, genome completeness, an independent confirmation, and phylogenetic placement.
- **Grape version:** the same matrix and phylogenies for grape datasets. Laboratory confirmation is outside this project, so replace Fig. 3 with in-silico checks: detection in independent BioProjects, even read coverage along the genome, absence from negative-control libraries, and host attribution as in the risk table above.

### Q1-level bar

Target: a first-quartile (Q1) journal in plant science, genetics or evolution. Quartile lists change each year, so the journal is chosen from the current list at submission [to confirm]. To compete at that level, the grape paper needs: complete or near-complete genomes for new viruses, evidence that each hit comes from a plant sample rather than contamination, and one ecological or agronomic pattern (tissue, region, cultivar or year) across a large set of public samples.

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
- INSDC 2024. The international nucleotide sequence database collaboration (INSDC): enhancing global participation. *Nucleic Acids Research*. [doi:10.1093/nar/gkae1058](https://doi.org/10.1093/nar/gkae1058)
- Abrahamian et al. 2025. Interlaboratory Validation of High-Throughput Sequencing for the Detection of Viruses and Viroids in Apple, Grapevine, and Stone Fruits. *PhytoFrontiers™*. [doi:10.1094/phytofr-03-25-0025-r](https://doi.org/10.1094/phytofr-03-25-0025-r)
- Massart et al. 2022. Guidelines for the reliable use of high throughput sequencing technologies to detect plant pathogens and pests. *Peer Community Journal*. [doi:10.24072/pcjournal.181](https://doi.org/10.24072/pcjournal.181)
- Stevens et al. 2024. High-Throughput Sequencing for the Detection of Viruses in Grapevine: Performance Analysis and Best Practices. *Viruses*. [doi:10.3390/v16121957](https://doi.org/10.3390/v16121957)
- Daghino et al. 2026. Expanded virome analysis of metatranscriptomes from grapevine downy mildew lesions reveals novel viral segments, novel viruses and viroid-like RNAs. *Virus Research*. [doi:10.1016/j.virusres.2026.199780](https://doi.org/10.1016/j.virusres.2026.199780)
- Kutnjak et al. 2021. A Primer on the Analysis of High-Throughput Sequencing Data for Detection of Plant Viruses. *Microorganisms*. [doi:10.3390/microorganisms9040841](https://doi.org/10.3390/microorganisms9040841)
- Pérez et al. 2026. Expanding the Orchidaceae virome through analysis of public-domain sequencing data. *Journal of Virology*. [doi:10.1128/jvi.00624-26](https://doi.org/10.1128/jvi.00624-26)
- Sidharthan 2026. Plant transcriptome data mining identified twenty-two putative novel taxa in the family Closteroviridae. *Archives of Virology*. [doi:10.1007/s00705-026-06537-0](https://doi.org/10.1007/s00705-026-06537-0)
- Gilbert et al. 2019. Hiding in plain sight: New virus genomes discovered via a systematic analysis of fungal public transcriptomes. *PLOS ONE*. [doi:10.1371/journal.pone.0219207](https://doi.org/10.1371/journal.pone.0219207)
- Jiang et al. 2019. Identification of emerging viral genomes in transcriptomic datasets of alfalfa (Medicago sativa L.). *Virology Journal*. [doi:10.1186/s12985-019-1257-y](https://doi.org/10.1186/s12985-019-1257-y)
