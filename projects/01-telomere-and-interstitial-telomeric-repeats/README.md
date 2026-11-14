# 01. Telomeres and interstitial telomeric repeats across near-complete grape haplotypes

中文：近完整葡萄单倍型的端粒与间质端粒重复

Rank 1 of 22 (score F 3 + N 2 + E 3 = 8; see docs/RANKING.md) · Tier: Quick (E = 3, effort range ending at 6 weeks or less) · Origin: continued: started earlier and restarted here from public data under a new preregistration · Status: draft v0.3.2, 2026-11-14

## Gap

Telomere arrays are reported one assembly at a time. A comparison of telomere array length and interstitial telomeric repeat (ITS) positions across all public near-complete *Vitis* and Vitaceae haplotypes, with assembly technology as a covariate, was not found [待确认: repeat the search before writing].

**Existing work**

- [Shi et al. 2023](https://doi.org/10.1093/hr/uhad061): PN_T2T reference with telomeres at chromosome ends.
- [Liu et al. 2024](https://doi.org/10.1038/s41588-024-01967-5): nine T2T diploid grapes.
- [Wang et al. 2026](https://doi.org/10.1038/s41477-026-02442-1): chromosome-level genomes across Vitaceae.

**How this project differs**

Uses every public near-complete haplotype with one scan and one QC rule, separates biology from assembly technology, and places ITS relative to known karyotype changes.

## Question

How much do telomere array lengths and ITS positions vary among grape haplotypes, and are ITS clusters found where karyotype changes are known?

## Hypotheses, planned figures and criteria

No results are given here. Each row says what would count as support; the exact thresholds go into the preregistration.

| Figure or table | Hypothesis or purpose | Criterion |
|---|---|---|
| Fig 1. Telomere presence at every chromosome end, by assembly and technology | Not a hypothesis: a completeness table. | Share of chromosome ends with a telomere array; completeness cut-off and minimum array length (in repeat units) fixed in advance; assemblies below the cut-off are excluded from length analyses. |
| Fig 2. Telomere array length within accession (haplotype 1 vs 2) and between accessions | Between-accession variance exceeds within-accession variance after adjusting for technology. | Mixed model with technology as a fixed effect and haplotype nested in accession; variance components estimated by REML and tested by likelihood ratio or parametric bootstrap; supported if the 95% interval for the between-accession component excludes zero. |
| Fig 3. ITS positions on chromosomes | ITS loci are enriched near known rearrangement breakpoints, including the fusion point on *Vitis* chr7, where the segments homologous to *Muscadinia* chr7 and chr20 meet (located on Cabernet Sauvignon and PN40024 chr7 by Cochetel et al. 2021). | Within-chromosome permutation against positions matched for GC content, repeat class, and chromosome position; one-sided test fixed in advance. |
| Table 1. Per-haplotype telomere and ITS catalogue | Resource table. | Every row traceable to an accession and a tool version. |

## Preregistration

Before any data are analysed, fill in [`docs/PREREGISTRATION.md`](../../docs/PREREGISTRATION.md) for this project: hypotheses, primary outcome, sample inclusion rules, thresholds, stop rules and what will be reported if a hypothesis fails. Commit it with a date. Criteria from any earlier attempt are reference only and are not carried over.

## Data

| Module | Dataset |
|---|---|
| [DS01](../../data/DS01-pn40024-references/) | PN40024 references: PN_T2T (v5), PN40024.v4 and 12X |
| [DS02](../../data/DS02-grapepan-v1/) | Grapepan v1.0: T2T haplotypes, graphs and a 466-accession resequencing panel |
| [DS03](../../data/DS03-vitis-super-pangenome-72/) | Vitis super-pangenome: 72 haplotype-resolved accessions |
| [DS05](../../data/DS05-vitaceae-family-genomes/) | Vitaceae family chromosome-level genomes |
| [DS07](../../data/DS07-cultivated-16-pangenome/) | Cultivated grapevine pangenome (16 cultivars, Plastivigne) |
| [DS08](../../data/DS08-muscadinia-genomes/) | Muscadinia rotundifolia assemblies and reads |
| [DS16](../../data/DS16-vitaceae-assembly-index/) | Index of all Vitaceae assemblies in NCBI |
| [DS17](../../data/DS17-angiosperm-near-complete-assemblies/) | Near-complete angiosperm assemblies (comparison set) |

## Analysis steps

Shared modules, in order:

1. [AM01 · Download and verify](../../analyses/AM01-download-and-verify/)
2. [AM05 · Assembly QC](../../analyses/AM05-assembly-qc/)
3. [AM10 · Telomeres, centromeric satellites and rDNA arrays](../../analyses/AM10-repeat-arrays/)

Project-specific steps:

- Pick near-complete assemblies from DS16 (Vitaceae) and, as a comparison set, DS17.
- Run AM05 QC; drop assemblies that fail the preregistered completeness cut-off.
- Run tidk and TRF (AM10) on every haplotype; record array start, end and length.
- Map ITS positions to PN_T2T through whole-genome alignment and test enrichment at breakpoints, including the *Vitis* chr7 fusion point (shared with the centromere project).

## Paper design and split

| Paper | Working title | Type | Figures |
|---|---|---|---|
| A1 | Telomere and ITS variation across near-complete grape haplotypes | short paper or data note | Fig 1–3, Table 1 |
| A2 | Joint repeat-array paper with project 02 (rDNA) | optional merger | Figures of both projects |

Each paper: introduction from the gap above; one results section per figure; methods with tool versions from the modules; data availability listing every accession used and the derived tables.

## Risks and novelty check

- Risk: Array length in an assembly is a lower bound when reads do not span the array.
- Risk: Assemblers can trim telomeres; technology must be modelled.
- Risk: Novelty: no dedicated literature search on this topic has been done beyond the grape literature base yet [待确认: repeat the search before writing].
- Novelty: checked against the existing work above (Crossref-verified DOIs). Repeat the search before writing; anything marked [待确认] is not yet verified.

## Rough estimates

- Compute: small [draft]
- Effort: 3–6 weeks for one person [draft]
- Target: genome or plant genetics journal [draft]

## Continue on HPC

Run each step as its own job, in this order. Every job writes `.DONE` or `.FAILED` and a log; the next step starts only after `.DONE`. Template and rules: [`docs/HPC_JOBS.md`](../../docs/HPC_JOBS.md).

| Order | Step | Main tools | Resources (rough) |
|---|---|---|---|
| 1 | [AM01](../../analyses/AM01-download-and-verify/) Download and verify | ncbi-datasets-cli, sra-tools, ENA FTP / Aspera | 1–4 CPU, 4 GB, network; array over files |
| 2 | [AM05](../../analyses/AM05-assembly-qc/) Assembly QC | compleasm, BUSCO, Merqury | 16 CPU, 64 GB, 1–3 h per assembly; array |
| 3 | [AM10](../../analyses/AM10-repeat-arrays/) Telomeres, centromeric satellites and rDNA arrays | tidk, TRF, TRASH | 8 CPU, 16 GB per assembly |

Public inputs: [DS01](../../data/DS01-pn40024-references/), [DS02](../../data/DS02-grapepan-v1/), [DS03](../../data/DS03-vitis-super-pangenome-72/), [DS05](../../data/DS05-vitaceae-family-genomes/), [DS07](../../data/DS07-cultivated-16-pangenome/), [DS08](../../data/DS08-muscadinia-genomes/), [DS16](../../data/DS16-vitaceae-assembly-index/), [DS17](../../data/DS17-angiosperm-near-complete-assemblies/).

## References

- Shi et al. 2023. The complete reference genome for grapevine ( Vitis vinifera L.) genetics and breeding. *Horticulture Research*. [doi:10.1093/hr/uhad061](https://doi.org/10.1093/hr/uhad061)
- Liu et al. 2024. Grapevine pangenome facilitates trait genetics and genomic breeding. *Nature Genetics*. [doi:10.1038/s41588-024-01967-5](https://doi.org/10.1038/s41588-024-01967-5)
- Wang et al. 2026. Chromosome-level phylogenomics and genome evolution of the grape family. *Nature Plants*. [doi:10.1038/s41477-026-02442-1](https://doi.org/10.1038/s41477-026-02442-1)
