# 02. 45S and 5S rDNA arrays in near-complete grape assemblies

中文：近完整葡萄组装中的 45S/5S rDNA 阵列

Rank 2 of 22 (score F 3 + N 2 + E 3 = 8; see docs/RANKING.md) · Tier: Quick (E = 3, effort range ending at 6 weeks or less) · Origin: continued: started earlier and restarted here from public data under a new preregistration · Status: draft v0.3.2, 2026-11-14

## Gap

The number, position and assembled length of 45S and 5S rDNA arrays across near-complete grape and Vitaceae haplotypes have not been compiled [待确认].

**Existing work**

- [Shi et al. 2023](https://doi.org/10.1093/hr/uhad061): PN_T2T, the first gap-free grape reference.
- [Liu et al. 2024](https://doi.org/10.1038/s41588-024-01967-5): T2T haplotypes of nine grapes.

**How this project differs**

Catalogues every public near-complete haplotype, flags arrays that are closed or truncated, and compares positions across the family.

## Question

Where are the 45S and 5S rDNA arrays in grape haplotypes, how often are they fully assembled, and are their positions conserved across Vitaceae?

## Hypotheses, planned figures and criteria

No results are given here. Each row says what would count as support; the exact thresholds go into the preregistration.

| Figure or table | Hypothesis or purpose | Criterion |
|---|---|---|
| Fig 1. Array positions across haplotypes | Array positions are conserved within *Vitis*. | Positions compared after mapping to PN_T2T; conservation is called when a locus is present in all complete haplotypes of a species; the number of complete haplotypes (denominator) is reported per species. |
| Fig 2. Assembled array length vs assembly technology | Array length is limited by assembly technology. | Assembled length is a lower bound, so length is modelled with censored regression (Tobit) on technology and read length; arrays closed by unique flanks on both sides are reported separately. |
| Fig 3. Family-wide comparison | Positions differ between *Vitis* and other Vitaceae genera. | Descriptive; positions placed on the ancestral karyotype of the Vitaceae study. |

## Preregistration

Before any data are analysed, fill in [`docs/PREREGISTRATION.md`](../../../../templates/PREREGISTRATION.md) for this project: hypotheses, primary outcome, sample inclusion rules, thresholds, stop rules and what will be reported if a hypothesis fails. Commit it with a date. Criteria from any earlier attempt are reference only and are not carried over.

## Data

| Module | Dataset |
|---|---|
| [DS01](../../data/DS01-pn40024-references/) | PN40024 references: PN_T2T (v5), PN40024.v4 and 12X |
| [DS02](../../data/DS02-grapepan-v1/) | Grapepan v1.0: T2T haplotypes, graphs and a 466-accession resequencing panel |
| [DS03](../../data/DS03-vitis-super-pangenome-72/) | Vitis super-pangenome: 72 haplotype-resolved accessions |
| [DS05](../../data/DS05-vitaceae-family-genomes/) | Vitaceae family chromosome-level genomes |
| [DS08](../../data/DS08-muscadinia-genomes/) | Muscadinia rotundifolia assemblies and reads |
| [DS16](../../data/DS16-vitaceae-assembly-index/) | Index of all Vitaceae assemblies in NCBI |
| [DS17](../../data/DS17-angiosperm-near-complete-assemblies/) | Near-complete angiosperm assemblies (comparison set) |

## Analysis steps

Shared modules, in order:

1. [AM01 · Download and verify](../../analyses/AM01-download-and-verify/)
2. [AM05 · Assembly QC](../../analyses/AM05-assembly-qc/)
3. [AM10 · Telomeres, centromeric satellites and rDNA arrays](../../analyses/AM10-repeat-arrays/)

Project-specific steps:

- Same assembly list as project 01.
- Search 45S and 5S seeds with BLASTN or nhmmer (AM10).
- Classify each array as closed (unique flank on both sides) or open.
- Map positions to PN_T2T and to the ancestral karyotype.

## Paper design and split

| Paper | Working title | Type | Figures |
|---|---|---|---|
| B1 | rDNA arrays in near-complete grape assemblies | short paper or data note | Fig 1–3 |

Each paper: introduction from the gap above; one results section per figure; methods with tool versions from the modules; data availability listing every accession used and the derived tables.

## Risks and novelty check

- Risk: rDNA arrays are the hardest region to assemble; most may be open.
- Risk: Copy number cannot be read from assemblies; read-depth estimates need raw reads.
- Risk: Novelty: no dedicated literature search on this topic has been done beyond the grape literature base yet [待确认: repeat the search before writing].
- Novelty: checked against the existing work above (Crossref-verified DOIs). Repeat the search before writing; anything marked [待确认] is not yet verified.

## Rough estimates

- Compute: small [draft]
- Effort: 3–6 weeks for one person [draft]
- Target: cytogenetics or genome journal [draft]

## Continue on HPC

Run each step as its own job, in this order. Every job writes `.DONE` or `.FAILED` and a log; the next step starts only after `.DONE`. Template and rules: [`docs/HPC_JOBS.md`](../../../../templates/HPC_JOBS.md).

| Order | Step | Main tools | Resources (rough) |
|---|---|---|---|
| 1 | [AM01](../../analyses/AM01-download-and-verify/) Download and verify | ncbi-datasets-cli, sra-tools, ENA FTP / Aspera | 1–4 CPU, 4 GB, network; array over files |
| 2 | [AM05](../../analyses/AM05-assembly-qc/) Assembly QC | compleasm, BUSCO, Merqury | 16 CPU, 64 GB, 1–3 h per assembly; array |
| 3 | [AM10](../../analyses/AM10-repeat-arrays/) Telomeres, centromeric satellites and rDNA arrays | tidk, TRF, TRASH | 8 CPU, 16 GB per assembly |

Public inputs: [DS01](../../data/DS01-pn40024-references/), [DS02](../../data/DS02-grapepan-v1/), [DS03](../../data/DS03-vitis-super-pangenome-72/), [DS05](../../data/DS05-vitaceae-family-genomes/), [DS08](../../data/DS08-muscadinia-genomes/), [DS16](../../data/DS16-vitaceae-assembly-index/), [DS17](../../data/DS17-angiosperm-near-complete-assemblies/).

## References

- Shi et al. 2023. The complete reference genome for grapevine ( Vitis vinifera L.) genetics and breeding. *Horticulture Research*. [doi:10.1093/hr/uhad061](https://doi.org/10.1093/hr/uhad061)
- Liu et al. 2024. Grapevine pangenome facilitates trait genetics and genomic breeding. *Nature Genetics*. [doi:10.1038/s41588-024-01967-5](https://doi.org/10.1038/s41588-024-01967-5)
