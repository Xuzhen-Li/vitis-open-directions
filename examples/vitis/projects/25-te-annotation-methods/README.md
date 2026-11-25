# 25. Transposable-element annotation methods, library curation and automation

中文：转座元件注释方法、文库整理与自动化

Not scored (see docs/RANKING.md; projects 23 to 26 were added after the ranking) · Tier: Medium [draft] · Origin: continued: outline written earlier, restarted here from published sources · Status: draft, 2026-11-25 · Progress: [STATUS.md](STATUS.md)

## Gap

TE annotation methods are described tool by tool, and benchmarks compare a few tools at a time. A methods-centred survey that treats detection, manual curation, curation automation and the evidence used to judge annotation quality as one connected topic, with plant assemblies as the main thread and published grape annotations as case studies, was not found [待确认: repeat the search before writing].

**Existing work and background survey**

The Wicker system and its 80-80-80 family rule are the common classification frame ([Wicker et al. 2007](https://doi.org/10.1038/nrg2165)); it is a convention, not a biological boundary. Variation in TE annotation between projects can change biological conclusions on new assemblies ([Platt et al. 2016](https://doi.org/10.1093/gbe/evw009)).

Detection: Dfam holds TE families, sequence models and genome annotations for many species ([Storer et al. 2021](https://doi.org/10.1186/s13100-020-00230-y)); RepeatModeler2 automates de novo family discovery ([Flynn et al. 2020](https://doi.org/10.1073/pnas.1921046117)); LTR_retriever identifies LTR retrotransposons with high specificity and builds LTR libraries ([Ou and Jiang 2018](https://doi.org/10.1104/pp.17.01310)); TEsorter classifies LTR retrotransposons in plant genomes ([Zhang et al. 2022](https://doi.org/10.1093/hr/uhac017)); a benchmark of annotation methods led to the EDTA pipeline ([Ou et al. 2019](https://doi.org/10.1186/s13059-019-1905-y)); TE families can be identified from pangenome polymorphisms ([Sierra and Durbin 2024](https://doi.org/10.1186/s13100-024-00323-y)).

Curation: a practical guide sets out manual curation of TE consensus sequences ([Goubert et al. 2022](https://doi.org/10.1186/s13100-021-00259-7)); MCHelper automates curation of TE libraries across eukaryotes ([Orozco-Arias et al. 2024](https://doi.org/10.1101/gr.278821.123)); TEtrimmer automates and replaces key steps of manual curation ([Qian et al. 2025](https://doi.org/10.1038/s41467-025-63889-y)).

Grape case study: a retrotransposon insertion in VvmybA1 is associated with loss of skin pigmentation in white cultivars ([Kobayashi et al. 2004](https://doi.org/10.1126/science.1095011)); PN_T2T released a TE annotation with the assembly ([Shi et al. 2023](https://doi.org/10.1093/hr/uhad061)).

**How this project differs**

This is a methods survey article, not an analysis. It does not produce a new TE library or insertion catalogue; project 14 remains the public-data analysis of insertion polymorphisms.

## Question

How have TE detection, curation and automation methods developed, what evidence is used to judge whether an annotation is good, and what do published grape annotations show about current practice?

## Planned figures and tables

No results are given here. A survey article has no hypotheses in the test sense; each row says what the item must contain and how it is checked.

| Figure or table | Purpose | Criterion |
|---|---|---|
| Fig 1. Timeline of method families | Show generations of detection, curation and automation methods. | Only tools with a published paper that was opened; preprint-only tools in a separate note. |
| Table 1. Tools by task | Compare inputs, outputs, TE classes covered and evaluation used in each tool paper. | Quoted from the tool paper or official documentation; no performance claims beyond what the paper reports. |
| Table 2. Evaluation evidence | List benchmark designs and quality measures (for example family completeness, false positives, classification accuracy). | From published benchmarks only. |
| Table 3. Published grape TE annotations and libraries | Case study. | Only deposits whose accession was opened; DS01 Zenodo 7751391 and pangenome deposits [待确认: which include TE annotations]. |

## Preregistration

Before drafting, fill in [`docs/PREREGISTRATION.md`](../../../../templates/PREREGISTRATION.md) for this project as an outline lock: scope, inclusion rules for papers and tools, cut-off date for preprints, and the journal's limits. Commit it with a date. Plans from any earlier attempt are reference only and are not carried over.

## Data

| Module | Dataset |
|---|---|
| [DS01](../../data/DS01-pn40024-references/) | PN40024 references: PN_T2T (v5), PN40024.v4 and 12X |
| [DS02](../../data/DS02-grapepan-v1/) | Grapepan v1.0: T2T haplotypes, graphs and a 466-accession resequencing panel |
| [DS03](../../data/DS03-vitis-super-pangenome-72/) | Vitis super-pangenome: 72 haplotype-resolved accessions |

The TE annotation file of PN_T2T is in Zenodo 7751391 (DS01). The main input is the published literature. New public data: none needed.

## Analysis steps

**Stepwise work plan**

| Step | Work | Tools or sources | Output |
|---|---|---|---|
| 1 | Lock scope, inclusion rules and journal in the outline lock | PREREGISTRATION template | Locked outline |
| 2 | Systematic literature search; record every DOI opened | Crossref, OpenAlex, publisher pages | Source table |
| 3 | Extract tool features from tool papers and documentation | manual extraction | Table 1 |
| 4 | Extract benchmark designs and measures | manual extraction | Table 2 |
| 5 | List grape TE annotations and libraries with accessions | DS01, DS02, DS03 | Table 3 |
| 6 | Draft sections: detection, curation, automation, evaluation, long-read and pangenome annotation | text | Manuscript |

## Expected results and how they will be read

- The article gives a map of methods and the evidence behind them; it makes no new performance claims.
- Table 3 shows how grape annotations were made and deposited; gaps (for example missing libraries) are reported as observations, not as errors of the source projects.

## Paper design and split

| Paper | Working title | Type | Figures |
|---|---|---|---|
| M1 | Transposable-element annotation in plant genomes: detection, curation and automation | methods survey article | Fig 1, Tables 1–3 |

Each paper: introduction from the gap above; one section per method family; data availability listing every accession named in the case study.

## Risks and novelty check

- Risk: The field moves fast; a preprint cut-off date must be fixed.
- Risk: Overlap with project 14 and the vitis-te catalogue; the split in docs/DEFAULTS.md applies.
- Risk: Several recent survey articles on TE annotation may exist [待确认].
- Novelty: checked against the existing work above (Crossref-verified DOIs). Repeat the search before writing; anything marked [待确认] is not yet verified.

## Rough estimates

- Compute: none to small [draft]
- Effort: 2–3 months for one person [draft]
- Target: genome biology or mobile DNA journal [draft]

## Suggested journal level (suggestion only)

**Specialty journal (mobile DNA or plant genome biology).** Comparable methods guides and benchmarks read here appeared in *Mobile DNA*, *Genome Biology and Evolution* and *Genome Biology*; the classification frame appeared in *Nat Rev Genet*. A methods survey with a grape case study fits a specialty venue; a broad survey journal is possible only if the scope covers all eukaryotes [待确认]. This is a suggestion, not a decision; impact factors are not used.

## Continue on HPC

No HPC jobs are needed. Optional: run AM01 only to fetch and checksum the grape annotation files named in Table 3. Template and rules: [`docs/HPC_JOBS.md`](../../../../templates/HPC_JOBS.md).

| Order | Step | Main tools | Resources (rough) |
|---|---|---|---|
| 1 | [AM01](../../analyses/AM01-download-and-verify/) Download and verify (optional) | Zenodo API, ncbi-datasets-cli | 1–4 CPU, 4 GB, network |

Public inputs: [DS01](../../data/DS01-pn40024-references/), [DS02](../../data/DS02-grapepan-v1/), [DS03](../../data/DS03-vitis-super-pangenome-72/).

## References

- Flynn et al. 2020. RepeatModeler2 for automated genomic discovery of transposable element families. *Proceedings of the National Academy of Sciences*. [doi:10.1073/pnas.1921046117](https://doi.org/10.1073/pnas.1921046117)
- Goubert et al. 2022. A beginner’s guide to manual curation of transposable elements. *Mobile DNA*. [doi:10.1186/s13100-021-00259-7](https://doi.org/10.1186/s13100-021-00259-7)
- Kobayashi et al. 2004. Retrotransposon-Induced Mutations in Grape Skin Color. *Science*. [doi:10.1126/science.1095011](https://doi.org/10.1126/science.1095011)
- Orozco-Arias et al. 2024. MCHelper automatically curates transposable element libraries across eukaryotic species. *Genome Research*. [doi:10.1101/gr.278821.123](https://doi.org/10.1101/gr.278821.123)
- Ou et al. 2018. LTR_retriever: A Highly Accurate and Sensitive Program for Identification of Long Terminal Repeat Retrotransposons. *Plant Physiology*. [doi:10.1104/pp.17.01310](https://doi.org/10.1104/pp.17.01310)
- Ou et al. 2019. Benchmarking transposable element annotation methods for creation of a streamlined, comprehensive pipeline. *Genome Biology*. [doi:10.1186/s13059-019-1905-y](https://doi.org/10.1186/s13059-019-1905-y)
- Platt et al. 2016. Accurate Transposable Element Annotation Is Vital When Analyzing New Genome Assemblies. *Genome Biology and Evolution*. [doi:10.1093/gbe/evw009](https://doi.org/10.1093/gbe/evw009)
- Qian et al. 2025. TEtrimmer: a tool to automate the manual curation of transposable elements. *Nature Communications*. [doi:10.1038/s41467-025-63889-y](https://doi.org/10.1038/s41467-025-63889-y)
- Shi et al. 2023. The complete reference genome for grapevine (Vitis vinifera L.) genetics and breeding. *Horticulture Research*. [doi:10.1093/hr/uhad061](https://doi.org/10.1093/hr/uhad061)
- Sierra et al. 2024. Identification of transposable element families from pangenome polymorphisms. *Mobile DNA*. [doi:10.1186/s13100-024-00323-y](https://doi.org/10.1186/s13100-024-00323-y)
- Storer et al. 2021. The Dfam community resource of transposable element families, sequence models, and genome annotations. *Mobile DNA*. [doi:10.1186/s13100-020-00230-y](https://doi.org/10.1186/s13100-020-00230-y)
- Wicker et al. 2007. A unified classification system for eukaryotic transposable elements. *Nat Rev Genet*. [doi:10.1038/nrg2165](https://doi.org/10.1038/nrg2165)
- Zhang et al. 2022. TEsorter: An accurate and fast method to classify LTR-retrotransposons in plant genomes. *Horticulture Research*. [doi:10.1093/hr/uhac017](https://doi.org/10.1093/hr/uhac017)
