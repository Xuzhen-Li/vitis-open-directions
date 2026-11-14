# 12. Convergent domestication: grape compared with other crops in one pipeline

中文：葡萄与其他作物统一流程的趋同驯化比较

Rank 12 of 22 (score F 2 + N 3 + E 1 = 6; see docs/RANKING.md) · Tier: Large (E = 1, more than 4 months or a high-risk step) · Origin: new · Status: draft v0.3.2, 2026-11-14

## Gap

Domestication scans exist for many crops, but grape has not been compared with other fruit or field crops using one pipeline and a gene-matched null [待确认].

**Existing work**

- [Chen et al. 2022](https://doi.org/10.1126/science.abg7985): convergent selection of one gene in maize and rice.
- [Yu et al. 2018](https://doi.org/10.1038/s41467-018-07744-3): peach domestication from resequencing.
- [Duan et al. 2017](https://doi.org/10.1038/s41467-017-00336-7): apple domestication from resequencing.
- [Jaillon et al. 2007](https://doi.org/10.1038/nature06148): grape genome and the ancestral triplication shared by core eudicots.

**How this project differs**

Same scan for every crop, orthology that handles one-to-many cases, and a null built from matched gene bins.

## Question

Do grape and other crops share selected genes or pathways more often than expected under a matched null?

## Hypotheses, planned figures and criteria

No results are given here. Each row says what would count as support; the exact thresholds go into the preregistration.

| Figure or table | Hypothesis or purpose | Criterion |
|---|---|---|
| Fig 1. Gene-level overlap vs null | Overlap exceeds the null. | Permutation within bins of gene length, family size and recombination proxy; one-sided test fixed in advance. |
| Fig 2. Pathway-level overlap | Overlap is stronger at pathway than at gene level. | Same null at pathway level. |
| Fig 3. Sensitivity to orthology | Results hold across orthology definitions. | Repeat with two orthology definitions. |

## Preregistration

Before any data are analysed, fill in [`docs/PREREGISTRATION.md`](../../docs/PREREGISTRATION.md) for this project: hypotheses, primary outcome, sample inclusion rules, thresholds, stop rules and what will be reported if a hypothesis fails. Commit it with a date. Criteria from any earlier attempt are reference only and are not carried over.

## Data

| Module | Dataset |
|---|---|
| [DS10](../../data/DS10-reseq-472-vitis/) | Resequencing of 472 Vitis accessions (and the 2017 domestication panel) |
| [DS12](../../data/DS12-reseq-204-magris2021/) | Resequencing of 204 V. vinifera accessions (Magris et al. 2021) |
| [DS21](../../data/DS21-other-crop-population-genomes/) | Population genomes of other domesticated plants (comparison set) |
| [DS01](../../data/DS01-pn40024-references/) | PN40024 references: PN_T2T (v5), PN40024.v4 and 12X |

## Analysis steps

Shared modules, in order:

1. [AM01 · Download and verify](../../analyses/AM01-download-and-verify/)
2. [AM03 · Short-read mapping and small-variant calling](../../analyses/AM03-short-read-variants/)
3. [AM11 · Diversity and selection scans](../../analyses/AM11-diversity-and-selection/)
4. [AM23 · Cross-crop orthology and convergence tests](../../analyses/AM23-cross-crop-convergence/)

Project-specific steps:

- Confirm accessions for each comparison crop (DS21).
- Run AM03 and AM11 the same way for each crop.
- Map to orthogroups (AM23); build the null; test overlap.

## Paper design and split

| Paper | Working title | Type | Figures |
|---|---|---|---|
| M1 | Convergent domestication signals in grape and other crops | main paper | Fig 1–3 |

Each paper: introduction from the gap above; one results section per figure; methods with tool versions from the modules; data availability listing every accession used and the derived tables.

## Risks and novelty check

- Risk: Lineage-specific duplications make orthology one-to-many.
- Risk: Different sample sizes change scan power; downsample to equal sizes.
- Risk: Novelty: no dedicated literature search on this topic has been done beyond the grape literature base yet [待确认: repeat the search before writing].
- Novelty: checked against the existing work above (Crossref-verified DOIs). Repeat the search before writing; anything marked [待确认] is not yet verified.

## Rough estimates

- Compute: large [draft]
- Effort: 4–6 months for one person [draft]
- Target: evolution journal [draft]

## Continue on HPC

Run each step as its own job, in this order. Every job writes `.DONE` or `.FAILED` and a log; the next step starts only after `.DONE`. Template and rules: [`docs/HPC_JOBS.md`](../../docs/HPC_JOBS.md).

| Order | Step | Main tools | Resources (rough) |
|---|---|---|---|
| 1 | [AM01](../../analyses/AM01-download-and-verify/) Download and verify | ncbi-datasets-cli, sra-tools, ENA FTP / Aspera | 1–4 CPU, 4 GB, network; array over files |
| 2 | [AM03](../../analyses/AM03-short-read-variants/) Short-read mapping and small-variant calling | bwa-mem2, samtools, DeepVariant | 16 CPU, 64 GB, 6–24 h per sample (DeepVariant); joint step 32 CPU, 128 GB |
| 3 | [AM11](../../analyses/AM11-diversity-and-selection/) Diversity and selection scans | pixy, vcftools, RAiSD | 8 CPU, 32 GB per chromosome |
| 4 | [AM23](../../analyses/AM23-cross-crop-convergence/) Cross-crop orthology and convergence tests | OrthoFinder, MAFFT, IQ-TREE | 32 CPU, 128 GB for OrthoFinder |

Public inputs: [DS10](../../data/DS10-reseq-472-vitis/), [DS12](../../data/DS12-reseq-204-magris2021/), [DS21](../../data/DS21-other-crop-population-genomes/), [DS01](../../data/DS01-pn40024-references/).

## References

- Chen et al. 2022. Convergent selection of a WD40 protein that enhances grain yield in maize and rice. *Science*. [doi:10.1126/science.abg7985](https://doi.org/10.1126/science.abg7985)
- Yu et al. 2018. Genome re-sequencing reveals the evolutionary history of peach fruit edibility. *Nature Communications*. [doi:10.1038/s41467-018-07744-3](https://doi.org/10.1038/s41467-018-07744-3)
- Duan et al. 2017. Genome re-sequencing reveals the history of apple and supports a two-stage model for fruit enlargement. *Nature Communications*. [doi:10.1038/s41467-017-00336-7](https://doi.org/10.1038/s41467-017-00336-7)
- The French–Italian Public Consortium for Grapevine Genome Characterization 2007. The grapevine genome sequence suggests ancestral hexaploidization in major angiosperm phyla. *Nature*. [doi:10.1038/nature06148](https://doi.org/10.1038/nature06148)
