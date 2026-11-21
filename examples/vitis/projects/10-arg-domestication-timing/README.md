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

## Rough estimates

- Compute: large [draft]
- Effort: 4–6 months for one person [draft]
- Target: genetics or evolution journal [draft]

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
