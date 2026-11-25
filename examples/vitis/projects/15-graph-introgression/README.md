# 15. Introgression on a graph pangenome: wild-to-cultivated and hybrid cultivars

中文：图泛基因组上的野生到栽培渗入与杂交品种单倍型着色

Rank 15 of 22 (score F 2 + N 2 + E 2 = 6; see docs/RANKING.md) · Tier: Medium (E = 2, effort range ending after 6 weeks and by 4 months) · Origin: new · Status: draft v0.3.2, 2026-11-14

## Gap

Introgression into cultivated grape was mapped with SNPs on linear references. Introgression at the SV level on a graph pangenome, and multi-species haplotype painting of commercial hybrids and rootstocks on T2T or graph references, were not found.

**Existing work**

- [Xiao et al. 2023](https://doi.org/10.1073/pnas.2222041120): adaptive and maladaptive introgression on a linear reference.
- [Freitas et al. 2021](https://doi.org/10.1126/sciadv.abi8584): hybridisation with local wild relatives.
- [Sawler et al. 2013](https://doi.org/10.1371/journal.pone.0080791): ancestry deconvolution in hybrid grapes.
- [Delame et al. 2018](https://doi.org/10.1007/s00122-018-3260-x): introgression reshapes recombination in interspecific hybrids.
- [Morales-Cruz et al. 2021](https://doi.org/10.1186/s13059-021-02467-z): introgression among North American wild grapes.
- [Wang et al. 2026](https://doi.org/10.1073/pnas.2607754123): introgression and parallel adaptation across North American Vitis.

**How this project differs**

Uses graph genotypes so introgressed SVs are seen, and paints hybrid genomes with several donor species.

**Background survey (literature read for this plan)**

Introgression into cultivated grape is well documented with SNPs on linear references. Over 1,000 USDA samples showed a Near East origin and introgression from wild grapes into cultivars ([Myles et al. 2011](https://doi.org/10.1073/pnas.1009363108)); Western European varieties show pervasive hybridisation with local wild relatives, strongest in a subset of Iberian varieties ([Freitas et al. 2021](https://doi.org/10.1126/sciadv.abi8584)); 345 samples supported a single domestication followed by continuous gene flow from European wild grapes, with adaptive and maladaptive introgression ([Xiao et al. 2023](https://doi.org/10.1073/pnas.2222041120)). Commercial hybrids and rootstocks carry ancestry from several species: ancestry deconvolution was shown with GBS ([Sawler et al. 2013](https://doi.org/10.1371/journal.pone.0080791)), and 64 hybrid cultivars were assigned ancestry from 7 wild *Vitis* and 7 *V. vinifera* references ([Migicovsky et al. 2016](https://doi.org/10.1186/s12864-016-2834-8)). Introgression also reshapes recombination in interspecific hybrids ([Delame et al. 2019](https://doi.org/10.1007/s00122-018-3260-x)).

Among wild North American grapes, introgression fuels biotic and abiotic adaptation ([Morales-Cruz et al. 2021](https://doi.org/10.1186/s13059-021-02467-z)) and shows parallel adaptation across species ([Wang et al. 2026](https://doi.org/10.1073/pnas.2607754123)). Methods are standard: ABBA-BABA statistics and f_dM for windows ([Martin et al. 2015](https://doi.org/10.1093/molbev/msu269)), Dsuite for many trios from VCF ([Malinsky et al. 2021](https://doi.org/10.1111/1755-0998.13265)), and RFMix for local ancestry ([Maples et al. 2013](https://doi.org/10.1016/j.ajhg.2013.06.020)). Graph genotyping makes SVs visible in short-read panels ([Sirén et al. 2021](https://doi.org/10.1126/science.abg8871); [Ebler et al. 2022](https://doi.org/10.1038/s41588-022-01043-w)).

**Specific gap.** No grape study was found that maps introgressed SVs from graph genotypes, compares SV and SNP introgression tracts, and paints hybrid cultivars and rootstocks with several donor species on a T2T or graph reference [待确认].

## Question

Which introgressed segments carry SVs that SNP-based maps miss, and how are donor species arranged along the genomes of hybrid cultivars and rootstocks?

## Hypotheses, planned figures and criteria

No results are given here. Each row says what would count as support; the exact thresholds go into the preregistration.

| Figure or table | Hypothesis or purpose | Criterion |
|---|---|---|
| Fig 1. SV vs SNP introgression tracts | Most SV tracts fall inside SNP tracts; some SV-only tracts exist. | Null by circular shifts of tracts within chromosomes, restricted to callable and genotypable regions while preserving tract lengths; coalescent simulations with incomplete lineage sorting and no introgression give the null for tract length and SV overlap; genome-wide D and f4 with block-jackknife Z, using blocks of a size fixed in advance and larger than the LD-decay distance (default 5 Mb [待确认: check against LD decay]); the callable and genotypable mask version is fixed before the run; windowed f_dM for local signals. SV-only tracts are reported only when confirmed in a long-read or assembly validation subset, stratified by genotyping accuracy. |
| Fig 2. Introgressed SVs near genes | Introgressed SVs are enriched near genes of adaptive traits. | Matched SVs by length, type, frequency, distance to gene, recombination rate, and mappability; adaptive-trait gene sets fixed in advance from named sources; BH FDR within the family of gene sets. |
| Fig 3. Painting of hybrid cultivars | Donor ancestry blocks match recorded pedigrees. | Agreement = difference between inferred donor proportions and pedigree expectations, with interval coverage; discordant cultivars counted; sensitivity to pedigree errors; minimum donor-panel size fixed in advance and segments without an adequate donor labelled unassigned. |

**Expected results and how they will be read**

- Fig 1: SV-only tracts (not seen with SNPs) are the new contribution; if there are none, SNP maps are shown to be sufficient for introgression in grape.
- Fig 2: enrichment of introgressed SVs near adaptive-trait genes is tested against matched windows; a positive result is a list of candidates, not proof of adaptation.
- Fig 3: donor blocks that match recorded pedigrees validate the painting; mismatches are flagged as pedigree or label questions for project 23.

## Preregistration

Before any data are analysed, fill in [`docs/PREREGISTRATION.md`](../../../../templates/PREREGISTRATION.md) for this project: hypotheses, primary outcome, sample inclusion rules, thresholds, stop rules and what will be reported if a hypothesis fails. Commit it with a date. Criteria from any earlier attempt are reference only and are not carried over.

## Data

| Module | Dataset |
|---|---|
| [DS02](../../data/DS02-grapepan-v1/) | Grapepan v1.0: T2T haplotypes, graphs and a 466-accession resequencing panel |
| [DS03](../../data/DS03-vitis-super-pangenome-72/) | Vitis super-pangenome: 72 haplotype-resolved accessions |
| [DS04](../../data/DS04-na-vitis-super-pangenome/) | North American Vitis super-pangenome and wild resequencing |
| [DS19](../../data/DS19-wild-vitis-extra-panels/) | Extra wild Vitis panels (V. riparia, V. californica, 40 Vitis species) |
| [DS10](../../data/DS10-reseq-472-vitis/) | Resequencing of 472 Vitis accessions (and the 2017 domestication panel) |
| [DS12](../../data/DS12-reseq-204-magris2021/) | Resequencing of 204 V. vinifera accessions (Magris et al. 2021) |
| [DS01](../../data/DS01-pn40024-references/) | PN40024 references: PN_T2T (v5), PN40024.v4 and 12X |

**How each dataset is used**

| Module | Role in this project |
|---|---|
| DS02, DS03 | Graph and haplotypes; donors from wild *V. vinifera* and other species |
| DS04, DS19 | North American and extra wild *Vitis* panels as donor references |
| DS10, DS12 | Cultivated and wild *V. vinifera* panels; hybrid cultivars and rootstocks where present |
| DS01 | PN_T2T coordinates |

New public data: none needed. Which hybrid cultivars and rootstocks are in public panels is [待确认].

## Analysis steps

Shared modules, in order:

1. [AM01 · Download and verify](../../analyses/AM01-download-and-verify/)
2. [AM03 · Short-read mapping and small-variant calling](../../analyses/AM03-short-read-variants/)
3. [AM07 · Pangenome graph build and genotyping](../../analyses/AM07-graph-build-and-genotype/)
4. [AM13 · Ancestry and introgression](../../analyses/AM13-ancestry-and-introgression/)
5. [AM18 · Long-read SV calling](../../analyses/AM18-long-read-sv/)

Project-specific steps:

- Genotype SVs in panels through the graph (AM07); validate a subset with long reads or assemblies (AM18).
- Infer introgression with D/f4, f_dM, and local ancestry (AM13); simulate the ILS-only null.
- Paint hybrid cultivars with donor panels chosen in advance.

**Stepwise work plan with tools**

| Step | Work | Tools (paper) | Output |
|---|---|---|---|
| 1 | Sample sets: recipients, donors, outgroup; one per identity group (project 08) | AM04 | Sample table |
| 2 | SNP calls and graph SV genotypes | AM03, PanGenie or vg (AM07) | SNP and SV VCFs |
| 3 | Validate a subset of SVs with long reads or assemblies | AM18 | Validation table |
| 4 | D, f4 and f_dM in windows; ILS-only null by simulation | Dsuite, msprime (AM13) | Tract calls |
| 5 | Local ancestry painting of hybrids with preregistered donor panels | RFMix | Painted genomes |
| 6 | Compare SV and SNP tracts; enrichment near trait genes | bedtools, R | Fig 1 to Fig 3 |

## Paper design and split

| Paper | Working title | Type | Figures |
|---|---|---|---|
| O1 | Structural-variant introgression in cultivated grape | main paper | Fig 1–2 |
| O2 | Multi-species ancestry of grape hybrids and rootstocks | paper | Fig 3 |

Each paper: introduction from the gap above; one results section per figure; methods with tool versions from the modules; data availability listing every accession used and the derived tables.

## Risks and novelty check

- Risk: Donor panels may be incomplete for some species.
- Risk: Graph SV genotypes in diverged haplotypes are less accurate.
- Novelty: checked against the existing work above (Crossref-verified DOIs). Repeat the search before writing; anything marked [待确认] is not yet verified.

## Rough estimates

- Compute: medium to large [draft]
- Effort: 3–4 months for one person [draft]
- Target: genetics journal [draft]

## Suggested journal level (suggestion only)

**Mid-field journal (genetics or molecular ecology).** Grape introgression papers read here appeared in *PNAS*, *Science Advances*, *Genome Biology*, *BMC Genomics*, *PLOS ONE* and *Theoretical and Applied Genetics*. An SV-level re-analysis with hybrid painting fits a mid-field venue; broad interest would need SV-only adaptive tracts with strong support. This is a suggestion, not a decision; impact factors are not used.

## Continue on HPC

Run each step as its own job, in this order. Every job writes `.DONE` or `.FAILED` and a log; the next step starts only after `.DONE`. Template and rules: [`docs/HPC_JOBS.md`](../../../../templates/HPC_JOBS.md).

| Order | Step | Main tools | Resources (rough) |
|---|---|---|---|
| 1 | [AM01](../../analyses/AM01-download-and-verify/) Download and verify | ncbi-datasets-cli, sra-tools, ENA FTP / Aspera | 1–4 CPU, 4 GB, network; array over files |
| 2 | [AM03](../../analyses/AM03-short-read-variants/) Short-read mapping and small-variant calling | bwa-mem2, samtools, DeepVariant | 16 CPU, 64 GB, 6–24 h per sample (DeepVariant); joint step 32 CPU, 128 GB |
| 3 | [AM07](../../analyses/AM07-graph-build-and-genotype/) Pangenome graph build and genotyping | Minigraph-Cactus, PGGB, vg | 32–64 CPU, 256–512 GB for graph builds; 16 CPU, 64 GB per sample for giraffe |
| 4 | [AM13](../../analyses/AM13-ancestry-and-introgression/) Ancestry and introgression | ADMIXTURE, Dsuite, ADMIXTOOLS 2 | 8 CPU, 32 GB |
| 5 | [AM18](../../analyses/AM18-long-read-sv/) Long-read SV calling | Sniffles2, cuteSV, pbsv | 16 CPU, 64 GB per sample |

Public inputs: [DS02](../../data/DS02-grapepan-v1/), [DS03](../../data/DS03-vitis-super-pangenome-72/), [DS04](../../data/DS04-na-vitis-super-pangenome/), [DS19](../../data/DS19-wild-vitis-extra-panels/), [DS10](../../data/DS10-reseq-472-vitis/), [DS12](../../data/DS12-reseq-204-magris2021/), [DS01](../../data/DS01-pn40024-references/).

## References

- Xiao et al. 2023. Adaptive and maladaptive introgression in grapevine domestication. *Proceedings of the National Academy of Sciences*. [doi:10.1073/pnas.2222041120](https://doi.org/10.1073/pnas.2222041120)
- Freitas et al. 2021. Pervasive hybridization with local wild relatives in Western European grapevine varieties. *Science Advances*. [doi:10.1126/sciadv.abi8584](https://doi.org/10.1126/sciadv.abi8584)
- Sawler et al. 2013. Genomics Assisted Ancestry Deconvolution in Grape. *PLoS ONE*. [doi:10.1371/journal.pone.0080791](https://doi.org/10.1371/journal.pone.0080791)
- Delame et al. 2018. Introgression reshapes recombination distribution in grapevine interspecific hybrids. *Theoretical and Applied Genetics*. [doi:10.1007/s00122-018-3260-x](https://doi.org/10.1007/s00122-018-3260-x)
- Morales-Cruz et al. 2021. Introgression among North American wild grapes (Vitis) fuels biotic and abiotic adaptation. *Genome Biology*. [doi:10.1186/s13059-021-02467-z](https://doi.org/10.1186/s13059-021-02467-z)
- Wang et al. 2026. The dynamics of introgression and parallel adaptation across North American Vitis species. *Proceedings of the National Academy of Sciences*. [doi:10.1073/pnas.2607754123](https://doi.org/10.1073/pnas.2607754123)
- Ebler et al. 2022. Pangenome-based genome inference allows efficient and accurate genotyping across a wide spectrum of variant classes. *Nature Genetics*. [doi:10.1038/s41588-022-01043-w](https://doi.org/10.1038/s41588-022-01043-w)
- Malinsky et al. 2021. Dsuite ‐ Fast D ‐statistics and related admixture evidence from VCF files. *Molecular Ecology Resources*. [doi:10.1111/1755-0998.13265](https://doi.org/10.1111/1755-0998.13265)
- Maples et al. 2013. RFMix: A Discriminative Modeling Approach for Rapid and Robust Local-Ancestry Inference. *The American Journal of Human Genetics*. [doi:10.1016/j.ajhg.2013.06.020](https://doi.org/10.1016/j.ajhg.2013.06.020)
- Martin et al. 2015. Evaluating the Use of ABBA–BABA Statistics to Locate Introgressed Loci. *Molecular Biology and Evolution*. [doi:10.1093/molbev/msu269](https://doi.org/10.1093/molbev/msu269)
- Migicovsky et al. 2016. Genomic ancestry estimation quantifies use of wild species in grape breeding. *BMC Genomics*. [doi:10.1186/s12864-016-2834-8](https://doi.org/10.1186/s12864-016-2834-8)
- Myles et al. 2011. Genetic structure and domestication history of the grape. *Proceedings of the National Academy of Sciences*. [doi:10.1073/pnas.1009363108](https://doi.org/10.1073/pnas.1009363108)
- Sirén et al. 2021. Pangenomics enables genotyping of known structural variants in 5202 diverse genomes. *Science*. [doi:10.1126/science.abg8871](https://doi.org/10.1126/science.abg8871)
