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

## Question

Does graph mapping reduce reference bias for ancient grape seeds, and how accurate is imputation at their depths?

## Hypotheses, planned figures and criteria

No results are given here. Each row says what would count as support; the exact thresholds go into the preregistration.

| Figure or table | Hypothesis or purpose | Criterion |
|---|---|---|
| Fig 1. Reference bias, linear vs graph | Graph mapping reduces allele-balance bias. | Allele balance at known heterozygous sites. |
| Fig 2. Imputation accuracy on downsampled modern samples | Accuracy is acceptable above a depth threshold. | r² by allele-frequency bin; threshold fixed in advance. |
| Fig 3. Matches of seeds to modern cultivars | Some assignments change after graph mapping and imputation. | Changes reported with their support. |

## Preregistration

Before any data are analysed, fill in [`docs/PREREGISTRATION.md`](../../../../templates/PREREGISTRATION.md) for this project: hypotheses, primary outcome, sample inclusion rules, thresholds, stop rules and what will be reported if a hypothesis fails. Commit it with a date. Criteria from any earlier attempt are reference only and are not carried over.

## Data

| Module | Dataset |
|---|---|
| [DS14](../../data/DS14-ancient-grape-seeds/) | Archaeological grape seed sequencing |
| [DS02](../../data/DS02-grapepan-v1/) | Grapepan v1.0: T2T haplotypes, graphs and a 466-accession resequencing panel |
| [DS10](../../data/DS10-reseq-472-vitis/) | Resequencing of 472 Vitis accessions (and the 2017 domestication panel) |
| [DS12](../../data/DS12-reseq-204-magris2021/) | Resequencing of 204 V. vinifera accessions (Magris et al. 2021) |

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
