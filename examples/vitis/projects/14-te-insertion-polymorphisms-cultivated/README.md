# 14. TE insertion polymorphisms in cultivated grape from graph genotyping

中文：栽培葡萄的图泛基因组 TE 插入多态（含 solo-LTR）

Rank 14 of 22 (score F 2 + N 2 + E 2 = 6; see docs/RANKING.md) · Tier: Medium (E = 2, effort range ending after 6 weeks and by 4 months) · Origin: continued: started earlier and restarted here from public data under a new preregistration · Status: draft v0.3.2, 2026-11-14

## Gap

Population-scale TE insertion genotyping on a graph pangenome has been done for wild *V. amurensis* but not for cultivated *V. vinifera*. Solo-LTR formation across pangenome compartments was not found.

**Existing work**

- [Ma et al. 2026](https://doi.org/10.1038/s41467-026-70026-w): 330 wild V. amurensis; TE variants and climate.
- [Carrier et al. 2012](https://doi.org/10.1371/journal.pone.0032973): TEs as a main cause of somatic polymorphism in Pinot.
- [Vondras et al. 2019](https://doi.org/10.1186/s12864-019-6211-2): TE insertions in Zinfandel clones.
- [He et al. 2022](https://doi.org/10.1111/jse.12850): LTR retrotransposons in six Vitis genomes.
- [Wang et al. 2025](https://doi.org/10.21203/rs.3.rs-5867196/v1): a pangenome TE-discovery tool with grape as the example (preprint).

**How this project differs**

Cultivated panels, graph genotyping of insertions, and solo-LTR ratios in core and dispensable compartments.

**Background survey (literature read for this plan)**

Transposable elements (TEs) are a major and still under-genotyped source of plant variation ([Bourque et al. 2018](https://doi.org/10.1186/s13059-018-1577-z)). Population studies in other plants set the reference points: 602 tomato accessions carried 6,906 TE insertion polymorphisms (TIPs) from 337 families, mostly at low frequency and often near environmental-response genes ([Domínguez et al. 2020](https://doi.org/10.1038/s41467-020-17874-2)); in more than 1,000 wild *Arabidopsis thaliana* accessions, TE insertions arose at almost the same rate as base substitutions ([Baduel et al. 2021](https://doi.org/10.1186/s13059-021-02348-5)). Short-read TIP callers differ widely in accuracy, so detection must be benchmarked on real data ([Vendrell-Mir et al. 2019](https://doi.org/10.1186/s13100-019-0197-9)). LTR retrotransposons are also lost from genomes: solo-LTRs form by unequal homologous recombination and counterbalance amplification in rice ([Vitte and Panaud 2003](https://doi.org/10.1093/molbev/msg055)), and illegitimate recombination drives DNA loss in *Arabidopsis* ([Devos et al. 2002](https://doi.org/10.1101/gr.132102)).

In grape, a retrotransposon insertion explains white berries ([Kobayashi et al. 2004](https://doi.org/10.1126/science.1095011)), TEs are a main cause of somatic polymorphism in Pinot ([Carrier et al. 2012](https://doi.org/10.1371/journal.pone.0032973)), and TE insertions separate Zinfandel clones ([Vondras et al. 2019](https://doi.org/10.1186/s12864-019-6211-2)). LTR retrotransposons were compared across six *Vitis* genomes ([He et al. 2023](https://doi.org/10.1111/jse.12850)), TE families were identified from pangenome polymorphisms ([Sierra et al. 2024](https://doi.org/10.1186/s13100-024-00323-y)), and in wild *V. amurensis* a graph pangenome of 330 samples gave 127,094 TE-associated structural variants linked to climate ([Ma et al. 2026](https://doi.org/10.1038/s41467-026-70026-w)).

**Specific gap.** Graph-based TIP genotyping at population scale has been done for wild *V. amurensis* but not for cultivated *V. vinifera*, and solo-LTR ratios have not been compared between core and dispensable pangenome compartments [待确认].

## Question

How common are polymorphic TE insertions in cultivated grape, which families are young, and do solo-LTR ratios differ between pangenome compartments?

## Hypotheses, planned figures and criteria

No results are given here. Each row says what would count as support; the exact thresholds go into the preregistration.

| Figure or table | Hypothesis or purpose | Criterion |
|---|---|---|
| Fig 1. Site frequency spectrum of TE insertions vs SNPs | TE insertions are shifted to rare frequencies. | Keep one sample per clone group (project 08) before building spectra; correct for genotypability of TE vs SNP sites; spectra with bootstrap intervals by accession. |
| Fig 2. Insertion age by polymorphism class | Polymorphic insertions are younger. | LTR divergence; one-sided test. |
| Fig 3. Solo-LTR ratio by compartment | The solo-to-intact ratio differs between core and dispensable regions. | Ratio with bootstrap intervals by compartment, with a local recombination-rate proxy as a covariate, because solo-LTRs form by recombination between the two LTRs. |

**Expected results and how they will be read**

- Fig 1: a TIP frequency spectrum shifted to rare classes relative to SNPs, as in tomato, would fit purifying selection or recent activity; clonal propagation and sampling of identity groups are accounted for before reading it.
- Fig 2: younger LTR insertion ages (LTR divergence) in polymorphic than in fixed insertions would support recent activity of those families; the families are named in a table.
- Fig 3: a different solo-to-intact ratio between core and dispensable regions would fit compartment-specific removal; equal ratios are reported as no difference.

## Preregistration

Before any data are analysed, fill in [`docs/PREREGISTRATION.md`](../../../../templates/PREREGISTRATION.md) for this project: hypotheses, primary outcome, sample inclusion rules, thresholds, stop rules and what will be reported if a hypothesis fails. Commit it with a date. Criteria from any earlier attempt are reference only and are not carried over.

## Data

| Module | Dataset |
|---|---|
| [DS02](../../data/DS02-grapepan-v1/) | Grapepan v1.0: T2T haplotypes, graphs and a 466-accession resequencing panel |
| [DS03](../../data/DS03-vitis-super-pangenome-72/) | Vitis super-pangenome: 72 haplotype-resolved accessions |
| [DS07](../../data/DS07-cultivated-16-pangenome/) | Cultivated grapevine pangenome (16 cultivars, Plastivigne) |
| [DS10](../../data/DS10-reseq-472-vitis/) | Resequencing of 472 Vitis accessions (and the 2017 domestication panel) |
| [DS12](../../data/DS12-reseq-204-magris2021/) | Resequencing of 204 V. vinifera accessions (Magris et al. 2021) |
| [DS01](../../data/DS01-pn40024-references/) | PN40024 references: PN_T2T (v5), PN40024.v4 and 12X |

**How each dataset is used**

| Module | Role in this project |
|---|---|
| DS02, DS03, DS07 | Haplotypes for discovery of insertions among assemblies and for the graph |
| DS10, DS12 | Cultivated and wild short-read panels for graph genotyping |
| DS01 | PN_T2T coordinates and its TE annotation |

New public data: none needed. The TE library comes from the public vitis-te catalogue; it is not rebuilt here.

## Analysis steps

Shared modules, in order:

1. [AM01 · Download and verify](../../analyses/AM01-download-and-verify/)
2. [AM05 · Assembly QC](../../analyses/AM05-assembly-qc/)
3. [AM06 · Whole-genome alignment, synteny and SVs from assemblies](../../analyses/AM06-wga-and-sv/)
4. [AM19 · TE insertion polymorphisms among haplotypes](../../analyses/AM19-te-insertion-polymorphism/)
5. [AM07 · Pangenome graph build and genotyping](../../analyses/AM07-graph-build-and-genotype/)

Project-specific steps:

- Use a curated TE library from vitis-te (not built here).
- Call insertions among haplotypes (AM19).
- Genotype in short-read panels through the graph (AM07).
- Classify solo and intact LTRs.

**Stepwise work plan with tools**

| Step | Work | Tools (paper) | Output |
|---|---|---|---|
| 1 | Take a curated grape TE library (vitis-te) and annotate every haplotype | RepeatMasker, EDTA ([Ou et al. 2019](https://doi.org/10.1186/s13059-019-1905-y)) | TE annotations |
| 2 | Call TE insertions among haplotypes from whole-genome alignments | SyRI, AM19 tools | TIP catalogue |
| 3 | Add TIPs to the graph and genotype short-read panels | PanGenie ([Ebler et al. 2022](https://doi.org/10.1038/s41588-022-01043-w)) or vg (AM07) | TIP genotypes |
| 4 | Check genotyping by downsampling samples with assemblies | vg, custom | Accuracy table |
| 5 | LTR ages from LTR divergence; solo versus intact classification | LTR_retriever ([Ou and Jiang 2018](https://doi.org/10.1104/pp.17.01310)) | Age and solo tables |
| 6 | Site frequency spectra (one sample per identity group) and compartment tests | R | Fig 1 to Fig 3 |

## Paper design and split

| Paper | Working title | Type | Figures |
|---|---|---|---|
| N1 | TE insertion polymorphisms in cultivated grape | main paper | Fig 1–2 |
| N2 | Solo-LTR formation across the grape pangenome | short paper | Fig 3 |

Each paper: introduction from the gap above; one results section per figure; methods with tool versions from the modules; data availability listing every accession used and the derived tables.

## Risks and novelty check

- Risk: Depends on the TE library; classification errors propagate.
- Risk: Graph genotyping of insertions inside repeats is less accurate.
- Novelty: checked against the existing work above (Crossref-verified DOIs). Repeat the search before writing; anything marked [待确认] is not yet verified.

## Risks and how to handle them

Added 2026-11-26. Each row names a risk, the evidence behind it, and a concrete check or fallback. Sources cited here were read for this section and their DOIs were checked on Crossref; preprints are marked.

| Area | Risk | Check or mitigation |
|---|---|---|
| Data access and licence | Graphs, assemblies and INSDC resequencing panels are listed as available ([data/DOWNLOADS.md](../../data/DOWNLOADS.md)); INSDC data are free and open ([INSDC 2024](https://doi.org/10.1093/nar/gkae1058)). | Freeze the run list. |
| Method failure | Graph-based TIP pipelines report high precision and recall on simulated and real data ([Groza et al. 2024](https://doi.org/10.1038/s41467-024-53294-2)), but performance inside repeats is lower (see above), and short-read tools differ ([Chu et al. 2021](https://doi.org/10.1038/s41467-021-24041-8)). | Use GraffiTE for graph genotyping and one read-based caller (xTea) as a cross-check; measure concordance against assemblies of the same accessions. |
| Graph construction | Graph builders differ in completeness and SV fidelity ([Kopalli et al. 2025](https://doi.org/10.1093/gigascience/giaf121)). | Report which builder produced the graph and repeat key counts on a second graph. |
| Library dependence | Family calls depend on the TE library (see above). | Fix the library version (project 25 output or a published library) and report counts by library. |
| Clones, synonyms and pedigree | SVs among Pinot noir clones lie mostly in repetitive DNA ([Callipo et al. 2026](https://doi.org/10.1186/s13059-026-04184-x)); some TIPs may be clonal rather than inherited. | Collapse clones to one genotype for population frequencies; analyse clone-specific TIPs separately. |
| Reference bias and genome choice | Insertions absent from the graph cannot be genotyped from short reads. | Report how many TIPs are discoverable only from assemblies. |
| Sample size and power | Age and frequency of young families need many carriers. | Fix a minimum allele count for family-level statistics. |
| Computing cost | Graph genotyping of hundreds of samples is the main cost. | Time ten samples first. |

**Recent and competing work (search of 2024 to 2026 literature on 2026-11-26)**

- In rice, a pangenome graph and 165 resequenced accessions gave 30,316 TIP sites and TIP-GWAS hits for cold tolerance ([Qian et al. 2025](https://doi.org/10.1038/s41467-025-62887-4)). Graph TIP studies in crops are established; for cultivated grape no such study was found.

**What would end the idea, and the fallback.** If concordance in repeats is too low, short-read TIPs are not reliable. The fallback is a TIP catalogue from assemblies only, with frequencies from the assembled haplotypes.

**Journal-level realism.** Mid-field genome biology; the rice study shows that a broad venue expects a trait link, which this plan does not promise.

## Reference study in another species

Added 2026-11-26. Published studies that already did this kind of work in another species, to plan the grape version against. Every DOI was checked on Crossref. Figures are described, not copied; a figure redrawn for a grape paper would be marked "Redrawn after" its source. The last bullet for each study lists what a grape results section would need; it is a planning suggestion, not a finding of that study.

### Domínguez et al. 2020

- **Paper:** [Domínguez et al. 2020](https://doi.org/10.1038/s41467-020-17874-2), *Nature Communications*.
- **Species:** Tomato, 602 accessions.
- **What was done:** Transposon insertion polymorphisms (TIPs) were detected in 602 accessions; their distribution and effect on transcription were analysed, and a TIP-based GWAS found key insertions that affect flavour.
- **Figures:** Fig. 1 the tomato mobilome and phylogeny of the 602 accessions; Fig. 2 TIP landscape and transcriptional effects; Fig. 3 TIPs as a hidden source of phenotypic variation (linkage disequilibrium and GWAS); Fig. 4 TIPs and secondary metabolism; Fig. 5 a key TIP affecting flavour.
- **What a grape results section would need:** TIP detection and validation; frequency and differentiation; TIPs in relation to expression; a TIP-based GWAS.

### Qian et al. 2025

- **Paper:** [Qian et al. 2025](https://doi.org/10.1038/s41467-025-62887-4), *Nature Communications* (PMC12357961). Licence CC BY 4.0: figures may be reused with credit; none are copied here.
- **Species:** rice, 165 accessions on a pangenome graph.
- **What was done:** 30,316 transposable element insertion polymorphism (TIP) sites were found; polymorphic TEs showed more H3K27me3; 26,914 TEs responded to cold in transcriptome data; a TIP-based GWAS found two cold-tolerance genes, confirmed with knockout and overexpression lines.
- **Figures:** Fig. 1 genomic features and population structure; Fig. 2 the TIP pipeline and transcriptional and epigenetic features of polymorphic TEs; Fig. 3 cold-responsive TEs and genes; Fig. 4 GWAS on the TIP map; Fig. 5 functional tests of the two genes.
- **What its results section needed:** a TIP map with a stated pipeline, features of polymorphic TEs, expression links, an association scan, and a functional test.
- **Grape version:** Fig. 1 to 4 equivalents from public grape data; laboratory tests are outside this project, so Fig. 5 is replaced by expression association of TIPs near genes (project 19) and genotyping accuracy checked on long-read assemblies.

### Q1-level bar

Target: a first-quartile (Q1) journal in plant science, genetics or evolution. Quartile lists change each year, so the journal is chosen from the current list at submission [to confirm]. To compete at that level, the grape paper needs: a TIP map with measured genotyping accuracy, a link to expression, and at least one association with a trait, as in the tomato study.

## Rough estimates

- Compute: medium [draft]
- Effort: 2–3 months for one person [draft]
- Target: genome journal [draft]

## Suggested journal level (suggestion only)

**Mid-field journal (genome biology or plant genomics).** Population TIP studies read here appeared in *Nature Communications* (tomato, *V. amurensis*) and *Genome Biology* (*Arabidopsis*); grape TE studies in *PLOS ONE*, *BMC Genomics*, *Journal of Systematics and Evolution* and *Mobile DNA*. A cultivated-grape graph TIP study with a compartment analysis fits a mid-field venue. This is a suggestion, not a decision; impact factors are not used.

## Continue on HPC

Run each step as its own job, in this order. Every job writes `.DONE` or `.FAILED` and a log; the next step starts only after `.DONE`. Template and rules: [`docs/HPC_JOBS.md`](../../../../templates/HPC_JOBS.md).

| Order | Step | Main tools | Resources (rough) |
|---|---|---|---|
| 1 | [AM01](../../analyses/AM01-download-and-verify/) Download and verify | ncbi-datasets-cli, sra-tools, ENA FTP / Aspera | 1–4 CPU, 4 GB, network; array over files |
| 2 | [AM05](../../analyses/AM05-assembly-qc/) Assembly QC | compleasm, BUSCO, Merqury | 16 CPU, 64 GB, 1–3 h per assembly; array |
| 3 | [AM06](../../analyses/AM06-wga-and-sv/) Whole-genome alignment, synteny and SVs from assemblies | minimap2, SyRI, AnchorWave | 16 CPU, 64 GB, 1–4 h per haplotype; array |
| 4 | [AM19](../../analyses/AM19-te-insertion-polymorphism/) TE insertion polymorphisms among haplotypes | GraffiTE, McClintock 2, RepeatMasker | 16–32 CPU, 128 GB |
| 5 | [AM07](../../analyses/AM07-graph-build-and-genotype/) Pangenome graph build and genotyping | Minigraph-Cactus, PGGB, vg | 32–64 CPU, 256–512 GB for graph builds; 16 CPU, 64 GB per sample for giraffe |

Public inputs: [DS02](../../data/DS02-grapepan-v1/), [DS03](../../data/DS03-vitis-super-pangenome-72/), [DS07](../../data/DS07-cultivated-16-pangenome/), [DS10](../../data/DS10-reseq-472-vitis/), [DS12](../../data/DS12-reseq-204-magris2021/), [DS01](../../data/DS01-pn40024-references/).

## References

- Ma et al. 2026. Population genomics reveals association of transposable elements variants with climatic adaptation in wild Amur grape. *Nature Communications*. [doi:10.1038/s41467-026-70026-w](https://doi.org/10.1038/s41467-026-70026-w)
- Carrier et al. 2012. Transposable Elements Are a Major Cause of Somatic Polymorphism in Vitis vinifera L.. *PLoS ONE*. [doi:10.1371/journal.pone.0032973](https://doi.org/10.1371/journal.pone.0032973)
- Vondras et al. 2019. The genomic diversification of grapevine clones. *BMC Genomics*. [doi:10.1186/s12864-019-6211-2](https://doi.org/10.1186/s12864-019-6211-2)
- He et al. 2022. Characterization of genome‐wide long terminal repeat retrotransposons provide insights into trait evolution of four grapevine species. *Journal of Systematics and Evolution*. [doi:10.1111/jse.12850](https://doi.org/10.1111/jse.12850)
- Wang et al. 2025. PanTE: A Comprehensive Framework for Transposable Element Discovery in Graph-based Pangenomes. *Research Square*. [doi:10.21203/rs.3.rs-5867196/v1](https://doi.org/10.21203/rs.3.rs-5867196/v1)
- Baduel et al. 2021. Genetic and environmental modulation of transposition shapes the evolutionary potential of Arabidopsis thaliana. *Genome Biology*. [doi:10.1186/s13059-021-02348-5](https://doi.org/10.1186/s13059-021-02348-5)
- Bourque et al. 2018. Ten things you should know about transposable elements. *Genome Biology*. [doi:10.1186/s13059-018-1577-z](https://doi.org/10.1186/s13059-018-1577-z)
- Devos et al. 2002. Genome Size Reduction through Illegitimate Recombination Counteracts Genome Expansion in Arabidopsis. *Genome Research*. [doi:10.1101/gr.132102](https://doi.org/10.1101/gr.132102)
- Domínguez et al. 2020. The impact of transposable elements on tomato diversity. *Nature Communications*. [doi:10.1038/s41467-020-17874-2](https://doi.org/10.1038/s41467-020-17874-2)
- Ebler et al. 2022. Pangenome-based genome inference allows efficient and accurate genotyping across a wide spectrum of variant classes. *Nature Genetics*. [doi:10.1038/s41588-022-01043-w](https://doi.org/10.1038/s41588-022-01043-w)
- Kobayashi et al. 2004. Retrotransposon-Induced Mutations in Grape Skin Color. *Science*. [doi:10.1126/science.1095011](https://doi.org/10.1126/science.1095011)
- Ou et al. 2018. LTR_retriever: A Highly Accurate and Sensitive Program for Identification of Long Terminal Repeat Retrotransposons. *Plant Physiology*. [doi:10.1104/pp.17.01310](https://doi.org/10.1104/pp.17.01310)
- Ou et al. 2019. Benchmarking transposable element annotation methods for creation of a streamlined, comprehensive pipeline. *Genome Biology*. [doi:10.1186/s13059-019-1905-y](https://doi.org/10.1186/s13059-019-1905-y)
- Sierra et al. 2024. Identification of transposable element families from pangenome polymorphisms. *Mobile DNA*. [doi:10.1186/s13100-024-00323-y](https://doi.org/10.1186/s13100-024-00323-y)
- Vendrell-Mir et al. 2019. A benchmark of transposon insertion detection tools using real data. *Mobile DNA*. [doi:10.1186/s13100-019-0197-9](https://doi.org/10.1186/s13100-019-0197-9)
- Vitte et al. 2003. Formation of Solo-LTRs Through Unequal Homologous Recombination Counterbalances Amplifications of LTR Retrotransposons in Rice Oryza sativa L. *Molecular Biology and Evolution*. [doi:10.1093/molbev/msg055](https://doi.org/10.1093/molbev/msg055)
- INSDC 2024. The international nucleotide sequence database collaboration (INSDC): enhancing global participation. *Nucleic Acids Research*. [doi:10.1093/nar/gkae1058](https://doi.org/10.1093/nar/gkae1058)
- Groza et al. 2024. A unified framework to analyze transposable element insertion polymorphisms using graph genomes. *Nature Communications*. [doi:10.1038/s41467-024-53294-2](https://doi.org/10.1038/s41467-024-53294-2)
- Chu et al. 2021. Comprehensive identification of transposable element insertions using multiple sequencing technologies. *Nature Communications*. [doi:10.1038/s41467-021-24041-8](https://doi.org/10.1038/s41467-021-24041-8)
- Kopalli et al. 2025. Toward a standardized framework for pangenome graph evaluation: assessing crop plant pangenome variation graph construction from multiple assemblies. *GigaScience*. [doi:10.1093/gigascience/giaf121](https://doi.org/10.1093/gigascience/giaf121)
- Callipo et al. 2026. A dual genome-methylome map of clonal evolution in grapevine. *Genome Biology*. [doi:10.1186/s13059-026-04184-x](https://doi.org/10.1186/s13059-026-04184-x)
- Qian et al. 2025. Pangenome analysis of transposable element insertion polymorphisms reveals features underlying cold tolerance in rice. *Nature Communications*. [doi:10.1038/s41467-025-62887-4](https://doi.org/10.1038/s41467-025-62887-4)
