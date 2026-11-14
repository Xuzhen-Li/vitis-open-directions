# 05. Gene presence/absence across grape pangenomes under one pipeline

中文：统一流程下的葡萄基因有/无：哪些是真的

Rank 5 of 22 (score F 3 + N 2 + E 2 = 7; see docs/RANKING.md) · Tier: Medium (E = 2, effort range ending after 6 weeks and by 4 months) · Origin: continued: started earlier and restarted here from public data under a new preregistration · Status: draft v0.3.2, 2026-11-14

## Gap

Each grape pangenome reports gene PAV with its own annotation pipeline. Cultivated and wild resources have not been processed together, so it is unclear how much reported PAV reflects annotation differences.

**Existing work**

- [Liu et al. 2024](https://doi.org/10.1038/s41588-024-01967-5): Grapepan gene PAV.
- [Guo et al. 2025](https://doi.org/10.1038/s41588-025-02111-7): Vitis super-pangenome.
- [Pierre et al. 2026](https://doi.org/10.1093/g3journal/jkag168): 16-cultivar pangenome with a large dispensable share.
- [Long et al. 2024](https://doi.org/10.1093/plphys/kiae039): gene gain and loss in grape domestication.
- [Zhou et al. 2019](https://doi.org/10.1038/s41477-019-0507-8): hemizygous genes in Chardonnay.

**How this project differs**

Re-annotates all haplotypes with one projection pipeline, checks absences by sequence and by read depth, and reports which PAV calls survive.

## Question

How much reported gene PAV in grape is reproduced when all haplotypes are processed the same way, and which gene classes are truly variable?

## Hypotheses, planned figures and criteria

No results are given here. Each row says what would count as support; the exact thresholds go into the preregistration.

| Figure or table | Hypothesis or purpose | Criterion |
|---|---|---|
| Fig 1. Concordance of PAV calls between original and uniform annotation | A measurable share of reported absences are annotation artefacts. | Each absence re-tested by sequence search and read depth; categories fixed in advance. |
| Fig 2. Confirmed absences by gene class | Confirmed absences are enriched in NLR, TPS and other clustered families. | Enrichment against length- and GC-matched background; BH FDR applied within the family of gene classes fixed in advance. |
| Fig 3. Pangenome growth curves before and after correction | Corrected curves saturate earlier. | Curves with bootstrap intervals; the resampling unit is the accession (both haplotypes of an accession together). |

## Preregistration

Before any data are analysed, fill in [`docs/PREREGISTRATION.md`](../../docs/PREREGISTRATION.md) for this project: hypotheses, primary outcome, sample inclusion rules, thresholds, stop rules and what will be reported if a hypothesis fails. Commit it with a date. Criteria from any earlier attempt are reference only and are not carried over.

## Data

| Module | Dataset |
|---|---|
| [DS01](../../data/DS01-pn40024-references/) | PN40024 references: PN_T2T (v5), PN40024.v4 and 12X |
| [DS02](../../data/DS02-grapepan-v1/) | Grapepan v1.0: T2T haplotypes, graphs and a 466-accession resequencing panel |
| [DS03](../../data/DS03-vitis-super-pangenome-72/) | Vitis super-pangenome: 72 haplotype-resolved accessions |
| [DS04](../../data/DS04-na-vitis-super-pangenome/) | North American Vitis super-pangenome and wild resequencing |
| [DS06](../../data/DS06-vitis-amurensis-pangenome/) | Vitis amurensis haplotype assemblies and 330-sample resequencing |
| [DS07](../../data/DS07-cultivated-16-pangenome/) | Cultivated grapevine pangenome (16 cultivars, Plastivigne) |

## Analysis steps

Shared modules, in order:

1. [AM01 · Download and verify](../../analyses/AM01-download-and-verify/)
2. [AM05 · Assembly QC](../../analyses/AM05-assembly-qc/)
3. [AM09 · Gene presence/absence and copy number](../../analyses/AM09-gene-pav-and-cnv/)
4. [AM08 · Gene-family search across haplotypes](../../analyses/AM08-gene-family-annotation/)

Project-specific steps:

- Collect haplotypes and annotations from DS02/DS03/DS04/DS06/DS07.
- Run AM05 QC.
- Project PN_T2T genes with Liftoff and miniprot (AM09); call PAV.
- Check each absence by sequence search and by short-read depth where reads exist.

## Paper design and split

| Paper | Working title | Type | Figures |
|---|---|---|---|
| F1 | How much gene PAV in grape is real | methods/resource paper | Fig 1–3 |
| F2 | Joint paper with project 06 (NLR), as two sections | optional merger |  |

Each paper: introduction from the gap above; one results section per figure; methods with tool versions from the modules; data availability listing every accession used and the derived tables.

## Risks and novelty check

- Risk: Collapsed or duplicated regions in assemblies mimic PAV.
- Risk: Wild haplotypes are more diverged, so projection under-calls presence.
- Novelty: checked against the existing work above (Crossref-verified DOIs). Repeat the search before writing; anything marked [待确认] is not yet verified.

## Rough estimates

- Compute: medium [draft]
- Effort: 2–3 months for one person [draft]
- Target: genome journal [draft]

## Continue on HPC

Run each step as its own job, in this order. Every job writes `.DONE` or `.FAILED` and a log; the next step starts only after `.DONE`. Template and rules: [`docs/HPC_JOBS.md`](../../docs/HPC_JOBS.md).

| Order | Step | Main tools | Resources (rough) |
|---|---|---|---|
| 1 | [AM01](../../analyses/AM01-download-and-verify/) Download and verify | ncbi-datasets-cli, sra-tools, ENA FTP / Aspera | 1–4 CPU, 4 GB, network; array over files |
| 2 | [AM05](../../analyses/AM05-assembly-qc/) Assembly QC | compleasm, BUSCO, Merqury | 16 CPU, 64 GB, 1–3 h per assembly; array |
| 3 | [AM09](../../analyses/AM09-gene-pav-and-cnv/) Gene presence/absence and copy number | Liftoff, OrthoFinder, mosdepth | 8 CPU, 32 GB per haplotype |
| 4 | [AM08](../../analyses/AM08-gene-family-annotation/) Gene-family search across haplotypes | miniprot, HMMER, InterProScan | 16 CPU, 32 GB, < 2 h per haplotype |

Public inputs: [DS01](../../data/DS01-pn40024-references/), [DS02](../../data/DS02-grapepan-v1/), [DS03](../../data/DS03-vitis-super-pangenome-72/), [DS04](../../data/DS04-na-vitis-super-pangenome/), [DS06](../../data/DS06-vitis-amurensis-pangenome/), [DS07](../../data/DS07-cultivated-16-pangenome/).

## References

- Liu et al. 2024. Grapevine pangenome facilitates trait genetics and genomic breeding. *Nature Genetics*. [doi:10.1038/s41588-024-01967-5](https://doi.org/10.1038/s41588-024-01967-5)
- Guo et al. 2025. Super pangenome of Vitis empowers identification of downy mildew resistance genes for grapevine improvement. *Nature Genetics*. [doi:10.1038/s41588-025-02111-7](https://doi.org/10.1038/s41588-025-02111-7)
- Pierre et al. 2026. Pangenomic analyses in the cultivated grapevine confirm high genomic collinearity and extensive dispensable gene content likely involved in adaptation. *G3: Genes, Genomes, Genetics*. [doi:10.1093/g3journal/jkag168](https://doi.org/10.1093/g3journal/jkag168)
- Long et al. 2024. Population comparative genomics discovers gene gain and loss during grapevine domestication. *Plant Physiology*. [doi:10.1093/plphys/kiae039](https://doi.org/10.1093/plphys/kiae039)
- Zhou et al. 2019. The population genetics of structural variants in grapevine domestication. *Nature Plants*. [doi:10.1038/s41477-019-0507-8](https://doi.org/10.1038/s41477-019-0507-8)
