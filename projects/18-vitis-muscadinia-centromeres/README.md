# 18. Centromeres of Vitis and Muscadinia, and a check of the chr7 fusion point

中文：Vitis 与 Muscadinia 着丝粒比较及 chr7 融合点核查

Rank 18 of 22 (score F 2 + N 2 + E 2 = 6; see docs/RANKING.md) · Tier: Medium (E = 2, effort range ending after 6 weeks and by 4 months) · Origin: continued: started earlier and restarted here from public data under a new preregistration · Status: draft v0.3.2, 2026-11-14

## Gap

*Vitis* centromeres are described from T2T assemblies, and functional CENH3 data exist for one cultivar, Chardonnay, not for *V. vinifera* in general. A comparison of centromeres between *Vitis* and *Muscadinia* was not found. No gap-free *Muscadinia* assembly is in NCBI.

**Existing work**

- [Shi et al. 2023](https://doi.org/10.1093/hr/uhad061): centromeres in the PN_T2T reference.
- [Guo et al. 2025](https://doi.org/10.1038/s41588-025-02111-7): CENH3 ChIP-seq for one cultivar, Chardonnay.
- [Pei et al. 2024](https://doi.org/10.1007/s00425-024-04374-6): centromeric repeat evolution in V. vinifera.
- [Wang et al. 2026](https://doi.org/10.1038/s41477-026-02442-1): ancestral karyotypes of Vitaceae.
- [Cochetel et al. 2021](https://doi.org/10.1093/g3journal/jkab033): Muscadinia assembly supporting a chromosome fusion.
- [Huff et al. 2023](https://doi.org/10.1186/s12864-023-09514-y): Carlos muscadine assembly.

**How this project differs**

Compares satellite families across genera, calibrates with the Chardonnay CENH3 data, and checks the *Vitis* side of the chr7 fusion now.

## Question

Do *Vitis* and *Muscadinia* use different centromeric satellites beyond the variation within *Vitis*, does *Vitis* chr7 retain traces of a second centromere or of telomeres at its fusion point, and which ancestral centromere did it keep?

## Hypotheses, planned figures and criteria

No results are given here. Each row says what would count as support; the exact thresholds go into the preregistration.

| Figure or table | Hypothesis or purpose | Criterion |
|---|---|---|
| Fig 1. Satellite families by genus | Dominant centromeric satellites differ between genera. | Monomer clustering with families defined before the comparison; a between-genus difference counts only if it exceeds the variation among *Vitis* haplotypes; *Muscadinia* satellite abundance is also measured from raw-read k-mers, because gapped assemblies can miss arrays. |
| Fig 2. CENH3 calibration (Chardonnay only) | Most CENH3 signal lies on the dominant satellite. | Share of CENH3 reads on satellite arrays; other accessions are labelled predicted, not functional. |
| Fig 3. The fusion point on *Vitis* chr7, where the segments homologous to *Muscadinia* chr7 and chr20 meet (located on Cabernet Sauvignon and PN40024 chr7 by Cochetel et al. 2021) | Residual centromeric satellite or interstitial telomeric repeats are present [待确认]. | Two-sided: report presence or absence; no prior assumption of end-to-end or nested fusion. |
| Fig 4. Which ancestral centromere was kept | The *Vitis* chr7 centromere lies in the segment homologous to either *Muscadinia* chr7 or chr20 [待确认]. | Assigned by synteny; descriptive. |

## Preregistration

Before any data are analysed, fill in [`docs/PREREGISTRATION.md`](../../docs/PREREGISTRATION.md) for this project: hypotheses, primary outcome, sample inclusion rules, thresholds, stop rules and what will be reported if a hypothesis fails. Commit it with a date. Criteria from any earlier attempt are reference only and are not carried over.

## Data

| Module | Dataset |
|---|---|
| [DS01](../../data/DS01-pn40024-references/) | PN40024 references: PN_T2T (v5), PN40024.v4 and 12X |
| [DS02](../../data/DS02-grapepan-v1/) | Grapepan v1.0: T2T haplotypes, graphs and a 466-accession resequencing panel |
| [DS03](../../data/DS03-vitis-super-pangenome-72/) | Vitis super-pangenome: 72 haplotype-resolved accessions |
| [DS05](../../data/DS05-vitaceae-family-genomes/) | Vitaceae family chromosome-level genomes |
| [DS08](../../data/DS08-muscadinia-genomes/) | Muscadinia rotundifolia assemblies and reads |

## Analysis steps

Shared modules, in order:

1. [AM01 · Download and verify](../../analyses/AM01-download-and-verify/)
2. [AM05 · Assembly QC](../../analyses/AM05-assembly-qc/)
3. [AM06 · Whole-genome alignment, synteny and SVs from assemblies](../../analyses/AM06-wga-and-sv/)
4. [AM10 · Telomeres, centromeric satellites and rDNA arrays](../../analyses/AM10-repeat-arrays/)

Project-specific steps:

- Annotate satellites with TRASH or quarTeT (AM10); count satellite k-mers in raw *Muscadinia* reads (DS08).
- Map the Chardonnay CENH3 ChIP-seq runs (2 ChIP-Seq runs in PRJNA1021789).
- Align *Muscadinia* chr7 and chr20 to *Vitis* chr7 (AM06); scan the fusion point on *Vitis* chr7 for satellites and ITS (shared with project 01); assign the *Vitis* chr7 centromere to the chr7- or chr20-homologous segment.

## Paper design and split

| Paper | Working title | Type | Figures |
|---|---|---|---|
| R1 | Centromeres of Vitis and Muscadinia | paper | Fig 1–2 |
| R2 | The Vitis side of the chr7 fusion | short note | Fig 3–4 |

Each paper: introduction from the gap above; one results section per figure; methods with tool versions from the modules; data availability listing every accession used and the derived tables.

## Risks and novelty check

- Risk: *Muscadinia* centromeres may be incomplete in gapped assemblies.
- Risk: CENH3 data come from one cultivar only.
- Risk: TRASH may not install; quarTeT is the fallback.
- Novelty: checked against the existing work above (Crossref-verified DOIs). Repeat the search before writing; anything marked [待确认] is not yet verified.

## Rough estimates

- Compute: small to medium [draft]
- Effort: 2–3 months for one person [draft]
- Target: chromosome biology or genome journal [draft]

## Continue on HPC

Run each step as its own job, in this order. Every job writes `.DONE` or `.FAILED` and a log; the next step starts only after `.DONE`. Template and rules: [`docs/HPC_JOBS.md`](../../docs/HPC_JOBS.md).

| Order | Step | Main tools | Resources (rough) |
|---|---|---|---|
| 1 | [AM01](../../analyses/AM01-download-and-verify/) Download and verify | ncbi-datasets-cli, sra-tools, ENA FTP / Aspera | 1–4 CPU, 4 GB, network; array over files |
| 2 | [AM05](../../analyses/AM05-assembly-qc/) Assembly QC | compleasm, BUSCO, Merqury | 16 CPU, 64 GB, 1–3 h per assembly; array |
| 3 | [AM06](../../analyses/AM06-wga-and-sv/) Whole-genome alignment, synteny and SVs from assemblies | minimap2, SyRI, AnchorWave | 16 CPU, 64 GB, 1–4 h per haplotype; array |
| 4 | [AM10](../../analyses/AM10-repeat-arrays/) Telomeres, centromeric satellites and rDNA arrays | tidk, TRF, TRASH | 8 CPU, 16 GB per assembly |

Public inputs: [DS01](../../data/DS01-pn40024-references/), [DS02](../../data/DS02-grapepan-v1/), [DS03](../../data/DS03-vitis-super-pangenome-72/), [DS05](../../data/DS05-vitaceae-family-genomes/), [DS08](../../data/DS08-muscadinia-genomes/).

## References

- Shi et al. 2023. The complete reference genome for grapevine ( Vitis vinifera L.) genetics and breeding. *Horticulture Research*. [doi:10.1093/hr/uhad061](https://doi.org/10.1093/hr/uhad061)
- Guo et al. 2025. Super pangenome of Vitis empowers identification of downy mildew resistance genes for grapevine improvement. *Nature Genetics*. [doi:10.1038/s41588-025-02111-7](https://doi.org/10.1038/s41588-025-02111-7)
- Pei et al. 2024. The evolution and formation of centromeric repeats analysis in Vitis vinifera. *Planta*. [doi:10.1007/s00425-024-04374-6](https://doi.org/10.1007/s00425-024-04374-6)
- Wang et al. 2026. Chromosome-level phylogenomics and genome evolution of the grape family. *Nature Plants*. [doi:10.1038/s41477-026-02442-1](https://doi.org/10.1038/s41477-026-02442-1)
- Cochetel et al. 2021. Diploid chromosome-scale assembly of the Muscadinia rotundifolia genome supports chromosome fusion and disease resistance gene expansion during Vitis and Muscadinia divergence. *G3 Genes|Genomes|Genetics*. [doi:10.1093/g3journal/jkab033](https://doi.org/10.1093/g3journal/jkab033)
- Huff et al. 2023. Long-read, chromosome-scale assembly of Vitis rotundifolia cv. Carlos and its unique resistance to Xylella fastidiosa subsp. fastidiosa. *BMC Genomics*. [doi:10.1186/s12864-023-09514-y](https://doi.org/10.1186/s12864-023-09514-y)
