# 24. Pedigree and linkage-disequilibrium recombination maps in grape

中文：葡萄的系谱与连锁不平衡重组图谱

Not scored (see docs/RANKING.md; projects 23 to 26 were added after the ranking) · Tier: Medium to Long [draft] · Origin: continued: design written earlier, restarted here from public data under a new preregistration · Status: draft, 2026-11-25 · Progress: [STATUS.md](STATUS.md)

## Gap

Grape genetic maps come from bi-parental crosses and are given in cM at marker resolution. A fine-scale, population-specific LD-based recombination map on PN_T2T, estimated separately for wild and cultivated groups and compared descriptively with published maps, was not found [待确认: repeat the search before writing].

**Existing work and background survey**

Recombination rate and distribution vary widely across eukaryotes ([Stapley et al. 2017](https://doi.org/10.1098/rstb.2016.0455)); genetic maps of 57 flowering plants showed that rate scales with relative chromosome size and that telomeres and centromeres shape the broad-scale distribution of crossovers, which follows gene distribution ([Brazier and Glémin 2022](https://doi.org/10.1371/journal.pgen.1010141)). In humans, a sequence-level map from pedigrees showed mutagenic effects of crossovers ([Halldorsson et al. 2019](https://doi.org/10.1126/science.aau1043)).

Grape maps: an integrated SSR map from five mapping populations ([Doligez et al. 2006](https://doi.org/10.1007/s00122-006-0295-1)); HetMappS for GBS maps in heterozygous species ([Hyma et al. 2015](https://doi.org/10.1371/journal.pone.0134880)); rhAmpSeq core-genome haplotype markers for maps across *Vitis* species ([Zou et al. 2020](https://doi.org/10.1038/s41467-019-14280-1)); a high-density integrated map from three populations on the Vitis18K chip ([Vervalle et al. 2022](https://doi.org/10.1007/s00122-022-04225-6)). Introgression reshaped recombination in interspecific hybrids ([Delame et al. 2019](https://doi.org/10.1007/s00122-018-3260-x)), and North American wild grapes show extensive introgression ([Morales-Cruz et al. 2021](https://doi.org/10.1186/s13059-021-02467-z)).

Methods: LDhelmet estimates fine-scale rates from population data and is robust to some selection and noise ([Chan et al. 2012](https://doi.org/10.1371/journal.pgen.1003090)); pyrho accounts for demography and gave population-specific maps across 26 human populations ([Spence and Song 2019](https://doi.org/10.1126/sciadv.aaw9206)); SHAPEIT5 phases large samples ([Hofmeister et al. 2023](https://doi.org/10.1038/s41588-023-01415-w)); Relate infers genealogies and population-size histories ([Speidel et al. 2019](https://doi.org/10.1038/s41588-019-0484-x)); R/qtl handles maps in experimental crosses ([Broman et al. 2003](https://doi.org/10.1093/bioinformatics/btg112)).

**How this project differs**

Historical LD-based rates (rho_LD) and recent pedigree rates (r_ped) are kept apart; failure of one route does not validate the other. Published maps are a descriptive comparison only, never a calibration. The pedigree route opens only if project 23 finds enough public informative meioses.

## Question

What does the fine-scale LD-based recombination landscape look like on PN_T2T in wild and cultivated grape groups, and how does it compare with published genetic maps?

## Hypotheses, planned figures and criteria

No results are given here. Each row says what would count as support; the exact thresholds go into the preregistration.

| Figure or table | Hypothesis or purpose | Criterion |
|---|---|---|
| Fig 1. Simulation check | rho_LD is estimable at the planned sample sizes. | Simulations under the inferred demography for each group recover known rates within a preregistered error; if not, the group is reported as not estimable. |
| Fig 2. rho_LD landscapes per group | Rates are lower in centromeric and pericentromeric windows. | Window-level rho_LD after masking; missing information is NA, not zero. |
| Fig 3. Comparison with published maps | Window-level rho_LD correlates with cM per Mb. | Descriptive correlation with interpolated published maps; not independent validation. |
| Fig 4. Group differences | Landscapes differ between wild and cultivated groups beyond what demography explains. | Differences tested against simulations with each group's demography; clonal propagation and structure listed as confounders. |

## Preregistration

Before any data are analysed, fill in [`docs/PREREGISTRATION.md`](../../../../templates/PREREGISTRATION.md) for this project: hypotheses, primary outcome, sample inclusion rules, thresholds, stop rules and what will be reported if a hypothesis fails. Commit it with a date. Criteria from any earlier attempt are reference only and are not carried over.

## Data

| Module | Dataset |
|---|---|
| [DS10](../../data/DS10-reseq-472-vitis/) | Resequencing of 472 Vitis accessions (and the 2017 domestication panel) |
| [DS12](../../data/DS12-reseq-204-magris2021/) | Resequencing of 204 V. vinifera accessions (Magris et al. 2021) |
| [DS02](../../data/DS02-grapepan-v1/) | Grapepan v1.0: T2T haplotypes, graphs and a 466-accession resequencing panel |
| [DS01](../../data/DS01-pn40024-references/) | PN40024 references: PN_T2T (v5), PN40024.v4 and 12X |

Published maps (Doligez et al. 2006; Vervalle et al. 2022; Zou et al. 2020) are used for comparison only; which has enough markers to interpolate onto PN_T2T is open [待确认]. New public data: none needed.

## Analysis steps

Shared modules, in order:

1. [AM04 · Sample identity, clones and relatedness](../../analyses/AM04-sample-identity/)
2. [AM26 · Phasing, ancestral states and recombination rates](../../analyses/AM26-phasing-polarisation-recombination/)
3. [AM14 · Ancestral recombination graphs and allele age](../../analyses/AM14-ancestral-recombination-graph/)

**Stepwise work plan with tools**

| Step | Work | Tools (paper) | Output |
|---|---|---|---|
| 1 | Clone-free, unrelated sample sets per group from projects 08 and 23 | AM04 | Group lists |
| 2 | Phase on PN_T2T; mask centromeres and low-mappability repeats | SHAPEIT5 (AM26) | Phased VCFs |
| 3 | Population-size history per group [待确认: Relate or SMC++] | Relate (AM14) | Demography inputs |
| 4 | Simulate under each demography; test estimability | msprime, pyrho | Fig 1 |
| 5 | Estimate rho_LD per group and window | pyrho or LDhelmet (AM26) | Fig 2 |
| 6 | Interpolate published maps; compare descriptively; contrast groups | custom | Fig 3, Fig 4 |

## Expected results and how they will be read

- Fig 1 decides which groups are analysed; a group that fails is reported as not estimable.
- Fig 2: lower rates around centromeres would agree with the broad-scale pattern reported across flowering plants; windows without information stay NA.
- Fig 3: a positive correlation with published maps supports the landscape at broad scale; disagreement is reported, not resolved by tuning.
- Fig 4 is read with care, because bottlenecks, structure and clonal propagation all distort rho_LD.

## Paper design and split

| Paper | Working title | Type | Figures |
|---|---|---|---|
| R1 | Fine-scale LD-based recombination landscapes in wild and cultivated grape | research article | Fig 1–4 |
| R2 | Pedigree recombination from public families (only if project 23 allows) | follow-up | to be set in its own preregistration |

Each paper: introduction from the gap above; one results section per figure; methods with tool versions from the modules; data availability listing every accession used and the derived tables.

## Risks and novelty check

- Risk: Bottlenecks, structure and clonal propagation distort LD-based estimates; simulations must use each group's demography.
- Risk: A gap in structural-variant regions may be a detection gap, not a cold spot.
- Risk: Do not present the result as the first such map; a limited search is not proof.
- Novelty: checked against the existing work above (Crossref-verified DOIs). Repeat the search before writing; anything marked [待确认] is not yet verified.

## Risks and how to handle them

Added 2026-11-26. Each row names a risk, the evidence behind it, and a concrete check or fallback. Sources cited here were read for this section and their DOIs were checked on Crossref; preprints are marked.

| Area | Risk | Check or mitigation |
|---|---|---|
| Data access and licence | DS11 runs were blocked on the public listing check; INSDC panels are available ([data/DOWNLOADS.md](../../data/DOWNLOADS.md)). | Plan group sizes on INSDC panels. |
| Demography | Bottlenecks, hidden structure and population size changes can greatly reduce power and raise false positives of LD-based hotspot detection, and neither can be predicted without the demographic history ([Dapper et al. 2018](https://doi.org/10.1093/molbev/msx272)). | Simulate under each group demography and report hotspots only against a demography-matched null. |
| Clonal propagation | Cloning raises heterozygosity and changes the site frequency spectrum ([Xiao et al. 2025](https://doi.org/10.1038/s41467-025-56817-7)); cultivated LD may reflect few meioses since the sexual origin of each cultivar. | Estimate cultivated maps on unique genotypes only and compare with pedigree-based crossovers (project 23). |
| Small wild groups | Some wild groups have few samples; recombination maps can be inferred from a single pair of unphased genomes with iSMC ([Barroso et al. 2019](https://doi.org/10.1371/journal.pgen.1008449)). | Use iSMC-type estimates for small groups as a cross-check on LD-based maps. |
| Inversions | Inversions reshaped the recombination landscape in a pineapple F1 population ([Fang et al. 2026](https://doi.org/10.1093/hr/uhag189)). | Mask inversions from project 17 or analyse them separately. |
| Reference bias and genome choice | Maps on PN_T2T can miss recombination in regions absent from it (see above). | Report coverage of the map by region and repeat on a wild haplotype for one chromosome. |
| Computing cost | Moderate (LD-based estimation per group and chromosome). | Time one chromosome. |

**Recent and competing work (search of 2024 to 2026 literature on 2026-11-26)**

- In maize, ARG-based maps and experimental populations showed a 12% genome-wide rise in recombination during domestication, with higher rates near centromeres on long arms ([Epstein et al. 2026](https://doi.org/10.1073/pnas.2534336123)). The wild-versus-domesticated comparison has a strong precedent; grape would add a perennial, clonally propagated case.

**What would end the idea, and the fallback.** If simulations show that LD maps for cultivated groups cannot be separated from demographic artefacts, the wild-versus-cultivated contrast fails. The fallback is a wild-only LD map compared with published genetic maps.

**Journal-level realism.** Mid-field genetics or evolution; the maize study in *PNAS* shows a higher venue is possible with a clear domestication contrast.

## Rough estimates

- Compute: medium [draft]
- Effort: 2–4 months for one person [draft]
- Target: genetics or evolution journal [draft]

## Suggested journal level (suggestion only)

**Mid-field journal (genetics or evolution).** Comparable plant recombination landscape papers read here appeared in *PLOS Genetics* and *Philosophical Transactions B*; grape genetic maps in *Theoretical and Applied Genetics*, *PLOS ONE* and *Nature Communications* (the latter for a new cross-species marker platform). An LD-based landscape for grape fits a mid-field venue. This is a suggestion, not a decision; impact factors are not used.

## Continue on HPC

Run each step as its own job, in this order. Every job writes `.DONE` or `.FAILED` and a log; the next step starts only after `.DONE`. Template and rules: [`docs/HPC_JOBS.md`](../../../../templates/HPC_JOBS.md).

| Order | Step | Main tools | Resources (rough) |
|---|---|---|---|
| 1 | [AM04](../../analyses/AM04-sample-identity/) Sample identity, clones and relatedness | PLINK 2, KING | 8 CPU, 32 GB |
| 2 | [AM26](../../analyses/AM26-phasing-polarisation-recombination/) Phasing | SHAPEIT5 | 16 CPU, 64 GB per chromosome; array |
| 3 | [AM14](../../analyses/AM14-ancestral-recombination-graph/) Population-size history | Relate | 8 CPU, 32 GB per chromosome |
| 4 | Simulation and rho_LD | msprime, pyrho or LDhelmet | 16 CPU, 64 GB per group and chromosome; array |

Public inputs: [DS10](../../data/DS10-reseq-472-vitis/), [DS12](../../data/DS12-reseq-204-magris2021/), [DS02](../../data/DS02-grapepan-v1/), [DS01](../../data/DS01-pn40024-references/).

## References

- Brazier et al. 2022. Diversity and determinants of recombination landscapes in flowering plants. *PLOS Genetics*. [doi:10.1371/journal.pgen.1010141](https://doi.org/10.1371/journal.pgen.1010141)
- Broman et al. 2003. R/qtl: QTL mapping in experimental crosses. *Bioinformatics*. [doi:10.1093/bioinformatics/btg112](https://doi.org/10.1093/bioinformatics/btg112)
- Chan et al. 2012. Genome-Wide Fine-Scale Recombination Rate Variation in Drosophila melanogaster. *PLoS Genetics*. [doi:10.1371/journal.pgen.1003090](https://doi.org/10.1371/journal.pgen.1003090)
- Delame et al. 2019. Introgression reshapes recombination distribution in grapevine interspecific hybrids. *Theoretical and Applied Genetics*. [doi:10.1007/s00122-018-3260-x](https://doi.org/10.1007/s00122-018-3260-x)
- Doligez et al. 2006. An integrated SSR map of grapevine based on five mapping populations. *Theoretical and Applied Genetics*. [doi:10.1007/s00122-006-0295-1](https://doi.org/10.1007/s00122-006-0295-1)
- Halldorsson et al. 2019. Characterizing mutagenic effects of recombination through a sequence-level genetic map. *Science*. [doi:10.1126/science.aau1043](https://doi.org/10.1126/science.aau1043)
- Hofmeister et al. 2023. Accurate rare variant phasing of whole-genome and whole-exome sequencing data in the UK Biobank. *Nature Genetics*. [doi:10.1038/s41588-023-01415-w](https://doi.org/10.1038/s41588-023-01415-w)
- Hyma et al. 2015. Heterozygous Mapping Strategy (HetMappS) for High Resolution Genotyping-By-Sequencing Markers: A Case Study in Grapevine. *PLOS ONE*. [doi:10.1371/journal.pone.0134880](https://doi.org/10.1371/journal.pone.0134880)
- Morales-Cruz et al. 2021. Introgression among North American wild grapes (Vitis) fuels biotic and abiotic adaptation. *Genome Biology*. [doi:10.1186/s13059-021-02467-z](https://doi.org/10.1186/s13059-021-02467-z)
- Speidel et al. 2019. A method for genome-wide genealogy estimation for thousands of samples. *Nature Genetics*. [doi:10.1038/s41588-019-0484-x](https://doi.org/10.1038/s41588-019-0484-x)
- Spence et al. 2019. Inference and analysis of population-specific fine-scale recombination maps across 26 diverse human populations. *Science Advances*. [doi:10.1126/sciadv.aaw9206](https://doi.org/10.1126/sciadv.aaw9206)
- Stapley et al. 2017. Variation in recombination frequency and distribution across eukaryotes: patterns and processes. *Philosophical Transactions of the Royal Society B: Biological Sciences*. [doi:10.1098/rstb.2016.0455](https://doi.org/10.1098/rstb.2016.0455)
- Vervalle et al. 2022. A high-density integrated map for grapevine based on three mapping populations genotyped by the Vitis18K SNP chip. *Theoretical and Applied Genetics*. [doi:10.1007/s00122-022-04225-6](https://doi.org/10.1007/s00122-022-04225-6)
- Zou et al. 2020. Haplotyping the Vitis collinear core genome with rhAmpSeq improves marker transferability in a diverse genus. *Nature Communications*. [doi:10.1038/s41467-019-14280-1](https://doi.org/10.1038/s41467-019-14280-1)
- Dapper et al. 2018. Effects of Demographic History on the Detection of Recombination Hotspots from Linkage Disequilibrium. *Molecular Biology and Evolution*. [doi:10.1093/molbev/msx272](https://doi.org/10.1093/molbev/msx272)
- Xiao et al. 2025. Impacts of reproductive systems on grapevine genome and breeding. *Nature Communications*. [doi:10.1038/s41467-025-56817-7](https://doi.org/10.1038/s41467-025-56817-7)
- Barroso et al. 2019. Inference of recombination maps from a single pair of genomes and its application to ancient samples. *PLOS Genetics*. [doi:10.1371/journal.pgen.1008449](https://doi.org/10.1371/journal.pgen.1008449)
- Fang et al. 2026. The heterozygous pineapple genome demonstrates the importance of haplotype-resolved plant genomes. *Horticulture Research*. [doi:10.1093/hr/uhag189](https://doi.org/10.1093/hr/uhag189)
- Epstein et al. 2026. Evolution of maize recombination landscape during domestication. *Proceedings of the National Academy of Sciences*. [doi:10.1073/pnas.2534336123](https://doi.org/10.1073/pnas.2534336123)
