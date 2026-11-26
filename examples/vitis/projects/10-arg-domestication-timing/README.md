# 10. Ancestral recombination graphs for hundreds of grape genomes and domestication timing

中文：数百样本级祖先重组图（ARG）与驯化定年

Rank 10 of 22 (score F 2 + N 3 + E 1 = 6; see docs/RANKING.md) · Tier: Large (E = 1, more than 4 months or a high-risk step) · Origin: continued: started earlier and restarted here from public data under a new preregistration · Status: draft v0.3.2, 2026-11-14

## Gap

ARG methods (Relate, tsinfer with tsdate, SINGER) have been applied to four grape genomes only. ARGs for hundreds of samples, used for domestication timing and allele ages, were not found.

**Existing work**

- [Srivastava et al. 2023](https://doi.org/10.1093/gbe/evad226): genealogies for four grape individuals.
- [Wang et al. 2026](https://doi.org/10.1073/pnas.2607754123): introgression in North American Vitis by coalescent composite likelihood, not an ARG.
- [Dong et al. 2023](https://doi.org/10.1126/science.add8655): dual domestication from 3,525 accessions.
- [Zhou et al. 2017](https://doi.org/10.1073/pnas.1709257114): domestication history from resequencing.

**How this project differs**

Uses hundreds of samples, simulation-based calibration that includes clonal propagation, polarisation with two or more outgroups, and time conversion that propagates uncertainty in the mutation rate and generation time.

**Background survey (literature read for this plan)**

Ancestral recombination graphs (ARGs) describe the local genealogies along the genome and give coalescence times and allele ages directly ([Nielsen et al. 2025](https://doi.org/10.1038/s41576-024-00772-4)). Scalable methods now exist: Relate estimates genome-wide genealogies for thousands of samples ([Speidel et al. 2019](https://doi.org/10.1038/s41588-019-0484-x)); tsinfer infers tree sequences for large datasets ([Kelleher et al. 2019](https://doi.org/10.1038/s41588-019-0483-y)) and, with tsdate, gave a unified genealogy of modern and ancient human genomes ([Wohns et al. 2022](https://doi.org/10.1126/science.abi8264)); SINGER samples ARGs from the posterior for hundreds of genomes ([Deng et al. 2025](https://doi.org/10.1038/s41588-025-02317-9)). Simulation benchmarks showed that coalescence-time accuracy differs between methods and must be checked for the setting at hand ([Brandt et al. 2022](https://doi.org/10.1093/genetics/iyac044)). msprime 1.0 ([Baumdicker et al. 2022](https://doi.org/10.1093/genetics/iyab229)) and SLiM 4 ([Haller and Messer 2023](https://doi.org/10.1086/723601)) can simulate the needed scenarios, including non-standard life histories.

Grape domestication history has been studied mostly with SFS and SMC methods. Resequencing inferred a protracted 22,000-year population decline before domestication and more deleterious heterozygous mutations in cultivars, partly due to clonal propagation ([Zhou et al. 2017](https://doi.org/10.1073/pnas.1709257114)), demographic history from 472 *Vitis* accessions ([Liang et al. 2019](https://doi.org/10.1038/s41467-019-09135-8)), and dual domestication from 3,525 accessions ([Dong et al. 2023](https://doi.org/10.1126/science.add8655)). Genealogies have been inferred for three Greek cultivars and one wild vine only ([Srivastava et al. 2023](https://doi.org/10.1093/gbe/evad226)). Introgression among North American *Vitis* was studied with coalescent composite likelihood, not an ARG ([Wang et al. 2026](https://doi.org/10.1073/pnas.2607754123)). Clonal propagation is a key feature of grape and of other clonal crops, and it changes the relation between years and sexual generations ([McKey et al. 2010](https://doi.org/10.1111/j.1469-8137.2010.03210.x)).

**Specific gap.** No ARG for hundreds of grape genomes was found, and no grape ARG study calibrated the methods by simulation that includes clonal propagation or propagated uncertainty in mutation rate and generation time into dates [待确认].

## Question

With calibration that accounts for clonal propagation, what do ARGs say about the timing of grape domestication and the ages of selected alleles?

## Hypotheses, planned figures and criteria

No results are given here. Each row says what would count as support; the exact thresholds go into the preregistration.

| Figure or table | Hypothesis or purpose | Criterion |
|---|---|---|
| Fig 1. Simulation calibration | Each ARG method recovers simulated split times under clonal propagation. | Metrics: bias, coverage of 95% intervals, and RMSE across a preregistered number of replicates per scenario; a method passes only if it meets the tolerance in every preregistered scenario. The method for Fig 2–3 is chosen from this figure before the real data are analysed. If no method passes, stop and publish the calibration as a methods paper. |
| Fig 2. Coalescence times between wild and cultivated groups | Single and multiple domestication scenarios make different predictions, written down before the run. | Simulation-based test: each scenario is simulated (SLiM + msprime) and run through the same pipeline (phasing, polarisation, inference); statistic = preregistered quantiles of the wild–cultivated cross-coalescence time distribution and the KS distance to each scenario; null distributions obtained from the simulations; observed uncertainty estimated by chromosome-block bootstrap; α and Holm correction across scenarios fixed in advance. Tests use μ-scaled times, so μ uncertainty does not enter the rejection decision; μ and g are applied only to convert results to years, with their uncertainty propagated via Monte Carlo. Reading table fixed in advance: both scenarios rejected = neither fits and no timing claim is made; neither rejected = the data cannot separate them; one rejected = the other is reported as consistent with the data, not as proven. |
| Fig 3. Ages of alleles at selected loci | Two expectations stated in advance: under a hard sweep from a new mutation, selected alleles are younger than matched neutral alleles; under selection on standing variation, they can be as old or older. | Selected loci fixed in advance from independent published scans, not from scans of these data; matched by frequency, recombination rate, callable fraction, and local tree count; two-sided test, with the pattern reported per locus. |
| Fig S1. Sensitivity | Conclusions hold across μ, g, sampling-time, somatic-filter, recombination-map, and outgroup choices. | Re-run with each alternative fixed in advance: μ and g at the ends of their intervals, earlier origin dates for documented old cultivars, a stricter somatic filter, a constant recombination rate, and *Muscadinia*-only polarisation. |

**Expected results and how they will be read**

- Fig 1 decides which ARG method is used: only a method that recovers simulated split times under clonal propagation within the preregistered error enters Fig 2 and Fig 3. If none passes, the paper becomes a methods report on why grape ARG dates are not yet reliable.
- Fig 2: cross-coalescence profiles between wild and cultivated groups are compared with the predictions written down for single and dual domestication; an outcome that fits neither is reported as such.
- Fig 3: allele ages at published selected loci are read against the two preregistered expectations (new mutation versus standing variation); all dates carry Monte Carlo intervals for μ and g.
- Fig S1 shows which conclusions depend on μ, g, sampling, somatic filter, recombination map and outgroup choice.

## Preregistration

Before any data are analysed, fill in [`docs/PREREGISTRATION.md`](../../../../templates/PREREGISTRATION.md) for this project: hypotheses, primary outcome, sample inclusion rules, thresholds, stop rules and what will be reported if a hypothesis fails. Commit it with a date. Criteria from any earlier attempt are reference only and are not carried over.

## Data

| Module | Dataset |
|---|---|
| [DS10](../../data/DS10-reseq-472-vitis/) | Resequencing of 472 Vitis accessions (and the 2017 domestication panel) |
| [DS11](../../data/DS11-reseq-3525-dong2023/) | Resequencing of 3,525 grapevine accessions (Dong et al. 2023) |
| [DS12](../../data/DS12-reseq-204-magris2021/) | Resequencing of 204 V. vinifera accessions (Magris et al. 2021) |
| [DS08](../../data/DS08-muscadinia-genomes/) | Muscadinia rotundifolia assemblies and reads |
| [DS04](../../data/DS04-na-vitis-super-pangenome/) | North American Vitis super-pangenome and wild resequencing |
| [DS06](../../data/DS06-vitis-amurensis-pangenome/) | Vitis amurensis haplotype assemblies and 330-sample resequencing |
| [DS01](../../data/DS01-pn40024-references/) | PN40024 references: PN_T2T (v5), PN40024.v4 and 12X |

**How each dataset is used**

| Module | Role in this project |
|---|---|
| DS10, DS11, DS12 | Wild and cultivated *V. vinifera* panels; one sample per clone group from project 08 |
| DS04, DS06, DS08 | Outgroups for polarisation (North American and East Asian *Vitis*, *Muscadinia*) |
| DS01 | PN_T2T coordinates and masks |

New public data: none needed. Published linkage maps for recombination are listed in AM26 and project 24 [待确认: which map is interpolated].

## Analysis steps

Shared modules, in order:

1. [AM01 · Download and verify](../../analyses/AM01-download-and-verify/)
2. [AM04 · Sample identity, clones and relatedness](../../analyses/AM04-sample-identity/)
3. [AM03 · Short-read mapping and small-variant calling](../../analyses/AM03-short-read-variants/)
4. [AM26 · Phasing, ancestral states and recombination rates](../../analyses/AM26-phasing-polarisation-recombination/)
5. [AM14 · Ancestral recombination graphs and allele age](../../analyses/AM14-ancestral-recombination-graph/)

Project-specific steps:

- Select samples using a preregistered rule before mapping: run AM04 on existing public genotypes, retain one sample per clone group (highest depth), and select several hundred samples balanced by group and depth; record the panel as a covariate; estimate CPU hours and storage.
- Call variants (AM03), then re-run AM04 (KING) on the new calls to deduplicate and verify sample labels against the public genotypes before phasing. Filter suspected somatic or layer-specific variants: heterozygous calls observed in a single sample with allele balance outside a preregistered window are removed; the sequenced tissue is recorded.
- Phase with SHAPEIT5 and polarise with est-sfs using *Muscadinia* plus a North American or East Asian *Vitis* outgroup aligned to PN_T2T with the outgroup settings in AM26; report the polarisation error.
- Recombination: use published linkage maps interpolated to PN_T2T by default; use LD-based rates (pyrho) only as an input to the ARG, and run a constant-rate check (AM26).
- Calibrate by simulation (AM14): use SLiM for clonal generations, recapitated with msprime, using custom grape parameters with written sources.
- Infer ARGs using the method chosen in Fig 1 and date alleles.
- Fix μ and g before the run: set μ as an interval spanning the per-generation rates used in published grape demographic studies (Zhou et al. 2017; Liang et al. 2019) [待确认: values and their primary sources]; set g as an interval of years per generation from the same literature [待确认]. Propagate both uncertainties by Monte Carlo into every time estimate.
- Run the sensitivity set (Fig S1).

**Stepwise work plan with tools**

| Step | Work | Tools (paper) | Output |
|---|---|---|---|
| 1 | Preregistered sample selection from public genotypes; one sample per clone group | KING, PLINK 2 (AM04) | Sample list |
| 2 | Call variants on PN_T2T; re-check identity; filter likely somatic calls | DeepVariant or GATK (AM03) | Filtered VCF |
| 3 | Phase; polarise with two or more outgroups | SHAPEIT5 ([Hofmeister et al. 2023](https://doi.org/10.1038/s41588-023-01415-w)), est-sfs (AM26) | Phased, polarised VCF |
| 4 | Recombination map from published linkage maps interpolated to PN_T2T | AM26 | Map file |
| 5 | Simulate grape-like histories with clonal generations; benchmark Relate, tsinfer+tsdate and SINGER | SLiM 4, msprime (AM14) | Fig 1 |
| 6 | Infer ARGs with the chosen method; cross-coalescence and allele ages | chosen ARG tool (AM14) | Fig 2, Fig 3 |
| 7 | Monte Carlo over μ and g; sensitivity set | R or Python | Fig S1 |

## Paper design and split

| Paper | Working title | Type | Figures |
|---|---|---|---|
| K1 | Calibrating ARG methods for a clonally propagated crop | methods paper (fallback if dating fails) | Fig 1 |
| K2 | Domestication timing and allele ages in grape from ARGs | main paper | Fig 2–3, Fig S1 |

Each paper: introduction from the gap above; one results section per figure; methods with tool versions from the modules; data availability listing every accession used and the derived tables.

## Risks and novelty check

- Risk: Calibration may fail, in which case a methods-only paper is the fallback.
- Risk: μ and g are uncertain and dominate the uncertainty of dates in years; intervals, rather than point values, are reported.
- Risk: Most cultivars have no known origin date; contemporaneous sampling is assumed by default [待确认: support for non-contemporaneous samples in tsdate and Relate].
- Risk: A single *Muscadinia* outgroup is deeply diverged; polarisation errors would inflate allele ages, so it is never used alone.
- Risk: Population recombination maps are not a product of this project.
- Risk: Novelty is judged within grape; whether ARG-based domestication dating with hundreds of samples exists in other crops has not been checked [待确认].
- Novelty: checked against the existing work above (Crossref-verified DOIs). Repeat the search before writing; anything marked [待确认] is not yet verified.

## Risks and how to handle them

Added 2026-11-26. Each row names a risk, the evidence behind it, and a concrete check or fallback. Sources cited here were read for this section and their DOIs were checked on Crossref; preprints are marked.

| Area | Risk | Check or mitigation |
|---|---|---|
| Data access and licence | Runs of the 3,525-accession panel (DS11) were blocked on the public listing check ([data/DOWNLOADS.md](../../data/DOWNLOADS.md)); INSDC panels (DS10, DS12) are open ([INSDC 2024](https://doi.org/10.1093/nar/gkae1058)). | Plan sample sizes on INSDC panels only; add DS11 only if access is obtained. |
| Clonal propagation and generation time | Vegetative propagation was in use by the mid-Iron Age, and one medieval pip was identical to modern Pinot noir, about 600 years of clonal continuity ([Noraz et al. 2026](https://doi.org/10.1038/s41467-026-70166-z)). Cloning raises heterozygosity and gives a double U-shaped site frequency spectrum ([Xiao et al. 2025](https://doi.org/10.1038/s41467-025-56817-7)). Calendar years then map poorly onto sexual generations. | Date wild lineages separately; treat each cultivar as sampled at its sexual origin; report dates across a range of generation times rather than one value. |
| Tree shape | ARG methods (SINGER, Relate, tsinfer) lose accuracy as genealogies become imbalanced, as under positive selection or skewed reproductive success ([Pouyet et al. 2026](https://doi.org/10.1093/gbe/evag215)); widespread use of a few elite parents may produce such imbalance. | Simulate data with imbalanced genealogies matched to grape and measure date bias before reading real dates. |
| Phasing errors | Four ARG methods degraded only slightly with computational phasing under the demographies tested ([Wang et al. 2025](https://doi.org/10.1101/2025.11.24.690249), preprint). | Still test on T2T haplotypes as phase truth: compare dates from true phase and from statistical phase. |
| Reference bias and genome choice | The choice of reference changes outlier windows even when genome-wide summaries agree ([Thorburn et al. 2023](https://doi.org/10.1111/1755-0998.13838)). | Repeat selected-allele ages on a second reference (PN40024.v4 or a wild haplotype). |
| Pooling across studies | Panels differ in depth and calling. | Joint calling from raw reads; exclude sites with panel-specific missingness. |
| Clones, synonyms and pedigree | Duplicate genotypes act as identical haplotypes and distort ARG branch lengths. | Use one sample per genotype (project 08). |
| Computing cost | SINGER samples genealogies by Bayesian inference for hundreds of genomes ([Deng et al. 2025](https://doi.org/10.1038/s41588-025-02317-9)); its run time on grape data is unknown. | Run Relate or tsinfer on all chromosomes first; run SINGER on two chromosomes for comparison. |

**Recent and competing work (search of 2024 to 2026 literature on 2026-11-26)**

- ARG inference has been used in maize and teosinte to build recombination maps and to show a 12% genome-wide rise in recombination during domestication ([Epstein et al. 2026](https://doi.org/10.1073/pnas.2534336123)). ARGs in crop domestication are therefore not new; a grape ARG with clonal calibration is.
- Ancient DNA now gives direct dates for domesticated grapes in France by about 625 to 500 BCE ([Noraz et al. 2026](https://doi.org/10.1038/s41467-026-70166-z)). These dates are an external check on any ARG-based timing.

**What would end the idea, and the fallback.** If dates under plausible mutation rates and generation times span most of the Holocene, the timing question has no answer. The fallback is the methods-only paper on calibration under clonal propagation (see above).

**Journal-level realism.** Mid-field genetics or molecular evolution. Ancient DNA results already constrain timing, so a broad venue would need ARG dates that add something the archaeological record cannot.

## Reference study in another species

Added 2026-11-26. Published studies that already did this kind of work in another species, to plan the grape version against. Every DOI was checked on Crossref. Figures are described, not copied; a figure redrawn for a grape paper would be marked "Redrawn after" its source. The last bullet for each study lists what a grape results section would need; it is a planning suggestion, not a finding of that study.

### Speidel et al. 2019

- **Paper:** [Speidel et al. 2019](https://doi.org/10.1038/s41588-019-0484-x), *Nature Genetics*.
- **Species:** Human (1000 Genomes).
- **What was done:** The Relate method estimates genome-wide genealogies for thousands of samples and was used to estimate population sizes, split times, the evolution of mutation rates and selection.
- **Figures:** Fig. 1 method overview; Fig. 2 run time and accuracy in simulations; Fig. 3 population sizes and split times; Fig. 4 mutation-rate evolution and evidence of introgression; Fig. 5 tests of selection; Fig. 6 selection on traits (full text read from the author manuscript in PubMed Central).
- **What a grape results section would need:** ARG inference with quality control; effective population size through time; split and domestication times; allele ages; selection tests.

### Kelleher et al. 2019

- **Paper:** [Kelleher et al. 2019](https://doi.org/10.1038/s41588-019-0483-y), *Nature Genetics*.
- **Species:** Human (global and UK samples).
- **What was done:** tsinfer infers tree sequences in large datasets and was used to describe structure in global and UK populations.
- **Figures:** Fig. 1 tree sequences compared with conventional variant storage; Fig. 2 main steps of the inference; Fig. 3 accuracy of ancestor inference in simulations; Fig. 4 global diversity described by genealogical nearest neighbours; Fig. 5 UK Biobank.
- **What a grape results section would need:** tree-sequence inference with an accuracy check; genealogical nearest-neighbour structure; allele ages with tsdate.

### Lu et al. 2022

- **Paper:** [Lu et al. 2022](https://doi.org/10.1186/s12284-022-00556-6), *Rice* (PMC8847465). Licence CC BY 4.0: figures may be reused with credit; none are copied here.
- **Species:** Asian rice and its wild relatives.
- **What was done:** gene genealogy-based mutation analysis of 101 genes on 12 chromosomes split rice history into two phases; 91 mutations predated the *indica* and *japonica* split; positive selection involved 22 loci; genealogies at some genes supported a hybrid origin.
- **Figures:** Fig. 1 positions of early mutations; Fig. 2 functional analysis and a gene genealogy; Fig. 3 flow of parental genes into rice and gene types; Fig. 4 genealogies of recombinant alleles.
- **What its results section needed:** mutations placed on genealogies relative to the population split, and genealogies at known domestication genes.
- **Grape version and limits:** a title search of open-access records in Europe PMC on 2026-11-26 found no crop study that dates domestication with genome-wide ARGs; the rice study uses per-gene genealogies. The grape version adds genome-wide ARGs, but the dating must pass the calibration check in the risk table above; genealogies at known grape domestication genes are the Fig. 2 and 4 equivalents.

### Q1-level bar

Target: a first-quartile (Q1) journal in plant science, genetics or evolution. Quartile lists change each year, so the journal is chosen from the current list at submission [to confirm]. To compete at that level, the grape paper needs: dates calibrated in a way that handles clonal propagation, checked against ancient DNA or historical records, and selection tests on the genealogies, compared with the published domestication models.

## Rough estimates

- Compute: large [draft]
- Effort: 4–6 months for one person [draft]
- Target: genetics or evolution journal [draft]

## Suggested journal level (suggestion only)

**Mid-field journal (genetics or molecular evolution); broad-interest only if the result changes the domestication picture.** Grape domestication papers read here appeared in *PNAS*, *Nature Communications* and *Science*, and the only grape genealogy study in *Genome Biology and Evolution*; ARG method papers appeared in *Nature Genetics*, *Genetics* and *Science*. A calibrated grape ARG with sensitivity analysis fits a mid-field venue; a broad one needs a clear new answer on timing. This is a suggestion, not a decision; impact factors are not used.

## Continue on HPC

Run each step as its own job, in this order. Every job writes `.DONE` or `.FAILED` and a log; the next step starts only after `.DONE`. Template and rules: [`docs/HPC_JOBS.md`](../../../../templates/HPC_JOBS.md).

| Order | Step | Main tools | Resources (rough) |
|---|---|---|---|
| 1 | [AM01](../../analyses/AM01-download-and-verify/) Download selected runs | ENA FTP, md5sum | 1–4 CPU, 4 GB, network node; array over files |
| 2 | [AM04](../../analyses/AM04-sample-identity/) Sample selection on public genotypes | plink2, KING | 8 CPU, 32 GB, < 2 h |
| 3 | [AM03](../../analyses/AM03-short-read-variants/) Mapping and calling | bwa-mem2, DeepVariant, GLnexus | 16 CPU, 64 GB, 6–24 h per sample (DeepVariant); joint step 32 CPU, 128 GB |
| 4 | [AM04](../../analyses/AM04-sample-identity/) Identity check and deduplication on the new calls | plink2, KING | 8 CPU, 32 GB, < 2 h |
| 5 | [AM26](../../analyses/AM26-phasing-polarisation-recombination/) Outgroup alignment and per-site outgroup bases | minimap2, paftools.js | 8–16 CPU, 32 GB per outgroup haplotype |
| 6 | [AM26](../../analyses/AM26-phasing-polarisation-recombination/) Phasing, ancestral states, recombination input | SHAPEIT5, est-sfs, pyrho | 8–16 CPU, 32–64 GB per chromosome; est-sfs single-threaded, hours per chromosome |
| 7 | [AM14](../../analyses/AM14-ancestral-recombination-graph/) Simulation calibration (Fig 1) | SLiM, pyslim, msprime, stdpopsim | SLiM 1 CPU, 8–32 GB per replicate; array over replicates |
| 8 | [AM14](../../analyses/AM14-ancestral-recombination-graph/) ARG inference and dating | tsinfer, tsdate, Relate, SINGER | 16 CPU, 64 GB per chromosome; long walltime; SINGER run time for several hundred samples measured on a pilot first [待确认] |

Public inputs: [DS10](../../data/DS10-reseq-472-vitis/), [DS11](../../data/DS11-reseq-3525-dong2023/), [DS12](../../data/DS12-reseq-204-magris2021/), [DS08](../../data/DS08-muscadinia-genomes/), [DS04](../../data/DS04-na-vitis-super-pangenome/), [DS06](../../data/DS06-vitis-amurensis-pangenome/), [DS01](../../data/DS01-pn40024-references/).

## References

- Srivastava et al. 2023. Genealogical Analyses of 3 Cultivated and 1 Wild Specimen of Vitis vinifera from Greece. *Genome Biology and Evolution*. [doi:10.1093/gbe/evad226](https://doi.org/10.1093/gbe/evad226)
- Wang et al. 2026. The dynamics of introgression and parallel adaptation across North American Vitis species. *Proceedings of the National Academy of Sciences*. [doi:10.1073/pnas.2607754123](https://doi.org/10.1073/pnas.2607754123)
- Dong et al. 2023. Dual domestications and origin of traits in grapevine evolution. *Science*. [doi:10.1126/science.add8655](https://doi.org/10.1126/science.add8655)
- Zhou et al. 2017. Evolutionary genomics of grape ( Vitis vinifera ssp. vinifera ) domestication. *Proceedings of the National Academy of Sciences*. [doi:10.1073/pnas.1709257114](https://doi.org/10.1073/pnas.1709257114)
- Baumdicker et al. 2022. Efficient ancestry and mutation simulation with msprime 1.0. *Genetics*. [doi:10.1093/genetics/iyab229](https://doi.org/10.1093/genetics/iyab229)
- Brandt et al. 2022. Evaluation of methods for estimating coalescence times using ancestral recombination graphs. *Genetics*. [doi:10.1093/genetics/iyac044](https://doi.org/10.1093/genetics/iyac044)
- Deng et al. 2025. Robust and accurate Bayesian inference of genome-wide genealogies for hundreds of genomes. *Nature Genetics*. [doi:10.1038/s41588-025-02317-9](https://doi.org/10.1038/s41588-025-02317-9)
- Haller et al. 2023. SLiM 4: Multispecies Eco-Evolutionary Modeling. *The American Naturalist*. [doi:10.1086/723601](https://doi.org/10.1086/723601)
- Hofmeister et al. 2023. Accurate rare variant phasing of whole-genome and whole-exome sequencing data in the UK Biobank. *Nature Genetics*. [doi:10.1038/s41588-023-01415-w](https://doi.org/10.1038/s41588-023-01415-w)
- Kelleher et al. 2019. Inferring whole-genome histories in large population datasets. *Nature Genetics*. [doi:10.1038/s41588-019-0483-y](https://doi.org/10.1038/s41588-019-0483-y)
- Liang et al. 2019. Whole-genome resequencing of 472 Vitis accessions for grapevine diversity and demographic history analyses. *Nature Communications*. [doi:10.1038/s41467-019-09135-8](https://doi.org/10.1038/s41467-019-09135-8)
- McKey et al. 2010. The evolutionary ecology of clonally propagated domesticated plants. *New Phytologist*. [doi:10.1111/j.1469-8137.2010.03210.x](https://doi.org/10.1111/j.1469-8137.2010.03210.x)
- Nielsen et al. 2025. Inference and applications of ancestral recombination graphs. *Nat Rev Genet*. [doi:10.1038/s41576-024-00772-4](https://doi.org/10.1038/s41576-024-00772-4)
- Speidel et al. 2019. A method for genome-wide genealogy estimation for thousands of samples. *Nature Genetics*. [doi:10.1038/s41588-019-0484-x](https://doi.org/10.1038/s41588-019-0484-x)
- Wohns et al. 2022. A unified genealogy of modern and ancient genomes. *Science*. [doi:10.1126/science.abi8264](https://doi.org/10.1126/science.abi8264)
- INSDC 2024. The international nucleotide sequence database collaboration (INSDC): enhancing global participation. *Nucleic Acids Research*. [doi:10.1093/nar/gkae1058](https://doi.org/10.1093/nar/gkae1058)
- Noraz et al. 2026. Ancient DNA reveals 4000 years of grapevine diversity, viticulture and clonal propagation in France. *Nature Communications*. [doi:10.1038/s41467-026-70166-z](https://doi.org/10.1038/s41467-026-70166-z)
- Xiao et al. 2025. Impacts of reproductive systems on grapevine genome and breeding. *Nature Communications*. [doi:10.1038/s41467-025-56817-7](https://doi.org/10.1038/s41467-025-56817-7)
- Pouyet et al. 2026. Comparing ARG Inference Methods Under Transmission of Reproductive Success: Tree Imbalance Matters. *Genome Biology and Evolution*. [doi:10.1093/gbe/evag215](https://doi.org/10.1093/gbe/evag215)
- Wang et al. 2025. Robustness of Ancestral Recombination Graph Inference Tools to Phasing Errors. *bioRxiv* (preprint). [doi:10.1101/2025.11.24.690249](https://doi.org/10.1101/2025.11.24.690249)
- Thorburn et al. 2023. Origin matters: Using a local reference genome improves measures in population genomics. *Molecular Ecology Resources*. [doi:10.1111/1755-0998.13838](https://doi.org/10.1111/1755-0998.13838)
- Epstein et al. 2026. Evolution of maize recombination landscape during domestication. *Proceedings of the National Academy of Sciences*. [doi:10.1073/pnas.2534336123](https://doi.org/10.1073/pnas.2534336123)
- Lu et al. 2022. Early Domestication History of Asian Rice Revealed by Mutations and Genome-Wide Analysis of Gene Genealogies. *Rice*. [doi:10.1186/s12284-022-00556-6](https://doi.org/10.1186/s12284-022-00556-6)
