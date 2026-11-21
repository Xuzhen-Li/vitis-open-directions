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

## Question

How common are polymorphic TE insertions in cultivated grape, which families are young, and do solo-LTR ratios differ between pangenome compartments?

## Hypotheses, planned figures and criteria

No results are given here. Each row says what would count as support; the exact thresholds go into the preregistration.

| Figure or table | Hypothesis or purpose | Criterion |
|---|---|---|
| Fig 1. Site frequency spectrum of TE insertions vs SNPs | TE insertions are shifted to rare frequencies. | Keep one sample per clone group (project 08) before building spectra; correct for genotypability of TE vs SNP sites; spectra with bootstrap intervals by accession. |
| Fig 2. Insertion age by polymorphism class | Polymorphic insertions are younger. | LTR divergence; one-sided test. |
| Fig 3. Solo-LTR ratio by compartment | The solo-to-intact ratio differs between core and dispensable regions. | Ratio with bootstrap intervals by compartment, with a local recombination-rate proxy as a covariate, because solo-LTRs form by recombination between the two LTRs. |

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

## Rough estimates

- Compute: medium [draft]
- Effort: 2–3 months for one person [draft]
- Target: genome journal [draft]

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
