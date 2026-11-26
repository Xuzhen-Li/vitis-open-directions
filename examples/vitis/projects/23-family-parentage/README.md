# 23. Family parentage and relationship QC on public grape records

中文：公开葡萄记录的亲本关系与亲缘质控

Not scored (see docs/RANKING.md; projects 23 to 26 were added after the ranking) · Tier: Medium [draft] · Origin: continued: design written earlier, restarted here from public data under a new preregistration · Status: draft, 2026-11-25 · Progress: [STATUS.md](STATUS.md)

## Gap

Grape parentage has been inferred from SSR and SNP-array panels, and published lists name many parent-offspring links. A check of those reported links against whole-genome public resequencing, with clones, aliases and sports collapsed first and with meiosis counts kept separate from edge counts, was not found [待确认: repeat the search before writing].

**Existing work and background survey**

Microsatellites first showed that Cabernet Sauvignon is a cross of Cabernet franc and Sauvignon blanc ([Bowers and Meredith 1997](https://doi.org/10.1038/ng0597-84)) and that Chardonnay, Gamay and other wine grapes descend from Pinot and Gouais blanc ([Bowers et al. 1999](https://doi.org/10.1126/science.285.5433.1562)). Large SSR profiles followed: 1,005 accessions ([Cipriani et al. 2010](https://doi.org/10.1007/s00122-010-1411-9)) and a large-scale parentage analysis in an extended set of cultivars ([Lacombe et al. 2013](https://doi.org/10.1007/s00122-012-1988-2)). SNP arrays then gave a 10K-SNP diversity analysis of 783 cultivars with parentage links ([Laucou et al. 2018](https://doi.org/10.1371/journal.pone.0192540)) and a parentage atlas of Italian varieties ([D’Onofrio et al. 2021](https://doi.org/10.3389/fpls.2020.605934)). Whole-genome panels of 204 accessions now exist ([Magris et al. 2021](https://doi.org/10.1038/s41467-021-27487-y)), and a phased Cabernet Sauvignon trio is public ([Cochetel et al. 2025](https://doi.org/10.1186/s13059-025-03858-2)).

Methods: KING estimates kinship robustly in structured samples ([Manichaikul et al. 2010](https://doi.org/10.1093/bioinformatics/btq559)); sequoia assigns parents, clusters half-siblings and assigns grandparents from SNP data ([Huisman 2017](https://doi.org/10.1111/1755-0998.12665)); pedigree-aware phasing uses family structure to improve haplotypes ([O'Connell et al. 2014](https://doi.org/10.1371/journal.pgen.1004234)).

**How this project differs**

Reported links are treated as claims to test, not as facts. The output is one validated pedigree table with the evidence for each edge, and separate counts of edges, offspring, candidate meioses, distinguishable gamete transmissions and informative meioses. Only public records and public genotypes are used.

## Question

Which reported grape parent-offspring links are supported, contradicted or untestable with public whole-genome genotypes, and how many independent meioses do the supported links give?

## Hypotheses, planned figures and criteria

No results are given here. Each row says what would count as support; the exact thresholds go into the preregistration.

| Figure or table | Hypothesis or purpose | Criterion |
|---|---|---|
| Table 1. Identity and pedigree inventory | Not a hypothesis. | Stable IDs, aliases, clone and duplicate flags, source of each reported link, missing parents and possible selfing; a catalogue of sources only. |
| Fig 1. Threshold calibration | IBS0 and Mendelian error separate true trios from unrelated triples. | Positive control: the DS18 trio and literature trios [待确认: which trios]; negative control: random unrelated triples; depth and genotype-quality filters fixed before any result is seen. |
| Fig 2. Support for reported links | Most reported links are supported. | Each link labelled supported, contradicted or untestable with the preregistered thresholds; conflicting labels flagged, not overwritten. |
| Table 2. Meiosis counts | Not a hypothesis. | Five counting layers reported separately; clones, aliases and sports add no meioses. |

## Preregistration

Before any data are analysed, fill in [`docs/PREREGISTRATION.md`](../../../../templates/PREREGISTRATION.md) for this project: hypotheses, primary outcome, sample inclusion rules, thresholds, stop rules and what will be reported if a hypothesis fails. Commit it with a date. Criteria from any earlier attempt are reference only and are not carried over.

## Data

| Module | Dataset |
|---|---|
| [DS10](../../data/DS10-reseq-472-vitis/) | Resequencing of 472 Vitis accessions (and the 2017 domestication panel) |
| [DS12](../../data/DS12-reseq-204-magris2021/) | Resequencing of 204 V. vinifera accessions (Magris et al. 2021) |
| [DS02](../../data/DS02-grapepan-v1/) | Grapepan v1.0: T2T haplotypes, graphs and a 466-accession resequencing panel |
| [DS11](../../data/DS11-reseq-3525-dong2023/) | Resequencing of 3,525 grapevine accessions (Dong et al. 2023) |
| [DS18](../../data/DS18-methylome-and-trio/) | Public grape methylomes and a phased Cabernet Sauvignon trio |
| [DS01](../../data/DS01-pn40024-references/) | PN40024 references: PN_T2T (v5), PN40024.v4 and 12X |

DS11 is used only after its run list can be exported [待确认]. Public records: published parentage lists (Laucou et al. 2018 and the papers above) and VIVC entries, recorded with the date opened. New public data: none needed.

## Analysis steps

Shared modules, in order:

1. [AM04 · Sample identity, clones and relatedness](../../analyses/AM04-sample-identity/)
2. [AM03 · Short-read mapping and small-variant calling](../../analyses/AM03-short-read-variants/)
3. [AM26 · Phasing, ancestral states and recombination rates](../../analyses/AM26-phasing-polarisation-recombination/)

**Stepwise work plan with tools**

| Step | Work | Tools (paper) | Output |
|---|---|---|---|
| 1 | Take the clone-collapsed sample table and biallelic SNP set from project 08 | AM04 | Sample and SNP set |
| 2 | Compile reported links from published lists and VIVC; link names to runs | custom | Table 1 |
| 3 | Fix depth and genotype-quality filters; compute IBS0, KING kinship and Mendelian error | PLINK 2, KING | Pair and trio statistics |
| 4 | Calibrate thresholds on the DS18 trio and literature trios | custom | Fig 1 |
| 5 | Test each reported link; run sequoia for unreported candidate parents as a separate, labelled analysis | sequoia | Fig 2 |
| 6 | Count edges, offspring and meioses in five layers; export the pedigree table for projects 10, 15, 16, 21 and 24 | custom | Table 2 |

## Expected results and how they will be read

- Fig 1 sets the thresholds; if the positive control fails at the available depth, the project reports only the inventory.
- Fig 2: a high share of supported links confirms that published lists can be reused; contradicted links are listed with evidence and sent back to the source as open questions, not corrected here.
- Table 2 is the input for project 24; a small number of informative meioses would close the pedigree route there.

## Paper design and split

| Paper | Working title | Type | Figures |
|---|---|---|---|
| P1 | Testing reported grape pedigrees with public whole-genome data | data note or short paper | Table 1, Fig 1–2, Table 2 |

Each paper: introduction from the gap above; one results section per figure; methods with tool versions from the modules; data availability listing every accession used and the derived tables.

## Risks and novelty check

- Risk: Low depth can drop one heterozygous allele and mimic a Mendelian error; filters must be fixed first.
- Risk: Name matching between records and runs may fail for many cultivars [待确认: share linkable].
- Risk: An edge count is not a meiosis count; mixing them would inflate later recombination work.
- Novelty: checked against the existing work above (Crossref-verified DOIs). Repeat the search before writing; anything marked [待确认] is not yet verified.

## Risks and how to handle them

Added 2026-11-26. Each row names a risk, the evidence behind it, and a concrete check or fallback. Sources cited here were read for this section and their DOIs were checked on Crossref; preprints are marked.

| Area | Risk | Check or mitigation |
|---|---|---|
| Data access and licence | Runs of the 3,525-accession panel (DS11) were blocked on the public listing check; INSDC panels are available ([data/DOWNLOADS.md](../../data/DOWNLOADS.md)). | Plan on INSDC panels; add DS11 only if access is obtained. |
| No positive controls | A parentage atlas of 840 olive cultivars validated its assignments with 13 seedlings from known crosses ([Gómez-Gálvez et al. 2026](https://doi.org/10.1186/s12870-026-08504-y)). Without such controls, error rates are unknown. | Include public samples from documented crosses (mapping-population parents and offspring) as controls and report the error rate on them. |
| Low depth | Pedigree links can be reconstructed from very low-coverage data with methods built for it ([Snyder-Mackler et al. 2016](https://doi.org/10.1534/genetics.116.187492)); hard Mendelian-error counts on low depth mimic exclusions (see above). | Use genotype-likelihood or IBD-based relationship estimates; count Mendelian errors only at sites above a depth threshold. |
| Clones, synonyms and pedigree | Identical genotypes persist for centuries ([Noraz et al. 2026](https://doi.org/10.1038/s41467-026-70166-z)), and selfing, crossing and cloning all occur in the Pinot noir pedigree ([Xiao et al. 2025](https://doi.org/10.1038/s41467-025-56817-7)). A clone can look like a parent-offspring pair at low depth, and selfed offspring have one parent. | Separate clone pairs (near-complete identity, few somatic differences) from parent-offspring pairs first; allow selfing in the pedigree model. |
| Array data | Many grape collections use arrays (Vitis18K, [de Oliveira et al. 2026](https://doi.org/10.1371/journal.pone.0343491); Vitis22K, [Costantini et al. 2026](https://doi.org/10.3389/fpls.2026.1771381)). | Keep a shared SNP set so array-genotyped records can be tested too. |
| Sample size and power | Untestable links (missing parents) can outnumber testable ones. | Report supported, contradicted and untestable counts; do not infer from untestable links. |
| Computing cost | Small once genotypes exist. | Reuse the project 08 identity SNP set. |

**Recent and competing work (search of 2024 to 2026 literature on 2026-11-26)**

- The olive atlas is the closest design in another clonal fruit crop. In grape, recent parentage studies cover national collections with arrays (see Background); no check of reported links across public whole-genome data was found.

**What would end the idea, and the fallback.** If too few parent-offspring sets are testable in public data, the meiosis count for project 24 is small. The fallback is a validated relationship table without the meiosis estimate.

**Journal-level realism.** Specialty plant genetics or germplasm journal.

## Reference study in another species

Added 2026-11-26. Published studies that already did this kind of work in another species, to plan the grape version against. Every DOI was checked on Crossref. Figures are described, not copied; a figure redrawn for a grape paper would be marked "Redrawn after" its source. The last bullet for each study lists what a grape results section would need; it is a planning suggestion, not a finding of that study.

### Muranty et al. 2020

- **Paper:** [Muranty et al. 2020](https://doi.org/10.1186/s12870-019-2171-6), *BMC Plant Biology* (PMC6941274). Licence CC BY 4.0: figures may be reused with credit; none are copied here.
- **Species:** apple, over 1,400 mostly old cultivars kept by grafting, about 253,000 SNPs.
- **What was done:** simple exclusion tests that count Mendelian errors found more than one thousand parent-offspring relations and 295 complete parent-offspring families; for 26 pairs a grandparent couple was found for the missing parent.
- **Figures:** Fig. 1 Mendelian error counts in candidate parent-offspring duos; Fig. 2 pedigree network of 832 individuals; Fig. 3 error counts in candidate trios; Fig. 4 and 5 error counts in grandparent groups with about 25,000 and about 253,000 SNPs; Fig. 6 one reconstructed multi-generation pedigree.
- **What its results section needed:** error-count distributions with a clear gap between true and false relations, a network view, and the effect of marker density on the tests.
- **Grape version:** Fig. 1, 3 and 4 equivalents on the de-duplicated grape panel, with the gap between true and false relations shown separately for high- and low-depth samples; the network (Fig. 2) feeds the meiosis count of project 24.
- **Further results a grape version would need:** detection of parent-offspring pairs and trios with thresholds; a relationship network; a multi-generation pedigree; inbreeding.

### Coverage note

Muranty et al. 2020 used SNP array data, not whole-genome resequencing, so its thresholds do not transfer directly to low-depth resequencing data.

### Q1-level bar

Target: a first-quartile (Q1) journal in plant science, genetics or evolution. Quartile lists change each year, so the journal is chosen from the current list at submission [to confirm]. To compete at that level, the grape paper needs: a relationship table tested on crosses of known parentage with error rates, and a pedigree result that matters for grape history; joining with project 08 or 24 strengthens the case.

## Rough estimates

- Compute: small to medium [draft]
- Effort: 4–8 weeks for one person [draft]
- Target: plant genetics or germplasm journal [draft]

## Suggested journal level (suggestion only)

**Specialty journal (plant genetics, germplasm or horticulture).** Comparable grape parentage papers read here appeared in *Theoretical and Applied Genetics*, *PLOS ONE* and *Frontiers in Plant Science*; the early landmark cases appeared in *Nature Genetics* and *Science* because they named the parents of famous cultivars, which this project does not aim to do. This is a suggestion, not a decision; impact factors are not used.

## Continue on HPC

Run each step as its own job, in this order. Every job writes `.DONE` or `.FAILED` and a log; the next step starts only after `.DONE`. Template and rules: [`docs/HPC_JOBS.md`](../../../../templates/HPC_JOBS.md).

| Order | Step | Main tools | Resources (rough) |
|---|---|---|---|
| 1 | [AM04](../../analyses/AM04-sample-identity/) Sample identity, clones and relatedness | PLINK 2, KING | 8 CPU, 32 GB |
| 2 | [AM03](../../analyses/AM03-short-read-variants/) Short-read variants (only for runs missing from project 08) | bwa-mem2, GATK or DeepVariant | 16 CPU, 64 GB per sample; array |
| 3 | Trio statistics and sequoia | PLINK 2, R sequoia | 4 CPU, 16 GB |

Public inputs: [DS10](../../data/DS10-reseq-472-vitis/), [DS12](../../data/DS12-reseq-204-magris2021/), [DS02](../../data/DS02-grapepan-v1/), [DS18](../../data/DS18-methylome-and-trio/), [DS01](../../data/DS01-pn40024-references/).

## References

- Bowers et al. 1997. The parentage of a classic wine grape, Cabernet Sauvignon. *Nature Genetics*. [doi:10.1038/ng0597-84](https://doi.org/10.1038/ng0597-84)
- Bowers et al. 1999. Historical Genetics: The Parentage of Chardonnay, Gamay, and Other Wine Grapes of Northeastern France. *Science*. [doi:10.1126/science.285.5433.1562](https://doi.org/10.1126/science.285.5433.1562)
- Cipriani et al. 2010. The SSR-based molecular profile of 1005 grapevine (Vitis vinifera L.) accessions uncovers new synonymy and parentages, and reveals a large admixture amongst varieties of different geographic origin. *Theoretical and Applied Genetics*. [doi:10.1007/s00122-010-1411-9](https://doi.org/10.1007/s00122-010-1411-9)
- Cochetel et al. 2025. Phased epigenomics and methylation inheritance in a historical Vitis vinifera hybrid. *Genome Biology*. [doi:10.1186/s13059-025-03858-2](https://doi.org/10.1186/s13059-025-03858-2)
- D’Onofrio et al. 2021. Parentage Atlas of Italian Grapevine Varieties as Inferred From SNP Genotyping. *Frontiers in Plant Science*. [doi:10.3389/fpls.2020.605934](https://doi.org/10.3389/fpls.2020.605934)
- Huisman 2017. Pedigree reconstruction from SNP data: parentage assignment, sibship clustering and beyond. *Molecular Ecology Resources*. [doi:10.1111/1755-0998.12665](https://doi.org/10.1111/1755-0998.12665)
- Lacombe et al. 2013. Large-scale parentage analysis in an extended set of grapevine cultivars (Vitis vinifera L.). *Theoretical and Applied Genetics*. [doi:10.1007/s00122-012-1988-2](https://doi.org/10.1007/s00122-012-1988-2)
- Laucou et al. 2018. Extended diversity analysis of cultivated grapevine Vitis vinifera with 10K genome-wide SNPs. *PLOS ONE*. [doi:10.1371/journal.pone.0192540](https://doi.org/10.1371/journal.pone.0192540)
- Magris et al. 2021. The genomes of 204 Vitis vinifera accessions reveal the origin of European wine grapes. *Nature Communications*. [doi:10.1038/s41467-021-27487-y](https://doi.org/10.1038/s41467-021-27487-y)
- Manichaikul et al. 2010. Robust relationship inference in genome-wide association studies. *Bioinformatics*. [doi:10.1093/bioinformatics/btq559](https://doi.org/10.1093/bioinformatics/btq559)
- O'Connell et al. 2014. A General Approach for Haplotype Phasing across the Full Spectrum of Relatedness. *PLoS Genetics*. [doi:10.1371/journal.pgen.1004234](https://doi.org/10.1371/journal.pgen.1004234)
- Gómez-Gálvez et al. 2026. An olive parentage atlas: founder cultivars, regional diversification, and implications for breeding programs. *BMC Plant Biology*. [doi:10.1186/s12870-026-08504-y](https://doi.org/10.1186/s12870-026-08504-y)
- Snyder-Mackler et al. 2016. Efficient Genome-Wide Sequencing and Low-Coverage Pedigree Analysis from Noninvasively Collected Samples. *Genetics*. [doi:10.1534/genetics.116.187492](https://doi.org/10.1534/genetics.116.187492)
- Noraz et al. 2026. Ancient DNA reveals 4000 years of grapevine diversity, viticulture and clonal propagation in France. *Nature Communications*. [doi:10.1038/s41467-026-70166-z](https://doi.org/10.1038/s41467-026-70166-z)
- Xiao et al. 2025. Impacts of reproductive systems on grapevine genome and breeding. *Nature Communications*. [doi:10.1038/s41467-025-56817-7](https://doi.org/10.1038/s41467-025-56817-7)
- de Oliveira et al. 2026. Genome-wide association study in a diverse grapevine collection provides insights into the genetic basis of berry size and cluster architecture traits. *PLOS One*. [doi:10.1371/journal.pone.0343491](https://doi.org/10.1371/journal.pone.0343491)
- Costantini et al. 2026. An advanced genotyping tool to inspect grapevine variability: the Axiom®Vitis22K SNP array. *Frontiers in Plant Science*. [doi:10.3389/fpls.2026.1771381](https://doi.org/10.3389/fpls.2026.1771381)
- Muranty et al. 2020. Using whole-genome SNP data to reconstruct a large multi-generation pedigree in apple germplasm. *BMC Plant Biology*. [doi:10.1186/s12870-019-2171-6](https://doi.org/10.1186/s12870-019-2171-6)
