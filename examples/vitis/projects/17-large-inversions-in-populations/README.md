# 17. Large inversions: discovery in assemblies, population genotyping and suppressed recombination

中文：大倒位：组装发现、群体分型与重组抑制

Rank 17 of 22 (score F 2 + N 2 + E 2 = 6; see docs/RANKING.md) · Tier: Medium (E = 2, effort range ending after 6 weeks and by 4 months) · Origin: continued: started earlier and restarted here from public data under a new preregistration · Status: draft v0.3.2, 2026-11-14

## Gap

Large inversions were reported in single assemblies or within SV catalogues. A population-scale inversion atlas, with breakpoint validation and tests of suppressed recombination, was not found.

**Existing work**

- [Zhou et al. 2019](https://doi.org/10.1038/s41477-019-0507-8): purifying selection on inversions; large inversions at the sex and colour loci.
- [Khan et al. 2026](https://doi.org/10.1038/s41597-026-06910-3): Cabernet Sauvignon T2T assemblies with a heterozygous inversion annotated.
- [Liu et al. 2024](https://doi.org/10.1038/s41588-024-01967-5): SVs among Grapepan haplotypes.

**How this project differs**

Discovers inversions across all near-complete haplotypes, validates breakpoints, and genotypes them in short-read panels.

## Question

How many large inversions segregate in grape, and do they show the haplotype structure expected from suppressed recombination?

## Hypotheses, planned figures and criteria

No results are given here. Each row says what would count as support; the exact thresholds go into the preregistration.

| Figure or table | Hypothesis or purpose | Criterion |
|---|---|---|
| Fig 1. Inversion catalogue | Not a hypothesis: catalogue with validated breakpoints. | Breakpoints confirmed by long reads where available. |
| Fig 2. Graph genotypes vs assembly genotypes | Graph genotyping recovers assembly genotypes. | Concordance on samples with both. |
| Fig 3. Differentiation between arrangements | Inversions suppress recombination in heterozygotes, so the two arrangements differ most near the breakpoints and the inversion genotype is in LD with SNPs inside. | After keeping one sample per clone group (project 08): F_ST between arrangements along the inversion and LD between inversion genotype and SNPs; permutation by within-chromosome window blocks. |

## Preregistration

Before any data are analysed, fill in [`docs/PREREGISTRATION.md`](../../../../templates/PREREGISTRATION.md) for this project: hypotheses, primary outcome, sample inclusion rules, thresholds, stop rules and what will be reported if a hypothesis fails. Commit it with a date. Criteria from any earlier attempt are reference only and are not carried over.

## Data

| Module | Dataset |
|---|---|
| [DS02](../../data/DS02-grapepan-v1/) | Grapepan v1.0: T2T haplotypes, graphs and a 466-accession resequencing panel |
| [DS03](../../data/DS03-vitis-super-pangenome-72/) | Vitis super-pangenome: 72 haplotype-resolved accessions |
| [DS07](../../data/DS07-cultivated-16-pangenome/) | Cultivated grapevine pangenome (16 cultivars, Plastivigne) |
| [DS10](../../data/DS10-reseq-472-vitis/) | Resequencing of 472 Vitis accessions (and the 2017 domestication panel) |
| [DS01](../../data/DS01-pn40024-references/) | PN40024 references: PN_T2T (v5), PN40024.v4 and 12X |

## Analysis steps

Shared modules, in order:

1. [AM01 · Download and verify](../../analyses/AM01-download-and-verify/)
2. [AM05 · Assembly QC](../../analyses/AM05-assembly-qc/)
3. [AM06 · Whole-genome alignment, synteny and SVs from assemblies](../../analyses/AM06-wga-and-sv/)
4. [AM07 · Pangenome graph build and genotyping](../../analyses/AM07-graph-build-and-genotype/)
5. [AM18 · Long-read SV calling](../../analyses/AM18-long-read-sv/)

Project-specific steps:

- Call inversions with SyRI on haplotype alignments (AM06).
- Validate breakpoints with long reads (AM18).
- Genotype through the graph (AM07); compute differentiation between arrangements and inversion–SNP LD.

## Paper design and split

| Paper | Working title | Type | Figures |
|---|---|---|---|
| Q1 | A population atlas of large inversions in grape | main paper | Fig 1–3 |

Each paper: introduction from the gap above; one results section per figure; methods with tool versions from the modules; data availability listing every accession used and the derived tables.

## Risks and novelty check

- Risk: Inversions flanked by repeats are hard to genotype from short reads.
- Risk: Uses the sample set from project 08.
- Novelty: checked against the existing work above (Crossref-verified DOIs). Repeat the search before writing; anything marked [待确认] is not yet verified.

## Rough estimates

- Compute: medium [draft]
- Effort: 2–4 months for one person [draft]
- Target: genome journal [draft]

## Continue on HPC

Run each step as its own job, in this order. Every job writes `.DONE` or `.FAILED` and a log; the next step starts only after `.DONE`. Template and rules: [`docs/HPC_JOBS.md`](../../../../templates/HPC_JOBS.md).

| Order | Step | Main tools | Resources (rough) |
|---|---|---|---|
| 1 | [AM01](../../analyses/AM01-download-and-verify/) Download and verify | ncbi-datasets-cli, sra-tools, ENA FTP / Aspera | 1–4 CPU, 4 GB, network; array over files |
| 2 | [AM05](../../analyses/AM05-assembly-qc/) Assembly QC | compleasm, BUSCO, Merqury | 16 CPU, 64 GB, 1–3 h per assembly; array |
| 3 | [AM06](../../analyses/AM06-wga-and-sv/) Whole-genome alignment, synteny and SVs from assemblies | minimap2, SyRI, AnchorWave | 16 CPU, 64 GB, 1–4 h per haplotype; array |
| 4 | [AM07](../../analyses/AM07-graph-build-and-genotype/) Pangenome graph build and genotyping | Minigraph-Cactus, PGGB, vg | 32–64 CPU, 256–512 GB for graph builds; 16 CPU, 64 GB per sample for giraffe |
| 5 | [AM18](../../analyses/AM18-long-read-sv/) Long-read SV calling | Sniffles2, cuteSV, pbsv | 16 CPU, 64 GB per sample |

Public inputs: [DS02](../../data/DS02-grapepan-v1/), [DS03](../../data/DS03-vitis-super-pangenome-72/), [DS07](../../data/DS07-cultivated-16-pangenome/), [DS10](../../data/DS10-reseq-472-vitis/), [DS01](../../data/DS01-pn40024-references/).

## References

- Zhou et al. 2019. The population genetics of structural variants in grapevine domestication. *Nature Plants*. [doi:10.1038/s41477-019-0507-8](https://doi.org/10.1038/s41477-019-0507-8)
- Khan et al. 2026. Haplotype-resolved T2T gap-free genomes of the winegrape cultivar Cabernet Sauvignon. *Scientific Data*. [doi:10.1038/s41597-026-06910-3](https://doi.org/10.1038/s41597-026-06910-3)
- Liu et al. 2024. Grapevine pangenome facilitates trait genetics and genomic breeding. *Nature Genetics*. [doi:10.1038/s41588-024-01967-5](https://doi.org/10.1038/s41588-024-01967-5)
