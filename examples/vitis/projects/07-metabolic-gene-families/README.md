# 07. Copy number and birth–death of stilbene and aroma gene families (STS, TPS, CCD, LOX)

中文：芪合酶与香气基因家族（STS、TPS、CCD、LOX）的拷贝数与生灭

Rank 7 of 22 (score F 3 + N 2 + E 2 = 7; see docs/RANKING.md) · Tier: Medium (E = 2, effort range ending after 6 weeks and by 4 months) · Origin: continued: started earlier and restarted here from public data under a new preregistration · Status: draft v0.3.2, 2026-11-14

## Gap

STS and TPS were catalogued in single references and compared among a few cultivars. Copy-number variation and birth–death rates across many near-complete haplotypes, with array-collapse checks, were not found.

**Existing work**

- [Vannozzi et al. 2012](https://doi.org/10.1186/1471-2229-12-130): stilbene synthase family in the grape reference.
- [Martin et al. 2010](https://doi.org/10.1186/1471-2229-10-226): terpene synthase family in the grape reference.
- [Smit et al. 2020](https://doi.org/10.3389/fgene.2020.00421): within-species comparison of TPS genes.

**How this project differs**

Uses near-complete haplotypes, checks tandem arrays for collapse, and estimates family-level rates on the species tree.

## Question

How variable are STS, TPS, CCD and LOX copy numbers among grape haplotypes, and do tandem families turn over faster than single-copy controls?

## Hypotheses, planned figures and criteria

No results are given here. Each row says what would count as support; the exact thresholds go into the preregistration.

| Figure or table | Hypothesis or purpose | Criterion |
|---|---|---|
| Fig 1. Copy number per haplotype | Tandem families (STS, TPS) vary more than single-copy controls. | Coefficient of variation with bootstrap intervals, against BUSCO single-copy genes. |
| Fig 2. Birth–death rates on the species tree | Between species, birth–death rates for STS and TPS exceed the genome-wide rate. | CAFE 5 run on one haplotype per species with a genome-wide background model; likelihood-ratio tests corrected across families. Copy-number differences among haplotypes of the same species reflect polymorphism rather than species-tree rates and are analysed separately (Fig 3). |
| Fig 3. Within-species copy-number polymorphism, wild vs cultivated | Copy number differs between wild and cultivated groups. | Permutation within species with the accession as the unit. |

## Preregistration

Before any data are analysed, fill in [`docs/PREREGISTRATION.md`](../../../../templates/PREREGISTRATION.md) for this project: hypotheses, primary outcome, sample inclusion rules, thresholds, stop rules and what will be reported if a hypothesis fails. Commit it with a date. Criteria from any earlier attempt are reference only and are not carried over.

## Data

| Module | Dataset |
|---|---|
| [DS01](../../data/DS01-pn40024-references/) | PN40024 references: PN_T2T (v5), PN40024.v4 and 12X |
| [DS02](../../data/DS02-grapepan-v1/) | Grapepan v1.0: T2T haplotypes, graphs and a 466-accession resequencing panel |
| [DS03](../../data/DS03-vitis-super-pangenome-72/) | Vitis super-pangenome: 72 haplotype-resolved accessions |
| [DS07](../../data/DS07-cultivated-16-pangenome/) | Cultivated grapevine pangenome (16 cultivars, Plastivigne) |
| [DS08](../../data/DS08-muscadinia-genomes/) | Muscadinia rotundifolia assemblies and reads |
| [DS10](../../data/DS10-reseq-472-vitis/) | Resequencing of 472 Vitis accessions (and the 2017 domestication panel) |

## Analysis steps

Shared modules, in order:

1. [AM01 · Download and verify](../../analyses/AM01-download-and-verify/)
2. [AM05 · Assembly QC](../../analyses/AM05-assembly-qc/)
3. [AM08 · Gene-family search across haplotypes](../../analyses/AM08-gene-family-annotation/)
4. [AM09 · Gene presence/absence and copy number](../../analyses/AM09-gene-pav-and-cnv/)

Project-specific steps:

- Annotate the four families with AM08.
- Check arrays for collapse with read depth.
- Build gene trees; run CAFE 5 with the background model.

## Paper design and split

| Paper | Working title | Type | Figures |
|---|---|---|---|
| H1 | Stilbene synthase arrays across grape haplotypes | short paper | Fig 1–2 (STS) |
| H2 | Aroma gene families (TPS, CCD, LOX) across grape haplotypes | paper | Fig 1–3 (aroma) |

Each paper: introduction from the gap above; one results section per figure; methods with tool versions from the modules; data availability listing every accession used and the derived tables.

## Risks and novelty check

- Risk: Tandem arrays are prone to collapse.
- Risk: Naming differs between studies; keep a mapping table.
- Novelty: checked against the existing work above (Crossref-verified DOIs). Repeat the search before writing; anything marked [待确认] is not yet verified.

## Rough estimates

- Compute: medium [draft]
- Effort: 2–3 months for one person [draft]
- Target: plant biology or genome journal [draft]

## Continue on HPC

Run each step as its own job, in this order. Every job writes `.DONE` or `.FAILED` and a log; the next step starts only after `.DONE`. Template and rules: [`docs/HPC_JOBS.md`](../../../../templates/HPC_JOBS.md).

| Order | Step | Main tools | Resources (rough) |
|---|---|---|---|
| 1 | [AM01](../../analyses/AM01-download-and-verify/) Download and verify | ncbi-datasets-cli, sra-tools, ENA FTP / Aspera | 1–4 CPU, 4 GB, network; array over files |
| 2 | [AM05](../../analyses/AM05-assembly-qc/) Assembly QC | compleasm, BUSCO, Merqury | 16 CPU, 64 GB, 1–3 h per assembly; array |
| 3 | [AM08](../../analyses/AM08-gene-family-annotation/) Gene-family search across haplotypes | miniprot, HMMER, InterProScan | 16 CPU, 32 GB, < 2 h per haplotype |
| 4 | [AM09](../../analyses/AM09-gene-pav-and-cnv/) Gene presence/absence and copy number | Liftoff, OrthoFinder, mosdepth | 8 CPU, 32 GB per haplotype |

Public inputs: [DS01](../../data/DS01-pn40024-references/), [DS02](../../data/DS02-grapepan-v1/), [DS03](../../data/DS03-vitis-super-pangenome-72/), [DS07](../../data/DS07-cultivated-16-pangenome/), [DS08](../../data/DS08-muscadinia-genomes/), [DS10](../../data/DS10-reseq-472-vitis/).

## References

- Vannozzi et al. 2012. Genome-wide analysis of the grapevine stilbene synthase multigenic family: genomic organization and expression profiles upon biotic and abiotic stresses. *BMC Plant Biology*. [doi:10.1186/1471-2229-12-130](https://doi.org/10.1186/1471-2229-12-130)
- Martin et al. 2010. Functional Annotation, Genome Organization and Phylogeny of the Grapevine (Vitis vinifera) Terpene Synthase Gene Family Based on Genome Assembly, FLcDNA Cloning, and Enzyme Assays. *BMC Plant Biology*. [doi:10.1186/1471-2229-10-226](https://doi.org/10.1186/1471-2229-10-226)
- Smit et al. 2020. Comparative (Within Species) Genomics of the Vitis vinifera L. Terpene Synthase Family to Explore the Impact of Genotypic Variation Using Phased Diploid Genomes. *Frontiers in Genetics*. [doi:10.3389/fgene.2020.00421](https://doi.org/10.3389/fgene.2020.00421)
