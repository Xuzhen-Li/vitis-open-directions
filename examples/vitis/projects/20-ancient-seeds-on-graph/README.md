# 20. Archaeological grape seeds: graph mapping and low-coverage imputation

中文：古葡萄种子：图参照比对与低覆盖填补

Rank 20 of 22 (score F 2 + N 2 + E 2 = 6; see docs/RANKING.md) · Tier: Medium (E = 2, effort range ending after 6 weeks and by 4 months) · Origin: new · Status: draft v0.3.2, 2026-11-14

## Gap

Archaeological grape seeds were analysed on linear references. Graph-based mapping, which reduces reference bias, and imputation from a modern panel were not found for grape.

**Existing work**

- [Ramos-Madrigal et al. 2019](https://doi.org/10.1038/s41477-019-0437-5): archaeological seeds and French grape diversity.
- [Cohen et al. 2023](https://doi.org/10.1073/pnas.2213563120): ancient DNA of a Negev Highlands grape.
- [Noraz et al. 2026](https://doi.org/10.1038/s41467-026-70166-z): 4000 years of grape diversity and clonal propagation in France.
- [Inanli et al. 2026](https://doi.org/10.1016/j.jas.2026.106605): seeds from Cetamura del Chianti.

**How this project differs**

Tests reference bias and imputation accuracy on downsampled modern data before applying them to seeds.

**Background survey (literature read for this plan)**

Archaeological grape seeds preserve DNA, but at low and variable endogenous content ([Wales et al. 2016](https://doi.org/10.1016/j.jas.2016.05.014)). Palaeogenomes from French sites linked ancient seeds to modern cultivars and showed long clonal histories ([Ramos-Madrigal et al. 2019](https://doi.org/10.1038/s41477-019-0437-5)); a Negev Highlands seed revealed a Late Antiquity wine lineage ([Cohen et al. 2023](https://doi.org/10.1073/pnas.2213563120)); 49 pips spanning about 4,000 years in France showed local wild grapes in the Bronze Age, early domesticated grapes by about 625-500 BCE and vegetative propagation ([Noraz et al. 2026](https://doi.org/10.1038/s41467-026-70166-z)); multiproxy evidence including seeds documented centuries of cultivation at Cetamura del Chianti ([Inanli et al. 2026](https://doi.org/10.1016/j.jas.2026.106605)).

Ancient reads are short and damaged, which increases reference bias; mapping to a variation graph reduced this bias and improved indel calls in human ancient DNA ([Martiniano et al. 2020](https://doi.org/10.1186/s13059-020-02160-7)). GLIMPSE2 imputes low-coverage genomes from large reference panels ([Rubinacci et al. 2023](https://doi.org/10.1038/s41588-023-01438-3)), and nf-core/eager standardises ancient-genome processing ([Fellows Yates et al. 2021](https://doi.org/10.7717/peerj.10947)). A grape graph and large modern panels now exist ([Liu et al. 2024](https://doi.org/10.1038/s41588-024-01967-5)).

**Specific gap.** Grape seed genomes were analysed on linear references; graph mapping and imputation from a modern panel have not been tested for grape, so it is unknown how much reference bias and missing data affect seed-to-cultivar matches [待确认].

## Question

Does graph mapping reduce reference bias for ancient grape seeds, and how accurate is imputation at their depths?

## Hypotheses, planned figures and criteria

No results are given here. Each row says what would count as support; the exact thresholds go into the preregistration.

| Figure or table | Hypothesis or purpose | Criterion |
|---|---|---|
| Fig 1. Reference bias, linear vs graph | Graph mapping reduces allele-balance bias. | Allele balance at known heterozygous sites. |
| Fig 2. Imputation accuracy on downsampled modern samples | Accuracy is acceptable above a depth threshold. | r² by allele-frequency bin; threshold fixed in advance. |
| Fig 3. Matches of seeds to modern cultivars | Some assignments change after graph mapping and imputation. | Changes reported with their support. |

**Expected results and how they will be read**

- Fig 1: lower allele-balance bias on the graph, measured on simulated damage and on real seeds, would justify graph mapping for grape ancient DNA.
- Fig 2 gives the depth above which imputation reaches the preregistered accuracy; seeds below it are analysed without imputation.
- Fig 3: changed assignments after graph mapping and imputation are listed; stable assignments strengthen the published conclusions; neither outcome is read as a new historical claim without support from the source papers.

## Preregistration

Before any data are analysed, fill in [`docs/PREREGISTRATION.md`](../../../../templates/PREREGISTRATION.md) for this project: hypotheses, primary outcome, sample inclusion rules, thresholds, stop rules and what will be reported if a hypothesis fails. Commit it with a date. Criteria from any earlier attempt are reference only and are not carried over.

## Data

| Module | Dataset |
|---|---|
| [DS14](../../data/DS14-ancient-grape-seeds/) | Archaeological grape seed sequencing |
| [DS02](../../data/DS02-grapepan-v1/) | Grapepan v1.0: T2T haplotypes, graphs and a 466-accession resequencing panel |
| [DS10](../../data/DS10-reseq-472-vitis/) | Resequencing of 472 Vitis accessions (and the 2017 domestication panel) |
| [DS12](../../data/DS12-reseq-204-magris2021/) | Resequencing of 204 V. vinifera accessions (Magris et al. 2021) |

**How each dataset is used**

| Module | Role in this project |
|---|---|
| DS14 | Archaeological seed reads |
| DS02 | Graph reference and haplotypes |
| DS10, DS12 | Modern panels: imputation reference and downsampling test samples |

New public data: none needed. Which recent seed studies have released reads is listed in DS14 [待确认 for 2026 studies].

## Analysis steps

Shared modules, in order:

1. [AM01 · Download and verify](../../analyses/AM01-download-and-verify/)
2. [AM17 · Ancient DNA processing](../../analyses/AM17-ancient-dna/)
3. [AM07 · Pangenome graph build and genotyping](../../analyses/AM07-graph-build-and-genotype/)
4. [AM13 · Ancestry and introgression](../../analyses/AM13-ancestry-and-introgression/)

Project-specific steps:

- Process seeds with nf-core/eager (AM17).
- Map to linear and graph references; measure bias.
- Downsample modern samples; test GLIMPSE2; then impute seeds.

**Stepwise work plan with tools**

| Step | Work | Tools (paper) | Output |
|---|---|---|---|
| 1 | Process seed reads: adapter removal, merging, damage profiles | nf-core/eager (AM17) | Clean BAMs |
| 2 | Map to PN_T2T and to the graph | bwa aln, vg giraffe or vg map (AM07) | Linear and graph BAMs |
| 3 | Reference bias on simulated damaged reads and real seeds | custom, gargammel-type simulation | Fig 1 |
| 4 | Downsample modern samples to seed depths; impute | GLIMPSE2 | Fig 2 |
| 5 | Impute seeds above the depth threshold; match to modern cultivars | GLIMPSE2, KING, AM13 | Fig 3 |

## Paper design and split

| Paper | Working title | Type | Figures |
|---|---|---|---|
| T1 | Graph mapping and imputation for ancient grape seeds | methods/application paper | Fig 1–3 |

Each paper: introduction from the gap above; one results section per figure; methods with tool versions from the modules; data availability listing every accession used and the derived tables.

## Risks and novelty check

- Risk: Very low coverage limits every analysis.
- Risk: Gains over linear mapping may be small.
- Risk: Whether raw reads for each ancient-seed dataset are public must be confirmed accession by accession [待确认].
- Novelty: checked against the existing work above (Crossref-verified DOIs). Repeat the search before writing; anything marked [待确认] is not yet verified.

## Rough estimates

- Compute: small to medium [draft]
- Effort: 2–3 months for one person [draft]
- Target: archaeogenomics journal [draft]

## Suggested journal level (suggestion only)

**Specialty journal (archaeogenomics or archaeological science); mid-field if assignments change.** Grape seed papers read here appeared in *Nature Plants*, *PNAS*, *Nature Communications* and *Journal of Archaeological Science*; the method papers in *Genome Biology*, *Nature Genetics* and *PeerJ*. A methods test on existing seeds fits a specialty venue. This is a suggestion, not a decision; impact factors are not used.

## Continue on HPC

Run each step as its own job, in this order. Every job writes `.DONE` or `.FAILED` and a log; the next step starts only after `.DONE`. Template and rules: [`docs/HPC_JOBS.md`](../../../../templates/HPC_JOBS.md).

| Order | Step | Main tools | Resources (rough) |
|---|---|---|---|
| 1 | [AM01](../../analyses/AM01-download-and-verify/) Download and verify | ncbi-datasets-cli, sra-tools, ENA FTP / Aspera | 1–4 CPU, 4 GB, network; array over files |
| 2 | [AM17](../../analyses/AM17-ancient-dna/) Ancient DNA processing | nf-core/eager, mapDamage2, vg | 8 CPU, 32 GB per sample |
| 3 | [AM07](../../analyses/AM07-graph-build-and-genotype/) Pangenome graph build and genotyping | Minigraph-Cactus, PGGB, vg | 32–64 CPU, 256–512 GB for graph builds; 16 CPU, 64 GB per sample for giraffe |
| 4 | [AM13](../../analyses/AM13-ancestry-and-introgression/) Ancestry and introgression | ADMIXTURE, Dsuite, ADMIXTOOLS 2 | 8 CPU, 32 GB |

Public inputs: [DS14](../../data/DS14-ancient-grape-seeds/), [DS02](../../data/DS02-grapepan-v1/), [DS10](../../data/DS10-reseq-472-vitis/), [DS12](../../data/DS12-reseq-204-magris2021/).

## References

- Ramos-Madrigal et al. 2019. Palaeogenomic insights into the origins of French grapevine diversity. *Nature Plants*. [doi:10.1038/s41477-019-0437-5](https://doi.org/10.1038/s41477-019-0437-5)
- Cohen et al. 2023. Ancient DNA from a lost Negev Highlands desert grape reveals a Late Antiquity wine lineage. *Proceedings of the National Academy of Sciences*. [doi:10.1073/pnas.2213563120](https://doi.org/10.1073/pnas.2213563120)
- Noraz et al. 2026. Ancient DNA reveals 4000 years of grapevine diversity, viticulture and clonal propagation in France. *Nature Communications*. [doi:10.1038/s41467-026-70166-z](https://doi.org/10.1038/s41467-026-70166-z)
- Inanli et al. 2026. Grapevine cultivation at Cetamura del Chianti: multiproxy evidence for centuries of continuity from the Etruscans to the Romans. *Journal of Archaeological Science*. [doi:10.1016/j.jas.2026.106605](https://doi.org/10.1016/j.jas.2026.106605)
- Fellows Yates et al. 2021. Reproducible, portable, and efficient ancient genome reconstruction with nf-core/eager. *PeerJ*. [doi:10.7717/peerj.10947](https://doi.org/10.7717/peerj.10947)
- Liu et al. 2024. Grapevine pangenome facilitates trait genetics and genomic breeding. *Nature Genetics*. [doi:10.1038/s41588-024-01967-5](https://doi.org/10.1038/s41588-024-01967-5)
- Martiniano et al. 2020. Removing reference bias and improving indel calling in ancient DNA data analysis by mapping to a sequence variation graph. *Genome Biology*. [doi:10.1186/s13059-020-02160-7](https://doi.org/10.1186/s13059-020-02160-7)
- Rubinacci et al. 2023. Imputation of low-coverage sequencing data from 150,119 UK Biobank genomes. *Nature Genetics*. [doi:10.1038/s41588-023-01438-3](https://doi.org/10.1038/s41588-023-01438-3)
- Wales et al. 2016. The limits and potential of paleogenomic techniques for reconstructing grapevine domestication. *Journal of Archaeological Science*. [doi:10.1016/j.jas.2016.05.014](https://doi.org/10.1016/j.jas.2016.05.014)
