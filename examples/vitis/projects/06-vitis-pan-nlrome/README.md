# 06. A genus-wide NLR catalogue with integrated domains and collapse checks

中文：带塌缩核查和整合结构域的葡萄属泛 NLR 组

Rank 6 of 22 (score F 3 + N 2 + E 2 = 7; see docs/RANKING.md) · Tier: Medium (E = 2, effort range ending after 6 weeks and by 4 months) · Origin: continued: started earlier and restarted here from public data under a new preregistration · Status: draft v0.3.2, 2026-11-14

## Gap

NLR genes were catalogued for single references, selected loci, or within one pangenome. A catalogue across the whole genus, with integrated decoy domains and checks for collapsed arrays, was not found.

**Existing work**

- [Guo et al. 2025](https://doi.org/10.1038/s41588-025-02111-7): resistance genes from the Vitis super-pangenome.
- [Massonnet et al. 2022](https://doi.org/10.1093/g3journal/jkac148): haplotype-resolved powdery mildew resistance loci in Muscadinia.
- [Van de Weyer et al. 2019](https://doi.org/10.1016/j.cell.2019.07.038): pan-NLRome method in Arabidopsis.

**How this project differs**

One annotation pipeline across lineages, read-depth checks for collapsed NLR clusters, and integrated-domain discovery.

## Question

How large is the grape NLR repertoire across lineages, which integrated domains occur, and does the repertoire saturate?

## Hypotheses, planned figures and criteria

No results are given here. Each row says what would count as support; the exact thresholds go into the preregistration.

| Figure or table | Hypothesis or purpose | Criterion |
|---|---|---|
| Fig 1. NLR count per haplotype before and after collapse checks | Raw counts underestimate clustered NLRs. | Read-depth ratio over clusters; a cluster is flagged when depth exceeds the preregistered multiple of the genome median. |
| Fig 2. Integrated domains by lineage | Some integrated domains are lineage-specific. | A domain is counted only if found in at least two haplotypes of the lineage; the number of haplotypes per lineage is reported because small lineages have a lower chance of passing. |
| Fig 3. Saturation curves by lineage | At equal numbers of haplotypes, the cultivated repertoire is closer to saturation than wild lineages. | Orthogroup accumulation compared at the same number of haplotypes per lineage (rarefied), with bootstrap resampling by accession. |

## Preregistration

Before any data are analysed, fill in [`docs/PREREGISTRATION.md`](../../../../templates/PREREGISTRATION.md) for this project: hypotheses, primary outcome, sample inclusion rules, thresholds, stop rules and what will be reported if a hypothesis fails. Commit it with a date. Criteria from any earlier attempt are reference only and are not carried over.

## Data

| Module | Dataset |
|---|---|
| [DS01](../../data/DS01-pn40024-references/) | PN40024 references: PN_T2T (v5), PN40024.v4 and 12X |
| [DS02](../../data/DS02-grapepan-v1/) | Grapepan v1.0: T2T haplotypes, graphs and a 466-accession resequencing panel |
| [DS03](../../data/DS03-vitis-super-pangenome-72/) | Vitis super-pangenome: 72 haplotype-resolved accessions |
| [DS04](../../data/DS04-na-vitis-super-pangenome/) | North American Vitis super-pangenome and wild resequencing |
| [DS06](../../data/DS06-vitis-amurensis-pangenome/) | Vitis amurensis haplotype assemblies and 330-sample resequencing |
| [DS08](../../data/DS08-muscadinia-genomes/) | Muscadinia rotundifolia assemblies and reads |

## Analysis steps

Shared modules, in order:

1. [AM01 · Download and verify](../../analyses/AM01-download-and-verify/)
2. [AM05 · Assembly QC](../../analyses/AM05-assembly-qc/)
3. [AM08 · Gene-family search across haplotypes](../../analyses/AM08-gene-family-annotation/)
4. [AM09 · Gene presence/absence and copy number](../../analyses/AM09-gene-pav-and-cnv/)
5. [AM18 · Long-read SV calling](../../analyses/AM18-long-read-sv/)

Project-specific steps:

- Annotate NLRs with miniprot, HMMER and InterProScan (AM08).
- Check clusters with long-read depth (AM18) where reads exist.
- Cluster into orthogroups; list integrated domains; build saturation curves.

## Paper design and split

| Paper | Working title | Type | Figures |
|---|---|---|---|
| G1 | A genus-wide grape NLR catalogue | main paper | Fig 1–3 |

Each paper: introduction from the gap above; one results section per figure; methods with tool versions from the modules; data availability listing every accession used and the derived tables.

## Risks and novelty check

- Risk: Collapsed clusters remain where long reads are not public.
- Risk: Integrated-domain calls depend on domain database versions.
- Novelty: checked against the existing work above (Crossref-verified DOIs). Repeat the search before writing; anything marked [待确认] is not yet verified.

## Rough estimates

- Compute: medium [draft]
- Effort: 2–3 months for one person [draft]
- Target: plant pathology or genome journal [draft]

## Continue on HPC

Run each step as its own job, in this order. Every job writes `.DONE` or `.FAILED` and a log; the next step starts only after `.DONE`. Template and rules: [`docs/HPC_JOBS.md`](../../../../templates/HPC_JOBS.md).

| Order | Step | Main tools | Resources (rough) |
|---|---|---|---|
| 1 | [AM01](../../analyses/AM01-download-and-verify/) Download and verify | ncbi-datasets-cli, sra-tools, ENA FTP / Aspera | 1–4 CPU, 4 GB, network; array over files |
| 2 | [AM05](../../analyses/AM05-assembly-qc/) Assembly QC | compleasm, BUSCO, Merqury | 16 CPU, 64 GB, 1–3 h per assembly; array |
| 3 | [AM08](../../analyses/AM08-gene-family-annotation/) Gene-family search across haplotypes | miniprot, HMMER, InterProScan | 16 CPU, 32 GB, < 2 h per haplotype |
| 4 | [AM09](../../analyses/AM09-gene-pav-and-cnv/) Gene presence/absence and copy number | Liftoff, OrthoFinder, mosdepth | 8 CPU, 32 GB per haplotype |
| 5 | [AM18](../../analyses/AM18-long-read-sv/) Long-read SV calling | Sniffles2, cuteSV, pbsv | 16 CPU, 64 GB per sample |

Public inputs: [DS01](../../data/DS01-pn40024-references/), [DS02](../../data/DS02-grapepan-v1/), [DS03](../../data/DS03-vitis-super-pangenome-72/), [DS04](../../data/DS04-na-vitis-super-pangenome/), [DS06](../../data/DS06-vitis-amurensis-pangenome/), [DS08](../../data/DS08-muscadinia-genomes/).

## References

- Guo et al. 2025. Super pangenome of Vitis empowers identification of downy mildew resistance genes for grapevine improvement. *Nature Genetics*. [doi:10.1038/s41588-025-02111-7](https://doi.org/10.1038/s41588-025-02111-7)
- Massonnet et al. 2022. Haplotype-resolved powdery mildew resistance loci reveal the impact of heterozygous structural variation on NLR genes in Muscadinia rotundifolia. *G3 Genes|Genomes|Genetics*. [doi:10.1093/g3journal/jkac148](https://doi.org/10.1093/g3journal/jkac148)
- Van de Weyer et al. 2019. A Species-Wide Inventory of NLR Genes and Alleles in Arabidopsis thaliana. *Cell*. [doi:10.1016/j.cell.2019.07.038](https://doi.org/10.1016/j.cell.2019.07.038)
