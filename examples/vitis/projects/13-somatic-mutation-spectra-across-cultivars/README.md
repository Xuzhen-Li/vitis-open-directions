# 13. Somatic mutation spectra across grape cultivars, with rates where clone dates are known

中文：跨品种体细胞突变谱（有日期时估速率）

Rank 13 of 22 (score F 2 + N 2 + E 2 = 6; see docs/RANKING.md) · Tier: Medium (E = 2, effort range ending after 6 weeks and by 4 months) · Origin: continued: started earlier and restarted here from public data under a new preregistration · Status: draft v0.3.2, 2026-11-14

## Gap

Multi-clone somatic variation has been studied within single cultivars, most extensively in 23 Pinot noir clones. No comparison of mutation spectra across cultivars using a single pipeline was found, and no per-year somatic mutation rate for grape was found in our search [待确认]. Clone-specific SVs reported for Pinot noir lie mostly in repeat and centromere regions, so mapping artefacts must be excluded before any spectrum is built.

**Existing work**

- [Vondras et al. 2019](https://doi.org/10.1186/s12864-019-6211-2): 15 Zinfandel clones.
- [Callipo et al. 2026](https://doi.org/10.1186/s13059-026-04184-x): 23 Pinot noir clones on a phased reference (67,277 SNPs among clones); clone SVs sit mostly in repeat and centromere regions.
- [Zdunić et al. 2026](https://doi.org/10.1186/s12870-026-10110-x): eight Tribidrag clones.
- [Roach et al. 2018](https://doi.org/10.1371/journal.pgen.1007807): Chardonnay clone population.
- [Sichel et al. 2023](https://doi.org/10.1186/s12864-023-09453-8): L1/L2 chimera in Merlot found by comparing roots and leaves.
- [Xiao et al. 2025](https://doi.org/10.1038/s41467-025-56817-7): reproductive systems and the grape genome; whether it analyses somatic variants among Pinot noir clones [待确认].
- [Liang et al. 2019](https://doi.org/10.1038/s41467-019-09135-8): uses an assumed per-generation (germline) mutation rate for demography; not a somatic estimate [待确认].

**How this project differs**

Re-calls all public clone panels with one pipeline, one reference, and the same masks; counts only new alleles, reports loss of heterozygosity separately, uses the clone as the unit of analysis, and gives a rate only as an upper bound where clone dates are documented.

**Background survey (literature read for this plan)**

Somatic mutation in long-lived plants is the raw material of clonal sports. Few fixed somatic mutations were found in a long-lived oak ([Schmid-Siegert et al. 2017](https://doi.org/10.1038/s41477-017-0066-9)); a phylogenomic method found a low somatic rate in a large *Eucalyptus melliodora* tree ([Orr et al. 2020](https://doi.org/10.1098/rspb.2019.2364)); and genetic and epigenetic somatic rates were estimated in a wild *Populus trichocarpa* ([Hofmeister et al. 2020](https://doi.org/10.1186/s13059-020-02162-5)). In apricot, more than 90% of somatic mutations were specific to one meristem layer ([Goel et al. 2024](https://doi.org/10.1186/s13059-024-03337-0)), so tissue choice decides what is seen. Mutational signatures, as developed in cancer genomics, give a framework for comparing spectra ([Alexandrov et al. 2013](https://doi.org/10.1038/nature12477)).

Grape clones have been studied within cultivars: 15 Zinfandel clones ([Vondras et al. 2019](https://doi.org/10.1186/s12864-019-6211-2)), a Chardonnay clone population that also showed ancestral inbreeding ([Roach et al. 2018](https://doi.org/10.1371/journal.pgen.1007807)), an L1/L2 chimera in Merlot ([Sichel et al. 2023](https://doi.org/10.1186/s12864-023-09453-8)), Tempranillo Tinto clones traced by somatic variants ([Tello et al. 2025](https://doi.org/10.1093/hr/uhaf237)), eight Tribidrag clones ([Zdunić et al. 2026](https://doi.org/10.1186/s12870-026-10110-x)) and 23 Pinot noir clones on a phased reference ([Callipo et al. 2026](https://doi.org/10.1186/s13059-026-04184-x)). Structural sports such as colour loss come from large rearrangements ([Carbonell-Bejerano et al. 2017](https://doi.org/10.1104/pp.17.00715)), and transposable elements are a major cause of somatic polymorphism in Pinot ([Carrier et al. 2012](https://doi.org/10.1371/journal.pone.0032973)).

**Specific gap.** Each grape study used its own pipeline, reference and filters. No comparison of somatic spectra across cultivars with one pipeline, one reference and the same masks was found, and no per-year upper bound on the grape somatic rate from documented clone dates [待确认].

## Question

Once artefact-prone regions are masked and loss of heterozygosity is separated, do somatic mutation spectra differ between grape cultivars, and what upper bound do documented clone dates place on the somatic mutation rate?

## Hypotheses, planned figures and criteria

No results are given here. Each row says what would count as support; the exact thresholds go into the preregistration.

| Figure or table | Hypothesis or purpose | Criterion |
|---|---|---|
| Fig 1. Artefact audit | A large share of raw clone-specific calls fall in low-mappability, repeat or centromere regions. | Share reported before and after masking; what counts as 'large' is fixed in advance; spectra use masked calls only. Thresholds are fixed in the preregistration before any data are analysed. |
| Fig 2. What counts as a somatic mutation | Method figure: new alleles vs loss of heterozygosity vs layer effects. | The clone used for a public phased assembly is one tip of the clone tree, not the ancestor: where its reads are public, it is re-called together with the other clones. The starting genotype at each site is the state shared by all clones, including the assembled clone, and the direction of change is set by parsimony with at least three clones per cultivar; for cultivars without a phased assembly, the starting genotype is the consensus of all clones. At variable sites, distinguishing LOH in one clone from a new mutation shared by several clones requires a rooted clone tree: root it with parental genotypes where they are public (for example Gouais blanc, a parent of Chardonnay), and call LOH as runs of consecutive germline heterozygous sites that become homozygous, by segment rather than site by site, since new mutations occur at isolated sites. Only new alleles, absent from the starting genotype and present in some clones, count as mutations. A state seen only in the assembly and in no sequenced clone is listed as unpolarised and is not counted as LOH. LOH (a starting heterozygous site that is homozygous in some clones) is reported as its own class; VAF window set from the tissue, because a variant in one cell layer has a VAF of about 0.5 × that layer's share of cells; layer displacement is listed as a source of false gain or loss. |
| Fig 3. Spectra by cultivar | Cultivars share one spectrum (null). | Unit: clone. Primary test: multinomial logit mixed model with cultivar as a fixed effect and clone as a random effect within the four-cultivar panel PRJNA847341; a clone-level permutation of the same contrast serves as the sensitivity analysis. Across studies there are fewer than five study levels and they are nearly collinear with cultivar, so study enters as a fixed effect and cross-study contrasts are descriptive; counts are normalised to the trinucleotide composition of each cultivar's callable region; all clones are down-sampled to a common depth. Cultivar and study cannot be separated across studies, so those differences are reported as cultivar × study. Pairwise comparisons corrected by BH within the family of all cultivar pairs × classes. Minimum clones and mutations per cultivar fixed in advance; below them, descriptive only. |
| Fig 4. Upper bound on the somatic rate | Somatic mutations accumulate with time since clones diverged. | Branch lengths of the clone tree (new alleles only, with LOH events excluded, per callable bp, corrected for sensitivity from in-silico spike-ins, with an intercept for false positives) regressed on time; clone-level block bootstrap; date uncertainty handled by interval sampling. Documented selection or registration dates are a lower bound on divergence time, so the rate is an upper bound unless the source gives the propagation lineage. Per-year or per-generation units fixed in advance [待确认]. Minimum number of independent branches (not clone pairs) fixed in advance; below it, counts only. |
| Table 1. Per-clone call sets | Resource table. | Calls, LOH table, masks, callable bp, and depth thresholds released. |

**Expected results and how they will be read**

- Fig 1: the share of raw clone-specific calls in low-mappability, repeat or centromere regions shows how much published counts depend on masking.
- Fig 3: if cultivars share one spectrum (null not rejected), grape somatic mutation is described by one process; if spectra differ, cultivar or tissue effects are tested next, with layer effects kept in mind.
- Fig 4 gives an upper bound only; it is not a rate estimate, because clone dates are approximate and callable fractions differ.
- Table 1 releases per-clone call sets with callable bp and sensitivity.

## Preregistration

Before any data are analysed, fill in [`docs/PREREGISTRATION.md`](../../../../templates/PREREGISTRATION.md) for this project: hypotheses, primary outcome, sample inclusion rules, thresholds, stop rules and what will be reported if a hypothesis fails. Commit it with a date. Criteria from any earlier attempt are reference only and are not carried over.

## Data

| Module | Dataset |
|---|---|
| [DS13](../../data/DS13-clone-somatic-variation/) | Clone resequencing across cultivars (Zinfandel, Chardonnay, Pinot noir, Malbec, Merlot and others) |
| [DS01](../../data/DS01-pn40024-references/) | PN40024 references: PN_T2T (v5), PN40024.v4 and 12X |
| [DS02](../../data/DS02-grapepan-v1/) | Grapepan v1.0: T2T haplotypes, graphs and a 466-accession resequencing panel |

**How each dataset is used**

| Module | Role in this project |
|---|---|
| DS13 | Clone resequencing across cultivars (Zinfandel, Chardonnay, Pinot noir, Merlot and others) |
| DS01 | PN_T2T as the single reference and source of masks |
| DS02 | Pangenome haplotypes for phased checks where a cultivar is assembled |

New public data: none needed. The Tribidrag and Tempranillo clone runs must be checked for public accessions before inclusion [待确认].

## Analysis steps

Shared modules, in order:

1. [AM01 · Download and verify](../../analyses/AM01-download-and-verify/)
2. [AM02 · Read QC and trimming](../../analyses/AM02-read-qc/)
3. [AM03 · Short-read mapping and small-variant calling](../../analyses/AM03-short-read-variants/)
4. [AM04 · Sample identity, clones and relatedness](../../analyses/AM04-sample-identity/)
5. [AM20 · Somatic variants among clones and mutation spectra](../../analyses/AM20-somatic-variants/)

Project-specific steps:

- Assemble the clone list from DS13 and confirm identity with AM04; keep cultivars with at least three clones for directional calls.
- Map all clones to PN_T2T (one reference for all cultivars); treat the clone used for a public phased assembly as one more tip and re-call it from its reads where they are public; take the starting genotype as the state shared by all clones (or the consensus of all clones where no phased assembly exists).
- Build masks (GenMap mappability, repeats, centromeres) before calling.
- Call somatic variants among clones (AM20); root the clone tree with public parental genotypes where available; separate new alleles, LOH (called by segment), and unpolarised assembly-only states; re-genotype across clones; estimate callable bp and sensitivity.
- Build normalised spectra; fit the clone-level model; run the within-study test on PRJNA847341.
- Collect documented clone dates from the source papers [待确认]; estimate the rate only as an upper bound.

**Stepwise work plan with tools**

| Step | Work | Tools (paper) | Output |
|---|---|---|---|
| 1 | Clone list from DS13; identity check | AM01, AM04 | Clone table |
| 2 | Masks: mappability, repeats, centromeres | GenMap, RepeatMasker, AM10 | Mask BED |
| 3 | Map all clones to PN_T2T; trim and QC | bwa-mem2 (AM02, AM03) | BAMs |
| 4 | Call somatic variants among clones; separate new alleles from LOH | AM20 tools | Call sets |
| 5 | Callable bp and sensitivity by spike-in or downsampling | custom | Callable table |
| 6 | Normalised spectra; clone-level model; signature extraction | SigProfiler-type NMF, R | Fig 3 |
| 7 | Upper bound from documented clone dates | R | Fig 4 |

## Paper design and split

| Paper | Working title | Type | Figures |
|---|---|---|---|
| E1 | Somatic mutation spectra across grape cultivars | main paper | Fig 1–3, Table 1 |
| E2 | An upper bound on the somatic mutation rate in grape from dated clones | short paper, only if enough dated independent branches | Fig 4 |

Each paper: introduction from the gap above; one results section per figure; methods with tool versions from the modules; data availability listing every accession used and the derived tables.

## Risks and novelty check

- Risk: Leaf DNA mixes L1- and L2-derived cells: variants in one layer remain detectable at a VAF below 0.5, but telling which layer carries them requires root and leaf samples (Merlot example); layer displacement can mimic gain or loss.
- Risk: Cultivar and study are confounded outside the four-cultivar panel.
- Risk: Sequencing depth differs between studies; downsample to a common depth.
- Risk: Clone dates may be undocumented; the rate paper runs only when enough dated, independent branches are available.
- Novelty: checked against the existing work above (Crossref-verified DOIs). Repeat the search before writing; anything marked [待确认] is not yet verified.

## Rough estimates

- Compute: medium [draft]
- Effort: 2–3 months for one person [draft]
- Target: genome or evolution journal [draft]

## Suggested journal level (suggestion only)

**Mid-field journal (genome biology or evolution).** Grape clone studies read here appeared in *BMC Genomics*, *PLOS Genetics*, *BMC Plant Biology*, *Horticulture Research* and *Genome Biology*; plant somatic-rate studies in *Nature Plants*, *Genome Biology* and *Proc R Soc B*. A cross-cultivar spectrum comparison with an artefact audit fits a mid-field venue. This is a suggestion, not a decision; impact factors are not used.

## Continue on HPC

Run each step as its own job, in this order. Every job writes `.DONE` or `.FAILED` and a log; the next step starts only after `.DONE`. Template and rules: [`docs/HPC_JOBS.md`](../../../../templates/HPC_JOBS.md).

| Order | Step | Main tools | Resources (rough) |
|---|---|---|---|
| 1 | [AM01](../../analyses/AM01-download-and-verify/) Download and verify | ncbi-datasets-cli, sra-tools, ENA FTP / Aspera | 1–4 CPU, 4 GB, network; array over files |
| 2 | [AM02](../../analyses/AM02-read-qc/) Read QC and trimming | fastp, MultiQC, seqkit | 8 CPU, 16 GB, 1–2 h per run; array over runs |
| 3 | [AM03](../../analyses/AM03-short-read-variants/) Short-read mapping and small-variant calling | bwa-mem2, samtools, DeepVariant | 16 CPU, 64 GB, 6–24 h per sample (DeepVariant); joint step 32 CPU, 128 GB |
| 4 | [AM04](../../analyses/AM04-sample-identity/) Sample identity, clones and relatedness | plink2, KING, VIVC | 8 CPU, 32 GB, < 2 h |
| 5 | [AM20](../../analyses/AM20-somatic-variants/) Somatic variants among clones and mutation spectra | DeepSomatic, GATK Mutect2, GenMap | 16 CPU, 64 GB per clone (DeepSomatic); GPU optional |

Public inputs: [DS13](../../data/DS13-clone-somatic-variation/), [DS01](../../data/DS01-pn40024-references/), [DS02](../../data/DS02-grapepan-v1/).

## References

- Vondras et al. 2019. The genomic diversification of grapevine clones. *BMC Genomics*. [doi:10.1186/s12864-019-6211-2](https://doi.org/10.1186/s12864-019-6211-2)
- Callipo et al. 2026. A dual genome-methylome map of clonal evolution in grapevine. *Genome Biology*. [doi:10.1186/s13059-026-04184-x](https://doi.org/10.1186/s13059-026-04184-x)
- Zdunić et al. 2026. Whole-genome sequencing of eight grapevine clones of cv. Tribidrag (Vitis vinifera L.) reveals measurable differentiation not linked directly to phenotypic divergence. *BMC Plant Biology*. [doi:10.1186/s12870-026-10110-x](https://doi.org/10.1186/s12870-026-10110-x)
- Roach et al. 2018. Population sequencing reveals clonal diversity and ancestral inbreeding in the grapevine cultivar Chardonnay. *PLOS Genetics*. [doi:10.1371/journal.pgen.1007807](https://doi.org/10.1371/journal.pgen.1007807)
- Sichel et al. 2023. Chimeras in Merlot grapevine revealed by phased assembly. *BMC Genomics*. [doi:10.1186/s12864-023-09453-8](https://doi.org/10.1186/s12864-023-09453-8)
- Xiao et al. 2025. Impacts of reproductive systems on grapevine genome and breeding. *Nature Communications*. [doi:10.1038/s41467-025-56817-7](https://doi.org/10.1038/s41467-025-56817-7)
- Liang et al. 2019. Whole-genome resequencing of 472 Vitis accessions for grapevine diversity and demographic history analyses. *Nature Communications*. [doi:10.1038/s41467-019-09135-8](https://doi.org/10.1038/s41467-019-09135-8)
- Alexandrov et al. 2013. Signatures of mutational processes in human cancer. *Nature*. [doi:10.1038/nature12477](https://doi.org/10.1038/nature12477)
- Carbonell-Bejerano et al. 2017. Catastrophic Unbalanced Genome Rearrangements Cause Somatic Loss of Berry Color in Grapevine. *Plant Physiology*. [doi:10.1104/pp.17.00715](https://doi.org/10.1104/pp.17.00715)
- Carrier et al. 2012. Transposable Elements Are a Major Cause of Somatic Polymorphism in Vitis vinifera L. *PLoS ONE*. [doi:10.1371/journal.pone.0032973](https://doi.org/10.1371/journal.pone.0032973)
- Goel et al. 2024. The vast majority of somatic mutations in plants are layer-specific. *Genome Biology*. [doi:10.1186/s13059-024-03337-0](https://doi.org/10.1186/s13059-024-03337-0)
- Hofmeister et al. 2020. A genome assembly and the somatic genetic and epigenetic mutation rate in a wild long-lived perennial Populus trichocarpa. *Genome Biology*. [doi:10.1186/s13059-020-02162-5](https://doi.org/10.1186/s13059-020-02162-5)
- Orr et al. 2020. A phylogenomic approach reveals a low somatic mutation rate in a long-lived plant. *Proceedings of the Royal Society B: Biological Sciences*. [doi:10.1098/rspb.2019.2364](https://doi.org/10.1098/rspb.2019.2364)
- Schmid-Siegert et al. 2017. Low number of fixed somatic mutations in a long-lived oak tree. *Nature Plants*. [doi:10.1038/s41477-017-0066-9](https://doi.org/10.1038/s41477-017-0066-9)
- Tello et al. 2025. Genome resequencing and custom genotyping elucidates the origin and dissemination history of an emblematic grapevine cultivar, ‘Tempranillo Tinto’. *Horticulture Research*. [doi:10.1093/hr/uhaf237](https://doi.org/10.1093/hr/uhaf237)
