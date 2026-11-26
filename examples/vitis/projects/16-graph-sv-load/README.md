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

**Background survey (literature read for this plan)**

The cost-of-domestication hypothesis predicts more deleterious variants in domesticated species, through bottlenecks, linked selection and, in clonal crops, sheltering of recessive variants ([Moyers et al. 2018](https://doi.org/10.1093/jhered/esx069)); genomic load estimates and their limits have been set out for non-model species ([Bertorelle et al. 2022](https://doi.org/10.1038/s41576-022-00448-x)). In grape, cultivars carry more deleterious mutations in heterozygous state than wild ancestors, partly because of clonal propagation ([Zhou et al. 2017](https://doi.org/10.1073/pnas.1709257114)); SV population genetics showed purifying selection on SVs and many hemizygous genes in Chardonnay ([Zhou et al. 2019](https://doi.org/10.1038/s41477-019-0507-8)); introgression carried both adaptive and maladaptive variants into cultivars ([Xiao et al. 2023](https://doi.org/10.1073/pnas.2222041120)); and reproductive systems shape the grape genome and breeding ([Xiao et al. 2025](https://doi.org/10.1038/s41467-025-56817-7)). In wild *V. arizonica*, load was shaped by climate and range dynamics ([Fiscus et al. 2025](https://doi.org/10.1111/nph.70238)).

Hemizygous genes on autosomes were compared across 22 genomes with clonal, outcrossed and inbred histories, with more hemizygous genes in clonal lineages ([Peng et al. 2025](https://doi.org/10.1073/pnas.2422487122)). Somatic SVs between clones are documented, including catastrophic rearrangements ([Carbonell-Bejerano et al. 2017](https://doi.org/10.1104/pp.17.00715)) and clone SVs that sit mostly in repeat and centromere regions ([Callipo et al. 2026](https://doi.org/10.1186/s13059-026-04184-x)). A phased Cabernet Sauvignon trio separates inherited from new variants ([Cochetel et al. 2025](https://doi.org/10.1186/s13059-025-03858-2)). Graph genotyping with PanGenie or vg reduces reference bias for SVs ([Ebler et al. 2022](https://doi.org/10.1038/s41588-022-01043-w); [Sirén et al. 2021](https://doi.org/10.1126/science.abg8871)).

**Specific gap.** No grape study was found that separates hemizygous SVs inherited at a cultivar's sexual origin from SVs that arose during clonal propagation with one graph-based pipeline, and relates each class to recombination and repeat density [待确认].

## Question

Do hemizygous SVs that arose between clones sit in different genomic contexts from hemizygous SVs inherited at the cultivar's sexual origin, and how do inherited hemizygous SVs relate to recombination and repeat density in cultivated versus wild grapes?

## Scope update (2026-11-26)

Added 2026-11-26. This section narrows or reframes the plan above; where the two differ, this section applies. Earlier text is kept unchanged.

**Narrowed scope: inherited versus clonal hemizygous differences within grape.** The cross-crop comparison of clonal and sexual hemizygosity is partly answered ([Peng et al. 2025](https://doi.org/10.1073/pnas.2422487122)). The project now asks only: within grape, how do hemizygous SVs that arose between clones of one cultivar differ from hemizygous SVs inherited at its sexual origin, in size, repeat context, gene content and expression?

Target: a first-quartile (Q1) journal in plant science, genetics or evolution. Quartile lists change each year, so the journal is chosen from the current list at submission [to confirm]. The points below are what the paper needs to compete at that level.

- Clone families with several sequenced clones per cultivar, so clonal SVs (present in some clones) and inherited SVs (present in all clones and traceable to a parent haplotype) are separated.
- Long-read or assembly confirmation for a stated share of both classes, with depth and loss-of-heterozygosity evidence as in the reference study below.
- Allele-specific expression of genes in both classes (project 19) as the functional readout.
- Known clonal colour-loss events used as positive controls.

**Fallback.** If too few clone families have enough clones, report inherited hemizygous SVs only and drop the clonal contrast.

## Hypotheses, planned figures and criteria

No results are given here. Each row says what would count as support; the exact thresholds go into the preregistration.

| Figure or table | Hypothesis or purpose | Criterion |
|---|---|---|
| Fig 1. Reference bias: graph vs linear genotyping | Graph genotypes have less allele-balance bias. | Allele balance at long-read-validated sites; concordance with assemblies. |
| Fig 2. Inherited vs clone-specific hemizygous SVs | Inherited hemizygous SVs reflect the sexual history (more in low-recombination regions); clone-specific SVs follow mutational input (repeat and TE density) rather than recombination. | Clone-specific SVs come from long-read or assembly comparisons of clones, because graph genotyping misses new SVs. In the trio, the parents are clones too: an SV present in the offspring and absent from both sampled parent plants is labelled as lost later in a parent's clonal lineage, new in the germline at the cross, or new during the offspring's clonal phase (only when it is present in some but not all offspring clones); where the data cannot tell these apart, it is labelled origin unresolved and kept out of the clone-specific class. Mixed logistic model with sample as a random effect and recombination rate, repeat and TE density, and centromere distance as covariates; supported if the preregistered coefficients' intervals exclude zero. |
| Fig 3. Inherited hemizygous SVs, cultivated vs wild | Cultivated and wild grapes differ in where inherited hemizygous SVs sit. | Group × region model with repeat and TE density covariates and a sample random effect; framed as cultivated vs wild, not as an effect of clonal propagation. |
| Fig 4. Load split by zygosity | Expectations stated separately: hemizygous deleterious variants are expressed in any diploid carrier, whereas heterozygous recessive ones are masked; what is specific to clones is that, without segregation and recombination, neither kind can be purged through sexual generations. | Load counted on derived alleles (AM26), split into hemizygous and heterozygous; reported with and without ROH as a covariate, because ROH and group are correlated. |

**Expected results and how they will be read**

- Fig 1: lower allele-balance bias with graph genotypes justifies the graph route; if bias is similar, linear calls are kept and the graph is reported as optional.
- Fig 2: inherited hemizygous SVs concentrated in low-recombination regions and clone-specific SVs following repeat and TE density would show two different origins; similar distributions would argue against a separate clonal process for SVs.
- Fig 3 compares cultivated and wild grapes descriptively; differences are not attributed to clonal propagation alone, because bottleneck and hybrid origin are confounded with it.
- Fig 4 splits load by zygosity with the expectations written down before the run.

## Preregistration

Before any data are analysed, fill in [`docs/PREREGISTRATION.md`](../../../../templates/PREREGISTRATION.md) for this project: hypotheses, primary outcome, sample inclusion rules, thresholds, stop rules and what will be reported if a hypothesis fails. Commit it with a date. Criteria from any earlier attempt are reference only and are not carried over.

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

**How each dataset is used**

| Module | Role in this project |
|---|---|
| DS02, DS03 | Graph, haplotypes and long-read samples for SV truth |
| DS10, DS12 | Cultivated and wild short-read panels for graph genotyping |
| DS13 | Clone panels for clone-specific SVs |
| DS18 | Phased Cabernet Sauvignon trio for inherited versus new SVs |
| DS01 | PN_T2T coordinates and masks |

New public data: none needed. The source of the recombination map is open in AM26 [待确认].

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

**Stepwise work plan with tools**

| Step | Work | Tools (paper) | Output |
|---|---|---|---|
| 1 | Identity groups and clone groups (project 08) | AM04 | Sample table |
| 2 | SV genotyping in short-read panels through the graph; compare with linear calls | PanGenie or vg (AM07), AM03 | SV VCFs, Fig 1 |
| 3 | Long-read validation subset | AM18 | Validation table |
| 4 | Clone-specific SVs from clone long reads or assemblies; origin labels from the trio | AM18, DS18 | Inherited/clonal labels |
| 5 | Window covariates: recombination (published maps), repeats, TE density, centromere distance | AM26, AM10 | Covariate table |
| 6 | Polarise; score deleterious effects; split by zygosity; fit models | est-sfs, SIFT-type scores (AM12, AM26) | Fig 2 to Fig 4 |

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

## Risks and how to handle them

Added 2026-11-26. Each row names a risk, the evidence behind it, and a concrete check or fallback. Sources cited here were read for this section and their DOIs were checked on Crossref; preprints are marked.

| Area | Risk | Check or mitigation |
|---|---|---|
| Data access and licence | The trio reads and assemblies of DS18 are available, but parts of one phased epigenomics study were blocked on the check, and one clone study is still to be confirmed ([data/DOWNLOADS.md](../../data/DOWNLOADS.md)). | Plan the clonal class on confirmed long-read clone data only. |
| SV calling variability | SV detection varies with caller, reference, alignment strategy and coverage ([Nardone et al. 2025](https://doi.org/10.3390/biomedicines13081949)). | Require two callers to agree, validate a random sample on long reads, and report the false discovery estimate. |
| Clonal SVs need long reads | Long reads found eleven large somatic SVs in one Tempranillo clone ([Alañón-Sánchez et al. 2026](https://doi.org/10.1186/s12870-026-08212-7)); SVs among Pinot noir clones lie mostly in repeats and centromeric repeats ([Callipo et al. 2026](https://doi.org/10.1186/s13059-026-04184-x)). | Build the clone-specific class from long-read data only; compare its genomic context with inherited SVs inside the same repeat classes. |
| Reference bias and genome choice | Graph genotyping favours old shared SVs (see above). | Report the graph-based and assembly-based classes separately. |
| Clones, synonyms and pedigree | Duplicate genotypes and relatives inflate SV frequencies. | One sample per genotype (project 08). |
| Sample size and power | Few cultivars have both long-read clone data and a trio. | State the number of cultivars in each class before testing; descriptive below the minimum. |
| Computing cost | Long-read SV calling is moderate; graph genotyping of panels is larger. | Run the long-read part first; it decides whether the panel part is needed. |

**Recent and competing work (search of 2024 to 2026 literature on 2026-11-26)**

- Across 22 genomes of several crops, hemizygous genes averaged 8.7% in outcrossed and 13.8% in clonal samples, sat more often in centromeric regions, showed weaker purifying selection and lower expression ([Peng et al. 2025](https://doi.org/10.1073/pnas.2422487122)). The clonal-versus-sexual contrast and the genomic context of hemizygous genes are therefore partly answered. What remains is the split, within grape, between hemizygous SVs inherited at the sexual origin and those that arose between clones.

**What would end the idea, and the fallback.** If the inherited and clonal classes cannot be separated with the available trios and clone long reads, the main contrast cannot be tested. The fallback is a grape extension of the cross-crop hemizygosity result with the recombination analysis.

**Journal-level realism.** The cross-crop result appeared in *PNAS*; a grape-specific follow-up fits mid-field unless the inherited versus clonal contrast is clear and new.

## Reference study in another species

Added 2026-11-26. Published studies that already did this kind of work in another species, to plan the grape version against. Every DOI was checked on Crossref. Figures are described, not copied; a figure redrawn for a grape paper would be marked "Redrawn after" its source. The last bullet for each study lists what a grape results section would need; it is a planning suggestion, not a finding of that study.

### Wang et al. 2021

- **Paper:** [Wang et al. 2021](https://doi.org/10.1038/s41477-021-00941-x), *Nature Plants*.
- **Note:** Only the figure titles were read, not the captions.
- **Species:** Sweet orange, 114 somatic mutants.
- **What was done:** A reference genome and six diploid mutant genomes were assembled; 114 somatic mutants were resequenced; somatic SNVs, SVs and transposon movements were classified and linked to fruit acidity.
- **Figures:** Fig. 1 sampling across South China and mutant phenotypes; Fig. 2 PCA and relationships; Fig. 3 genomic positions of somatic variants; Fig. 4 classes of somatic transposon movements; Fig. 5 history of divergence and spread.
- **What a grape results section would need:** SV and transposon detection between clones; the genomic distribution of somatic variants; association with phenotype.

### Ríos et al. 2008

- **Paper:** [Ríos et al. 2008](https://doi.org/10.1186/1471-2164-9-381), *BMC Genomics* (PMC2533677). Licence CC BY 2.0: figures may be reused with credit; none are copied here.
- **Species:** clementine (*Citrus clementina*), a heterozygous, vegetatively propagated fruit tree.
- **What was done:** two fast-neutron mutants expected to carry hemizygous deletions were studied; array comparative genomic hybridization found under-represented genes; homologues were placed on poplar, *Arabidopsis* and grapevine chromosomes; one deletion was mapped physically, and its genes were linked to expression and a chlorophyll phenotype; SNP alleles of one deleted gene were compared between mutant and wild type.
- **Figures:** Fig. 1 the protocol; Fig. 2 and 3 homologues on other genomes; Fig. 4 and 6 gene content and order of the deletion; Fig. 5 physical mapping; Fig. 7 chlorophyll a/b ratio; Fig. 8 expression of genes in the deletion; Fig. 9 SNP alleles in a deleted gene.
- **What its results section needed:** detection of a hemizygous deletion on a heterozygous background, confirmation by loss of one allele at heterozygous sites, mapping of its boundaries, and expression of the affected genes.
- **Grape version and what grape adds:** the same confirmation logic (depth drop plus loss of heterozygosity, boundaries from long reads, allele-specific expression) applied to natural variation; grape adds the split the citrus mutants could not give, between hemizygous SVs that arose between clones and those inherited at the sexual origin (see Scope update above).

### Q1-level bar

Target: a first-quartile (Q1) journal in plant science, genetics or evolution. Quartile lists change each year, so the journal is chosen from the current list at submission [to confirm]. To compete at that level, the grape paper needs the points listed in the Scope update section above, which applies to this project.

## Rough estimates

- Compute: medium [draft]
- Effort: 2–4 months for one person [draft]
- Target: genetics or evolution journal [draft]

## Suggested journal level (suggestion only)

**Mid-field journal (genetics or evolution); broad-interest if the inherited versus clonal contrast is clear.** Grape load and SV papers read here appeared in *PNAS*, *Nature Plants*, *Nature Communications* and *New Phytologist*; general load syntheses in *Journal of Heredity* and *Nat Rev Genet*. This is a suggestion, not a decision; impact factors are not used.

## Continue on HPC

Run each step as its own job, in this order. Every job writes `.DONE` or `.FAILED` and a log; the next step starts only after `.DONE`. Template and rules: [`docs/HPC_JOBS.md`](../../../../templates/HPC_JOBS.md).

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
- Bertorelle et al. 2022. Genetic load: genomic estimates and applications in non-model animals. *Nat Rev Genet*. [doi:10.1038/s41576-022-00448-x](https://doi.org/10.1038/s41576-022-00448-x)
- Callipo et al. 2026. A dual genome-methylome map of clonal evolution in grapevine. *Genome Biology*. [doi:10.1186/s13059-026-04184-x](https://doi.org/10.1186/s13059-026-04184-x)
- Carbonell-Bejerano et al. 2017. Catastrophic Unbalanced Genome Rearrangements Cause Somatic Loss of Berry Color in Grapevine. *Plant Physiology*. [doi:10.1104/pp.17.00715](https://doi.org/10.1104/pp.17.00715)
- Cochetel et al. 2025. Phased epigenomics and methylation inheritance in a historical Vitis vinifera hybrid. *Genome Biology*. [doi:10.1186/s13059-025-03858-2](https://doi.org/10.1186/s13059-025-03858-2)
- Ebler et al. 2022. Pangenome-based genome inference allows efficient and accurate genotyping across a wide spectrum of variant classes. *Nature Genetics*. [doi:10.1038/s41588-022-01043-w](https://doi.org/10.1038/s41588-022-01043-w)
- Moyers et al. 2018. Genetic Costs of Domestication and Improvement. *Journal of Heredity*. [doi:10.1093/jhered/esx069](https://doi.org/10.1093/jhered/esx069)
- Sirén et al. 2021. Pangenomics enables genotyping of known structural variants in 5202 diverse genomes. *Science*. [doi:10.1126/science.abg8871](https://doi.org/10.1126/science.abg8871)
- Nardone et al. 2025. A Hitchhiker Guide to Structural Variant Calling: A Comprehensive Benchmark Through Different Sequencing Technologies. *Biomedicines*. [doi:10.3390/biomedicines13081949](https://doi.org/10.3390/biomedicines13081949)
- Alañón-Sánchez et al. 2026. A complex reciprocal translocation is linked to reduced gamete viability in a loose-bunch grapevine somatic variant. *BMC Plant Biology*. [doi:10.1186/s12870-026-08212-7](https://doi.org/10.1186/s12870-026-08212-7)
- Wang et al. 2021. Somatic variations led to the selection of acidic and acidless orange cultivars. *Nature Plants*. [doi:10.1038/s41477-021-00941-x](https://doi.org/10.1038/s41477-021-00941-x)
- Ríos et al. 2008. Characterization of hemizygous deletions in Citrus using array-Comparative Genomic Hybridization and microsynteny comparisons with the poplar genome. *BMC Genomics*. [doi:10.1186/1471-2164-9-381](https://doi.org/10.1186/1471-2164-9-381)
