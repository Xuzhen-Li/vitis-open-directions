# 21. Meta-analysis of public GWAS, cross-ancestry genomic prediction and SV markers

中文：公开 GWAS 荟萃、跨祖先基因组预测与 SV 标记

Rank 21 of 22 (score F 1 + N 2 + E 2 = 5; see docs/RANKING.md) · Tier: Medium (E = 2, effort range ending after 6 weeks and by 4 months) · Origin: new · Status: draft v0.3.2, 2026-11-14

## Gap

No meta-analysis of grape GWAS summary statistics was found, genomic prediction between wild species and *V. vinifera* was not found, and SV-based markers for breeding were not found. All depend on public phenotypes [待确认].

**Existing work**

- [Liu et al. 2024](https://doi.org/10.1038/s41588-024-01967-5): SV-based GWAS in Grapepan.
- [Brault et al. 2022](https://doi.org/10.1093/hr/uhac041): across-population genomic prediction in grape.

**How this project differs**

Starts with an inventory of what is public; the meta-analysis and prediction run only if the inventory passes.

**Background survey (literature read for this plan)**

Grape GWAS panels are moderate in size. A 279-cultivar diversity panel phenotyped for 127 traits and genotyped for 63k SNPs mapped yield, acidity, aroma-precursor and polyphenol traits and tested genomic prediction ([Flutre et al. 2022](https://doi.org/10.1093/g3journal/jkac103)); the design and LD of that panel were described earlier ([Nicolas et al. 2016](https://doi.org/10.1186/s12870-016-0754-z)). Across-population prediction from a diversity panel to ten connected bi-parental crosses gave useful accuracy for cross means ([Brault et al. 2022](https://doi.org/10.1093/hr/uhac041)). Grapepan added SV-based GWAS on graph genotypes ([Liu et al. 2024](https://doi.org/10.1038/s41588-024-01967-5)).

The methods are standard in human genetics. METAL combines GWAS summary statistics ([Willer et al. 2010](https://doi.org/10.1093/bioinformatics/btq340)); LD score regression separates confounding from polygenicity but needs a matched LD reference and large samples ([Bulik-Sullivan et al. 2015](https://doi.org/10.1038/ng.3211)); BGLR fits Bayesian whole-genome regressions for prediction ([Pérez and de los Campos 2014](https://doi.org/10.1534/genetics.114.164442)). Polygenic scores lose accuracy across ancestry groups, which is the human precedent for the cross-ancestry test planned here ([Martin et al. 2019](https://doi.org/10.1038/s41588-019-0379-x)).

**Specific gap.** No grape GWAS meta-analysis was found, and prediction from wild *Vitis* groups to *V. vinifera* was not tested; whether enough public summary statistics exist is itself unknown [待确认].

## Question

Is there enough public phenotype and summary-statistic data for a grape GWAS meta-analysis and for cross-ancestry prediction?

## Hypotheses, planned figures and criteria

No results are given here. Each row says what would count as support; the exact thresholds go into the preregistration.

| Figure or table | Hypothesis or purpose | Criterion |
|---|---|---|
| Table 1. Inventory of public GWAS data | Not a hypothesis. | Stop rule: if fewer than the preregistered number of studies share a trait with public statistics, the meta-analysis stops. Rule for when two studies measure the same trait fixed in advance. |
| Fig 1. Meta-analysis (if feasible) | Loci found in a discovery set of studies replicate in a separate set. | Sample overlap between studies identified first at the individual level with AM04; LDSC intercepts used only where individual data are missing and only above a minimum number of SNPs and samples fixed in advance, because small grape GWAS lack a matched LD reference; replication effect sizes taken from the replication set rather than the discovery set; per-study genomic control checked and applied once; random effects by REML with Hartung–Knapp when fewer than five studies; heterogeneity reported; discovery and replication sets disjoint and fixed in advance. |
| Fig 2. Prediction across ancestry groups | Accuracy drops when training and test groups differ. | Deduplicate with AM04 (one sample per genotype); clones and relatives kept in the same fold; marker QC and selection performed inside training folds only; largest training–test kinship reported; compared with within-group cross-validation at matched sample size. |
| Table 2. SV marker panel | Resource. | Graph-genotyped SVs with r² above a preregistered threshold to reported loci, using an LD panel of the same ancestry as the original GWAS and re-estimated in the target group; flanking sequence provided for assay design. |

**Expected results and how they will be read**

- Table 1 decides the project: if the stop rule triggers, the output is a published inventory and a data note, which is still useful.
- Fig 1: replicated loci across independent studies would be the first grape meta-analysis result; no replication is reported with the power of the replication set.
- Fig 2: an accuracy drop between ancestry groups at matched sample size, beyond within-group variation, would show that the human pattern applies to grape panels.
- Table 2 is a resource for marker design, with r² values in the target group.

## Preregistration

Before any data are analysed, fill in [`docs/PREREGISTRATION.md`](../../../../templates/PREREGISTRATION.md) for this project: hypotheses, primary outcome, sample inclusion rules, thresholds, stop rules and what will be reported if a hypothesis fails. Commit it with a date. Criteria from any earlier attempt are reference only and are not carried over.

## Data

| Module | Dataset |
|---|---|
| [DS22](../../data/DS22-phenotypes-and-gwas-summaries/) | Public grape phenotypes, GWAS summary statistics and variant call sets |
| [DS02](../../data/DS02-grapepan-v1/) | Grapepan v1.0: T2T haplotypes, graphs and a 466-accession resequencing panel |
| [DS10](../../data/DS10-reseq-472-vitis/) | Resequencing of 472 Vitis accessions (and the 2017 domestication panel) |
| [DS12](../../data/DS12-reseq-204-magris2021/) | Resequencing of 204 V. vinifera accessions (Magris et al. 2021) |
| [DS01](../../data/DS01-pn40024-references/) | PN40024 references: PN_T2T (v5), PN40024.v4 and 12X |

**How each dataset is used**

| Module | Role in this project |
|---|---|
| DS22 | Public phenotypes and summary statistics; the inventory starts here |
| DS02, DS10, DS12 | Genotypes for LD panels, graph SVs and prediction |
| DS01 | PN_T2T coordinates; liftover of older summary statistics |

New public data: none planned. Phenotypes and summary statistics from the 279-cultivar panel are listed in DS22 only if their public release is confirmed [待确认].

## Analysis steps

Shared modules, in order:

1. [AM04 · Sample identity, clones and relatedness](../../analyses/AM04-sample-identity/)
2. [AM24 · GWAS meta-analysis and genomic prediction](../../analyses/AM24-gwas-meta-and-prediction/)
3. [AM03 · Short-read mapping and small-variant calling](../../analyses/AM03-short-read-variants/)
4. [AM07 · Pangenome graph build and genotyping](../../analyses/AM07-graph-build-and-genotype/)

Project-specific steps:

- Inventory public phenotypes and statistics (DS22).
- Find overlapping samples between studies (AM04 at the individual level first; LDSC intercepts only where individual data are lacking).
- Harmonise to PN_T2T; meta-analyse with METAL and metafor (AM24).
- Run prediction across groups with BGLR or rrBLUP under the deduplication and fold rules.
- List SV markers from graph genotypes (AM07).

**Stepwise work plan with tools**

| Step | Work | Tools (paper) | Output |
|---|---|---|---|
| 1 | Inventory phenotypes and summary statistics; apply the stop rule | DS22 | Table 1 |
| 2 | Identity and overlap of samples across studies | AM04 | Overlap table |
| 3 | Lift over to PN_T2T; harmonise alleles | AM24 | Harmonised statistics |
| 4 | Meta-analysis in discovery and replication sets | METAL; LDSC only under the preregistered limits (AM24) | Fig 1 |
| 5 | Prediction within and across ancestry groups | BGLR or rrBLUP (AM24) | Fig 2 |
| 6 | Graph-genotyped SVs in LD with reported loci | AM07, PLINK 2 | Table 2 |

## Paper design and split

| Paper | Working title | Type | Figures |
|---|---|---|---|
| U1 | Public grape GWAS data: inventory and meta-analysis | short paper, only if the inventory passes | Table 1, Fig 1 |
| U2 | Cross-ancestry genomic prediction in grape | paper | Fig 2 |
| U3 | An SV marker panel from graph genotypes | data note | Table 2 |

Each paper: introduction from the gap above; one results section per figure; methods with tool versions from the modules; data availability listing every accession used and the derived tables.

## Risks and novelty check

- Risk: Phenotypes may not be public.
- Risk: Trait definitions differ between studies.
- Novelty: checked against the existing work above (Crossref-verified DOIs). Repeat the search before writing; anything marked [待确认] is not yet verified.

## Risks and how to handle them

Added 2026-11-26. Each row names a risk, the evidence behind it, and a concrete check or fallback. Sources cited here were read for this section and their DOIs were checked on Crossref; preprints are marked.

| Area | Risk | Check or mitigation |
|---|---|---|
| Data access and licence | Licence terms for DS22 are still open per source; the across-population prediction data and the Bordeaux call sets are available ([data/DOWNLOADS.md](../../data/DOWNLOADS.md)). | Record the licence of every phenotype and summary-statistic file before use; leave out any file without clear reuse terms. |
| Platform and panel differences | Recent grape GWAS used different panels and platforms: 288 accessions on the Vitis18K array over 12 years ([de Oliveira et al. 2026](https://doi.org/10.1371/journal.pone.0343491)), 588 cultivars of a breeding programme over three seasons ([García-Abadillo et al. 2024](https://doi.org/10.1093/hr/uhad283)), and 231 resequenced accessions ([Gan et al. 2025](https://doi.org/10.1093/hr/uhaf128)). | Lift all markers to PN_T2T coordinates; meta-analyse at the locus level where marker sets do not overlap. |
| Environment and season | QTL effects vary across environments; metaGE meta-analyses single-environment GWAS while allowing effects to differ ([De Walsche et al. 2025](https://doi.org/10.1371/journal.pgen.1011553)). | Use a random-effects or metaGE-type model and report heterogeneity per locus. |
| Prediction across populations | From a diversity panel to ten crosses, predictive ability averaged 0.6 for cross means but 0.26 for individuals within crosses, and depended on genetic distance between parents ([Brault et al. 2022](https://doi.org/10.1093/hr/uhac041)). | Set expectations from these values; report accuracy against genetic distance between training and target groups. |
| Clones, synonyms and pedigree | Breeding panels share parents and include clones. | Fit a kinship matrix; remove duplicate genotypes across studies (project 08). |
| Sample size and power | Few studies share a trait with public summary statistics. | Keep the stop rule: if fewer studies than the preregistered minimum share a trait, publish the inventory as a data note. |
| Computing cost | Small. | None. |

**Recent and competing work (search of 2024 to 2026 literature on 2026-11-26)**

- Genomic prediction in grape has been applied within breeding programmes ([Brault et al. 2024](https://doi.org/10.1093/g3journal/jkae038)) and with deep learning on phenotype images ([Gan et al. 2025](https://doi.org/10.1093/hr/uhaf128)). No grape GWAS meta-analysis across public studies was found.

**What would end the idea, and the fallback.** If summary statistics are not public for enough studies, the meta-analysis cannot run. The fallback is the data inventory (see the stop rule above).

**Journal-level realism.** Specialty plant breeding or horticulture journal; a data note if the stop rule triggers.

## Reference study in another species

Added 2026-11-26. Published studies that already did this kind of work in another species, to plan the grape version against. Every DOI was checked on Crossref. Figures are described, not copied; a figure redrawn for a grape paper would be marked "Redrawn after" its source. The last bullet for each study lists what a grape results section would need; it is a planning suggestion, not a finding of that study.

### Yang et al. 2025

- **Paper:** [Yang et al. 2025](https://doi.org/10.1038/s41467-025-58081-1), *Nature Communications*.
- **Species:** Rice, six populations.
- **What was done:** GWAS in six rice populations were combined by meta-analysis on a graph pangenome, including PAV; 156 QTL were found, and candidate genes for grain width and length were tested with CRISPR.
- **Figures:** Fig. 1 study design; Fig. 2 trait-associated variants found by the meta-analysis (156 QTL); Fig. 3 meta-GWAS for grain width and functional analysis; Fig. 4 meta-GWAS for grain length and functional analysis.
- **What a grape results section would need:** GWAS per population and the meta-analysis; loci found only by the meta-analysis; PAV and SV associations; validation of candidate genes.

### Minamikawa et al. 2017

- **Paper:** [Minamikawa et al. 2017](https://doi.org/10.1038/s41598-017-05100-x), *Scientific Reports* (PMC5498537). Licence CC BY 4.0: figures may be reused with credit; none are copied here.
- **Species:** citrus, a parental population of 111 varieties and a breeding population of 676 individuals from 35 full-sib families.
- **What was done:** both populations were genotyped at 1,841 SNPs and scored for 17 fruit quality traits; combining them raised GWAS power and prediction accuracy; a multi-kernel model with additive and dominance effects helped some traits; GBLUP with a linear kernel was more robust than a Gaussian kernel.
- **Figures:** Fig. 1 LD decay; Fig. 2 genetic and phenotypic structure; Fig. 3 Manhattan plots for 17 traits; Fig. 4 prediction models compared; Fig. 5 prediction of distribution tails; Fig. 6 accuracy in the breeding population.
- **What its results section needed:** LD decay and structure, a combined association scan, several prediction models compared, and accuracy in a population not used for training.
- **Grape version:** Fig. 3 equivalents from meta-analysis of published grape summary statistics, and Fig. 4 and 6 equivalents for prediction across populations, if the phenotype inventory passes (risk above).

### Q1-level bar

Target: a first-quartile (Q1) journal in plant science, genetics or evolution. Quartile lists change each year, so the journal is chosen from the current list at submission [to confirm]. To compete at that level, the grape paper needs: a meta-analysis that finds loci missed by single studies, cross-population prediction accuracy, and at least one candidate supported by other evidence, as in the rice study.

## Rough estimates

- Compute: small to medium [draft]
- Effort: 1–3 months for one person [draft]
- Target: breeding or genetics journal [draft]

## Suggested journal level (suggestion only)

**Specialty journal (plant breeding or horticulture); a data note if the stop rule triggers.** Grape GWAS and prediction papers read here appeared in *G3*, *BMC Plant Biology* and *Horticulture Research*; the human method papers in *Bioinformatics*, *Genetics* and *Nature Genetics*. This is a suggestion, not a decision; impact factors are not used.

## Continue on HPC

Run each step as its own job, in this order. Every job writes `.DONE` or `.FAILED` and a log; the next step starts only after `.DONE`. Template and rules: [`docs/HPC_JOBS.md`](../../../../templates/HPC_JOBS.md).

| Order | Step | Main tools | Resources (rough) |
|---|---|---|---|
| 1 | [AM04](../../analyses/AM04-sample-identity/) Sample identity, clones and relatedness | plink2, KING, VIVC | 8 CPU, 32 GB, < 2 h |
| 2 | [AM24](../../analyses/AM24-gwas-meta-and-prediction/) GWAS meta-analysis and genomic prediction | METAL, metafor, LDSC | 8 CPU, 32 GB |
| 3 | [AM03](../../analyses/AM03-short-read-variants/) Short-read mapping and small-variant calling | bwa-mem2, samtools, DeepVariant | 16 CPU, 64 GB, 6–24 h per sample (DeepVariant); joint step 32 CPU, 128 GB |
| 4 | [AM07](../../analyses/AM07-graph-build-and-genotype/) Pangenome graph build and genotyping | Minigraph-Cactus, PGGB, vg | 32–64 CPU, 256–512 GB for graph builds; 16 CPU, 64 GB per sample for giraffe |

Public inputs: [DS22](../../data/DS22-phenotypes-and-gwas-summaries/), [DS02](../../data/DS02-grapepan-v1/), [DS10](../../data/DS10-reseq-472-vitis/), [DS12](../../data/DS12-reseq-204-magris2021/), [DS01](../../data/DS01-pn40024-references/).

## References

- Liu et al. 2024. Grapevine pangenome facilitates trait genetics and genomic breeding. *Nature Genetics*. [doi:10.1038/s41588-024-01967-5](https://doi.org/10.1038/s41588-024-01967-5)
- Brault et al. 2022. Across-population genomic prediction in grapevine opens up promising prospects for breeding. *Horticulture Research*. [doi:10.1093/hr/uhac041](https://doi.org/10.1093/hr/uhac041)
- Bulik-Sullivan et al. 2015. LD Score regression distinguishes confounding from polygenicity in genome-wide association studies. *Nature Genetics*. [doi:10.1038/ng.3211](https://doi.org/10.1038/ng.3211)
- Flutre et al. 2022. A genome-wide association and prediction study in grapevine deciphers the genetic architecture of multiple traits and identifies genes under many new QTLs. *G3 Genes|Genomes|Genetics*. [doi:10.1093/g3journal/jkac103](https://doi.org/10.1093/g3journal/jkac103)
- Martin et al. 2019. Clinical use of current polygenic risk scores may exacerbate health disparities. *Nature Genetics*. [doi:10.1038/s41588-019-0379-x](https://doi.org/10.1038/s41588-019-0379-x)
- Nicolas et al. 2016. Genetic diversity, linkage disequilibrium and power of a large grapevine (Vitis vinifera L) diversity panel newly designed for association studies. *BMC Plant Biology*. [doi:10.1186/s12870-016-0754-z](https://doi.org/10.1186/s12870-016-0754-z)
- Pérez et al. 2014. Genome-Wide Regression and Prediction with the BGLR Statistical Package. *Genetics*. [doi:10.1534/genetics.114.164442](https://doi.org/10.1534/genetics.114.164442)
- Willer et al. 2010. METAL: fast and efficient meta-analysis of genomewide association scans. *Bioinformatics*. [doi:10.1093/bioinformatics/btq340](https://doi.org/10.1093/bioinformatics/btq340)
- de Oliveira et al. 2026. Genome-wide association study in a diverse grapevine collection provides insights into the genetic basis of berry size and cluster architecture traits. *PLOS One*. [doi:10.1371/journal.pone.0343491](https://doi.org/10.1371/journal.pone.0343491)
- García-Abadillo et al. 2024. Dissecting the complex genetic basis of pre- and post-harvest traits in Vitis vinifera L . using genome-wide association studies. *Horticulture Research*. [doi:10.1093/hr/uhad283](https://doi.org/10.1093/hr/uhad283)
- Gan et al. 2025. Deep learning empowers genomic selection of pest-resistant grapevine. *Horticulture Research*. [doi:10.1093/hr/uhaf128](https://doi.org/10.1093/hr/uhaf128)
- De Walsche et al. 2025. metaGE: Investigating genotype x environment interactions through GWAS meta-analysis. *PLOS Genetics*. [doi:10.1371/journal.pgen.1011553](https://doi.org/10.1371/journal.pgen.1011553)
- Brault et al. 2024. Enhancing grapevine breeding efficiency through genomic prediction and selection index. *G3: Genes, Genomes, Genetics*. [doi:10.1093/g3journal/jkae038](https://doi.org/10.1093/g3journal/jkae038)
- Yang et al. 2025. GWAS meta-analysis using a graph-based pan-genome enhanced gene mining efficiency for agronomic traits in rice. *Nature Communications*. [doi:10.1038/s41467-025-58081-1](https://doi.org/10.1038/s41467-025-58081-1)
- Minamikawa et al. 2017. Genome-wide association study and genomic prediction in citrus: Potential of genomics-assisted breeding for fruit quality traits. *Scientific Reports*. [doi:10.1038/s41598-017-05100-x](https://doi.org/10.1038/s41598-017-05100-x)
