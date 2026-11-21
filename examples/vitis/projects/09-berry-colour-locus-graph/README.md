# 09. Graph genotyping of the berry colour locus

中文：果皮颜色位点的图基因组分型

Rank 9 of 22 (score F 3 + N 1 + E 3 = 7; see docs/RANKING.md) · Tier: Quick (E = 3, effort range ending at 6 weeks or less) · Origin: new · Status: draft v0.3.2, 2026-11-14

## Gap

The colour locus and its somatic sports are well described. Genotyping its structural haplotypes from short reads through a graph, across public panels, was not found [待确认].

**Existing work**

- [Kobayashi et al. 2004](https://doi.org/10.1126/science.1095011): retrotransposon-induced mutations at the colour locus.
- [Pelsy et al. 2015](https://doi.org/10.1371/journal.pgen.1005081): chromosome replacement and deletion in colour sports.
- [Carbonell-Bejerano et al. 2017](https://doi.org/10.1104/pp.17.00715): unbalanced rearrangements in colour loss.
- [Reynard et al. 2025](https://doi.org/10.1093/hr/uhaf069): a divergent haplotype with a large deletion at the colour locus.

**How this project differs**

Builds a locus graph from all near-complete haplotypes and genotypes structural haplotypes in public panels.

## Question

Can graph genotyping recover colour-locus haplotypes from short reads well enough to predict berry colour?

## Hypotheses, planned figures and criteria

No results are given here. Each row says what would count as support; the exact thresholds go into the preregistration.

| Figure or table | Hypothesis or purpose | Criterion |
|---|---|---|
| Fig 1. Locus graph | Not a hypothesis: graph of all haplotypes. | Built from near-complete haplotypes only. |
| Fig 2. Genotype vs recorded berry colour | Graph genotypes at VvMybA1 and VvMybA2 together predict recorded berry colour. | Accuracy per colour class with Wilson 95% intervals (classes are unbalanced); colour sports are listed separately and excluded from accuracy calculations. |
| Fig 3. Haplotype frequencies by group | Descriptive. | Counts by panel and group. |

## Preregistration

Before any data are analysed, fill in [`docs/PREREGISTRATION.md`](../../../../templates/PREREGISTRATION.md) for this project: hypotheses, primary outcome, sample inclusion rules, thresholds, stop rules and what will be reported if a hypothesis fails. Commit it with a date. Criteria from any earlier attempt are reference only and are not carried over.

## Data

| Module | Dataset |
|---|---|
| [DS02](../../data/DS02-grapepan-v1/) | Grapepan v1.0: T2T haplotypes, graphs and a 466-accession resequencing panel |
| [DS03](../../data/DS03-vitis-super-pangenome-72/) | Vitis super-pangenome: 72 haplotype-resolved accessions |
| [DS10](../../data/DS10-reseq-472-vitis/) | Resequencing of 472 Vitis accessions (and the 2017 domestication panel) |
| [DS12](../../data/DS12-reseq-204-magris2021/) | Resequencing of 204 V. vinifera accessions (Magris et al. 2021) |
| [DS01](../../data/DS01-pn40024-references/) | PN40024 references: PN_T2T (v5), PN40024.v4 and 12X |

## Analysis steps

Shared modules, in order:

1. [AM01 · Download and verify](../../analyses/AM01-download-and-verify/)
2. [AM07 · Pangenome graph build and genotyping](../../analyses/AM07-graph-build-and-genotype/)
3. [AM03 · Short-read mapping and small-variant calling](../../analyses/AM03-short-read-variants/)

Project-specific steps:

- Extract the locus from each haplotype; build a PGGB graph (AM07).
- Genotype panel samples with vg giraffe and vg call.
- Compare with VIVC colour records.

## Paper design and split

| Paper | Working title | Type | Figures |
|---|---|---|---|
| J1 | Graph genotyping of the grape colour locus | short methods note | Fig 1–3 |

Each paper: introduction from the gap above; one results section per figure; methods with tool versions from the modules; data availability listing every accession used and the derived tables.

## Risks and novelty check

- Risk: Colour records may be inconsistent.
- Risk: Colour sports are periclinal chimeras: a change in one cell layer appears in leaf DNA as a lower VAF rather than an absence; which layer determines berry colour is checked against the colour-sport literature [待确认].
- Novelty: checked against the existing work above (Crossref-verified DOIs). Repeat the search before writing; anything marked [待确认] is not yet verified.

## Rough estimates

- Compute: small [draft]
- Effort: 3–6 weeks for one person [draft]
- Target: plant genetics journal [draft]

## Continue on HPC

Run each step as its own job, in this order. Every job writes `.DONE` or `.FAILED` and a log; the next step starts only after `.DONE`. Template and rules: [`docs/HPC_JOBS.md`](../../../../templates/HPC_JOBS.md).

| Order | Step | Main tools | Resources (rough) |
|---|---|---|---|
| 1 | [AM01](../../analyses/AM01-download-and-verify/) Download and verify | ncbi-datasets-cli, sra-tools, ENA FTP / Aspera | 1–4 CPU, 4 GB, network; array over files |
| 2 | [AM07](../../analyses/AM07-graph-build-and-genotype/) Pangenome graph build and genotyping | Minigraph-Cactus, PGGB, vg | 32–64 CPU, 256–512 GB for graph builds; 16 CPU, 64 GB per sample for giraffe |
| 3 | [AM03](../../analyses/AM03-short-read-variants/) Short-read mapping and small-variant calling | bwa-mem2, samtools, DeepVariant | 16 CPU, 64 GB, 6–24 h per sample (DeepVariant); joint step 32 CPU, 128 GB |

Public inputs: [DS02](../../data/DS02-grapepan-v1/), [DS03](../../data/DS03-vitis-super-pangenome-72/), [DS10](../../data/DS10-reseq-472-vitis/), [DS12](../../data/DS12-reseq-204-magris2021/), [DS01](../../data/DS01-pn40024-references/).

## References

- Kobayashi et al. 2004. Retrotransposon-Induced Mutations in Grape Skin Color. *Science*. [doi:10.1126/science.1095011](https://doi.org/10.1126/science.1095011)
- Pelsy et al. 2015. Chromosome Replacement and Deletion Lead to Clonal Polymorphism of Berry Color in Grapevine. *PLOS Genetics*. [doi:10.1371/journal.pgen.1005081](https://doi.org/10.1371/journal.pgen.1005081)
- Carbonell-Bejerano et al. 2017. Catastrophic Unbalanced Genome Rearrangements Cause Somatic Loss of Berry Color in Grapevine. *Plant Physiology*. [doi:10.1104/pp.17.00715](https://doi.org/10.1104/pp.17.00715)
- Reynard et al. 2025. A divergent haplotype with a large deletion at the berry color locus causes a white-skinned phenotype in grapevine. *Horticulture Research*. [doi:10.1093/hr/uhaf069](https://doi.org/10.1093/hr/uhaf069)
