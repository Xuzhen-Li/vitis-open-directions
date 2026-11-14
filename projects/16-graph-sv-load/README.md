# 16. Inherited and clonal structural variants on a graph: where hemizygous SVs sit and why

中文：图上分型的结构变异：有性起源继承的与克隆期新增的半合子 SV 分布与负担

Rank 16 of 22 (score F 2 + N 2 + E 2 = 6; see docs/RANKING.md) · Tier: Medium (E = 2, effort range ending after 6 weeks and by 4 months) · Origin: continued: started earlier and restarted here from public data under a new preregistration · Status: draft v0.3.2, 2026-11-14

## Gap

SV load in grape has been estimated on linear references, and hemizygosity has been compared across crops. No comparison was found between hemizygous SVs inherited at a cultivar's sexual origin and SVs that arose during clonal propagation using a single graph-based genotyping pipeline.

**Existing work**

- [Zhou et al. 2017](https://doi.org/10.1073/pnas.1709257114): deleterious load in domestication and clonal propagation.
- [Zhou et al. 2019](https://doi.org/10.1038/s41477-019-0507-8): SV population genetics in grape.
- [Zhou et al. 2018](https://doi.org/10.1101/508119): preprint version of the SV study, which discusses clonal propagation.
- [Xiao et al. 2023](https://doi.org/10.1073/pnas.2222041120): introgression and load on a linear reference.
- [Xiao et al. 2025](https://doi.org/10.1038/s41467-025-56817-7): reproductive systems and the grape genome.
- [Fiscus et al. 2025](https://doi.org/10.1111/nph.70238): load in wild V. arizonica.
- [Peng et al. 2025](https://doi.org/10.1073/pnas.2422487122): hemizygous genes across crops with different reproductive systems; more hemizygous genes in clonal crops, mostly near centromeres (not a clonal-load study).

**How this project differs**

Graph genotyping reduces reference bias and places all panels on one pipeline. Inherited SVs are separated from clone-specific SVs using cultivars with known parents (for example Cabernet Sauvignon, from Cabernet franc × Sauvignon blanc [待确认: VIVC record]) and clone panels. Differences between cultivated and wild grapes are not attributed to clonal propagation alone, because domestication bottlenecks and hybrid origin are confounded with it.

## Question

Do hemizygous SVs that arose between clones sit in different genomic contexts from hemizygous SVs inherited at the cultivar's sexual origin, and how do inherited hemizygous SVs relate to recombination and repeat density in cultivated versus wild grapes?

## Hypotheses, planned figures and criteria

No results are given here. Each row says what would count as support; the exact thresholds go into the preregistration.

| Figure or table | Hypothesis or purpose | Criterion |
|---|---|---|
| Fig 1. Reference bias: graph vs linear genotyping | Graph genotypes have less allele-balance bias. | Allele balance at long-read-validated sites; concordance with assemblies. |
| Fig 2. Inherited vs clone-specific hemizygous SVs | Inherited hemizygous SVs reflect the sexual history (more in low-recombination regions); clone-specific SVs follow mutational input (repeat and TE density) rather than recombination. | Clone-specific SVs come from long-read or assembly comparisons of clones, because graph genotyping misses new SVs. In the trio, the parents are clones too: an SV present in the offspring and absent from both sampled parent plants is labelled as lost later in a parent's clonal lineage, new in the germline at the cross, or new during the offspring's clonal phase (only when it is present in some but not all offspring clones); where the data cannot tell these apart, it is labelled origin unresolved and kept out of the clone-specific class. Mixed logistic model with sample as a random effect and recombination rate, repeat and TE density, and centromere distance as covariates; supported if the preregistered coefficients' intervals exclude zero. |
| Fig 3. Inherited hemizygous SVs, cultivated vs wild | Cultivated and wild grapes differ in where inherited hemizygous SVs sit. | Group × region model with repeat and TE density covariates and a sample random effect; framed as cultivated vs wild, not as an effect of clonal propagation. |
| Fig 4. Load split by zygosity | Expectations stated separately: hemizygous deleterious variants are expressed in any diploid carrier, whereas heterozygous recessive ones are masked; what is specific to clones is that, without segregation and recombination, neither kind can be purged through sexual generations. | Load counted on derived alleles (AM26), split into hemizygous and heterozygous; reported with and without ROH as a covariate, because ROH and group are correlated. |

## Preregistration

Before any data are analysed, fill in [`docs/PREREGISTRATION.md`](../../docs/PREREGISTRATION.md) for this project: hypotheses, primary outcome, sample inclusion rules, thresholds, stop rules and what will be reported if a hypothesis fails. Commit it with a date. Criteria from any earlier attempt are reference only and are not carried over.

## Data

| Module | Dataset |
|---|---|
| [DS02](../../data/DS02-grapepan-v1/) | Grapepan v1.0: T2T haplotypes, graphs and a 466-accession resequencing panel |
| [DS03](../../data/DS03-vitis-super-pangenome-72/) | Vitis super-pangenome: 72 haplotype-resolved accessions |
| [DS10](../../data/DS10-reseq-472-vitis/) | Resequencing of 472 Vitis accessions (and the 2017 domestication panel) |
| [DS12](../../data/DS12-reseq-204-magris2021/) | Resequencing of 204 V. vinifera accessions (Magris et al. 2021) |
| [DS13](../../data/DS13-clone-somatic-variation/) | Clone resequencing across cultivars (Zinfandel, Chardonnay, Pinot noir, Malbec, Merlot and others) |
| [DS18](../../data/DS18-methylome-and-trio/) | Public grape methylomes and a phased Cabernet Sauvignon trio |
| [DS01](../../data/DS01-pn40024-references/) | PN40024 references: PN_T2T (v5), PN40024.v4 and 12X |

## Analysis steps

Shared modules, in order:

1. [AM01 · Download and verify](../../analyses/AM01-download-and-verify/)
2. [AM03 · Short-read mapping and small-variant calling](../../analyses/AM03-short-read-variants/)
3. [AM04 · Sample identity, clones and relatedness](../../analyses/AM04-sample-identity/)
4. [AM07 · Pangenome graph build and genotyping](../../analyses/AM07-graph-build-and-genotype/)
5. [AM18 · Long-read SV calling](../../analyses/AM18-long-read-sv/)
6. [AM26 · Phasing, ancestral states and recombination rates](../../analyses/AM26-phasing-polarisation-recombination/)
7. [AM12 · Runs of homozygosity and deleterious load](../../analyses/AM12-roh-and-load/)

Project-specific steps:

- Genotype SVs through the graph (AM07); validate on long-read samples (AM18).
- Call clone-specific SVs from long reads or assemblies of clones (DS13, AM18); use the trio (DS18) to distinguish inherited from new SVs, using the origin labels of Fig 2.
- Take recombination rates from published linkage maps (AM26) [待确认: map source]; compute repeat and TE density per window.
- Polarise and score variants (AM26, AM12); split by zygosity; fit the models.

## Paper design and split

| Paper | Working title | Type | Figures |
|---|---|---|---|
| P1 | Inherited and clonal hemizygous structural variants in grape | main paper | Fig 1–4 |

Each paper: introduction from the gap above; one results section per figure; methods with tool versions from the modules; data availability listing every accession used and the derived tables.

## Risks and novelty check

- Risk: Hemizygous calls from short reads are error-prone; validate on long reads.
- Risk: Graph genotyping recovers SVs already in the graph; new clone-specific SVs are mostly absent, so the graph component is biased toward old, shared SVs.
- Risk: Recombination proxies from linkage maps are coarse.
- Risk: Whether public long-read data from clones are sufficient for the clone-specific class is not yet verified [待确认].
- Novelty: checked against the existing work above (Crossref-verified DOIs). Repeat the search before writing; anything marked [待确认] is not yet verified.

## Rough estimates

- Compute: medium [draft]
- Effort: 2–4 months for one person [draft]
- Target: genetics or evolution journal [draft]

## Continue on HPC

Run each step as its own job, in this order. Every job writes `.DONE` or `.FAILED` and a log; the next step starts only after `.DONE`. Template and rules: [`docs/HPC_JOBS.md`](../../docs/HPC_JOBS.md).

| Order | Step | Main tools | Resources (rough) |
|---|---|---|---|
| 1 | [AM01](../../analyses/AM01-download-and-verify/) Download and verify | ncbi-datasets-cli, sra-tools, ENA FTP / Aspera | 1–4 CPU, 4 GB, network; array over files |
| 2 | [AM03](../../analyses/AM03-short-read-variants/) Short-read mapping and small-variant calling | bwa-mem2, samtools, DeepVariant | 16 CPU, 64 GB, 6–24 h per sample (DeepVariant); joint step 32 CPU, 128 GB |
| 3 | [AM04](../../analyses/AM04-sample-identity/) Sample identity, clones and relatedness | plink2, KING, VIVC | 8 CPU, 32 GB, < 2 h |
| 4 | [AM07](../../analyses/AM07-graph-build-and-genotype/) Pangenome graph build and genotyping | Minigraph-Cactus, PGGB, vg | 32–64 CPU, 256–512 GB for graph builds; 16 CPU, 64 GB per sample for giraffe |
| 5 | [AM18](../../analyses/AM18-long-read-sv/) Long-read SV calling | Sniffles2, cuteSV, pbsv | 16 CPU, 64 GB per sample |
| 6 | [AM26](../../analyses/AM26-phasing-polarisation-recombination/) Phasing, ancestral states and recombination rates | SHAPEIT5, minimap2, est-sfs | 8–16 CPU, 32–64 GB per chromosome; est-sfs single-threaded, hours per chromosome |
| 7 | [AM12](../../analyses/AM12-roh-and-load/) Runs of homozygosity and deleterious load | bcftools roh, SnpEff, PlantCaduceus | 4 CPU, 16 GB per chromosome |

Public inputs: [DS02](../../data/DS02-grapepan-v1/), [DS03](../../data/DS03-vitis-super-pangenome-72/), [DS10](../../data/DS10-reseq-472-vitis/), [DS12](../../data/DS12-reseq-204-magris2021/), [DS13](../../data/DS13-clone-somatic-variation/), [DS18](../../data/DS18-methylome-and-trio/), [DS01](../../data/DS01-pn40024-references/).

## References

- Zhou et al. 2017. Evolutionary genomics of grape ( Vitis vinifera ssp. vinifera ) domestication. *Proceedings of the National Academy of Sciences*. [doi:10.1073/pnas.1709257114](https://doi.org/10.1073/pnas.1709257114)
- Zhou et al. 2019. The population genetics of structural variants in grapevine domestication. *Nature Plants*. [doi:10.1038/s41477-019-0507-8](https://doi.org/10.1038/s41477-019-0507-8)
- Zhou et al. 2018. Structural variants, clonal propagation, and genome evolution in grapevine ( Vitis vinifera ). *bioRxiv*. [doi:10.1101/508119](https://doi.org/10.1101/508119)
- Xiao et al. 2023. Adaptive and maladaptive introgression in grapevine domestication. *Proceedings of the National Academy of Sciences*. [doi:10.1073/pnas.2222041120](https://doi.org/10.1073/pnas.2222041120)
- Xiao et al. 2025. Impacts of reproductive systems on grapevine genome and breeding. *Nature Communications*. [doi:10.1038/s41467-025-56817-7](https://doi.org/10.1038/s41467-025-56817-7)
- Fiscus et al. 2025. Mutational load and adaptive variation are shaped by climate and species range dynamics in Vitis arizonica. *New Phytologist*. [doi:10.1111/nph.70238](https://doi.org/10.1111/nph.70238)
- Peng et al. 2025. The genomic and epigenomic landscapes of hemizygous genes across crops with contrasting reproductive systems. *Proceedings of the National Academy of Sciences*. [doi:10.1073/pnas.2422487122](https://doi.org/10.1073/pnas.2422487122)
