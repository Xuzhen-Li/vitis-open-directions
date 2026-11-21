# 22. Population-level evolution of the sex-determining region (demoted)

中文：性别决定区的群体层面演化（降级）

Rank 22 of 22 (score F 1 + N 1 + E 2 = 4; see docs/RANKING.md) · Tier: Medium (E = 2, effort range ending after 6 weeks and by 4 months) · Origin: new · Status: draft v0.3.2, 2026-11-14

## Gap

The sex-determining region has been assembled and compared across Vitaceae genera. Population-level haplotype diversity of the region was not found: M and F haplotypes in wild panels with recorded sex, and H haplotypes, which occur mainly in cultivated grapes. Functional validation of *Muscadinia* candidate genes needs experiments and is out of scope here.

**Existing work**

- [Massonnet et al. 2020](https://doi.org/10.1038/s41467-020-16700-z): genetic basis of sex determination in grapes.
- [Badouin et al. 2020](https://doi.org/10.1186/s13059-020-02131-y): wild grape genome and the transition from dioecy to hermaphroditism.
- [Iocco-Corena et al. 2021](https://doi.org/10.1038/s41467-021-27259-8): VviPLATZ1 controls female flower morphology.
- [Massonnet et al. 2025](https://doi.org/10.1038/s41467-025-61387-9): sex-determining regions assembled and phased in six Vitaceae species and Leea; cross-genus comparison done.

**How this project differs**

Restricted to population-level questions that public reads can answer: M and F from wild samples, H and F from cultivated samples, with sex types inferred from region genotypes and checked on samples with recorded sex.

## Question

What are the haplotype diversity and genealogical relationships of wild M and F haplotypes and cultivated H and F haplotypes of the sex-determining region?

## Hypotheses, planned figures and criteria

No results are given here. Each row says what would count as support; the exact thresholds go into the preregistration.

| Figure or table | Hypothesis or purpose | Criterion |
|---|---|---|
| Fig 1. Diversity of M, F and H haplotypes | M diversity relative to F departs from the neutral expectation. | With a 1:1 sex ratio, F has about three times as many copies as M, so F is expected to be more diverse under neutrality; the test is the deviation of the M/F diversity ratio from the expectation set by the copy-number (Ne) ratio and autosomal controls. M does not recombine, so linked selection (background selection and hitchhiking) is expected to lower its diversity further below one third of F; a low M/F ratio is therefore expected and is not interpreted as evidence for another mechanism. Sex types inferred from region genotypes and validated on the recorded subset; minimum samples per group fixed in advance. |
| Fig 2. Genealogy of H relative to M and F | Descriptive: where H haplotypes sit among wild M and F haplotypes [待确认: published H–M relationship]. | Haplotype networks and trees with bootstrap support. |
| Fig 3. Anther phasiRNA (optional, exploratory) | 24-nt phasiRNAs are linked to anther development, mainly in grasses [待确认: evidence in eudicots], so their abundance may differ between female (F/F) flowers, whose pollen is sterile, and male (M/F) or hermaphrodite flowers; no link to the region's genes is assumed. | Only if flower small-RNA libraries by sex type exist [待确认]; descriptive. |

## Preregistration

Before any data are analysed, fill in [`docs/PREREGISTRATION.md`](../../../../templates/PREREGISTRATION.md) for this project: hypotheses, primary outcome, sample inclusion rules, thresholds, stop rules and what will be reported if a hypothesis fails. Commit it with a date. Criteria from any earlier attempt are reference only and are not carried over.

## Data

| Module | Dataset |
|---|---|
| [DS09](../../data/DS09-sex-locus-haplotypes/) | Sex-determination region haplotypes and reads |
| [DS10](../../data/DS10-reseq-472-vitis/) | Resequencing of 472 Vitis accessions (and the 2017 domestication panel) |
| [DS20](../../data/DS20-small-rna-public/) | Public grape small-RNA data |
| [DS01](../../data/DS01-pn40024-references/) | PN40024 references: PN_T2T (v5), PN40024.v4 and 12X |

## Analysis steps

Shared modules, in order:

1. [AM01 · Download and verify](../../analyses/AM01-download-and-verify/)
2. [AM03 · Short-read mapping and small-variant calling](../../analyses/AM03-short-read-variants/)
3. [AM25 · Small-RNA and phasiRNA loci](../../analyses/AM25-small-rna-phasirna/)

Project-specific steps:

- Select wild samples (M, F) and cultivated samples (H, F); infer sex types from region genotypes and check against recorded sex.
- Genotype the region (AM03); build haplotype networks.
- Optional: phasiRNA from small RNA by flower sex type (AM25).

## Paper design and split

| Paper | Working title | Type | Figures |
|---|---|---|---|
| V1 | Population diversity and genealogy of grape sex-region haplotypes | short paper | Fig 1–3 |

Each paper: introduction from the gap above; one results section per figure; methods with tool versions from the modules; data availability listing every accession used and the derived tables.

## Risks and novelty check

- Risk: Sex records are sparse.
- Risk: The main question is already answered at the cross-genus level.
- Risk: Whether public wild samples with recorded sex and flower small-RNA libraries by sex type exist is not yet verified [待确认].
- Novelty: checked against the existing work above (Crossref-verified DOIs). Repeat the search before writing; anything marked [待确认] is not yet verified.

## Rough estimates

- Compute: small [draft]
- Effort: 1–2 months for one person [draft]
- Target: plant evolution journal [draft]

## Continue on HPC

Run each step as its own job, in this order. Every job writes `.DONE` or `.FAILED` and a log; the next step starts only after `.DONE`. Template and rules: [`docs/HPC_JOBS.md`](../../../../templates/HPC_JOBS.md).

| Order | Step | Main tools | Resources (rough) |
|---|---|---|---|
| 1 | [AM01](../../analyses/AM01-download-and-verify/) Download and verify | ncbi-datasets-cli, sra-tools, ENA FTP / Aspera | 1–4 CPU, 4 GB, network; array over files |
| 2 | [AM03](../../analyses/AM03-short-read-variants/) Short-read mapping and small-variant calling | bwa-mem2, samtools, DeepVariant | 16 CPU, 64 GB, 6–24 h per sample (DeepVariant); joint step 32 CPU, 128 GB |
| 3 | [AM25](../../analyses/AM25-small-rna-phasirna/) Small-RNA and phasiRNA loci | fastp, ShortStack, samtools | 8 CPU, 16 GB per library |

Public inputs: [DS09](../../data/DS09-sex-locus-haplotypes/), [DS10](../../data/DS10-reseq-472-vitis/), [DS20](../../data/DS20-small-rna-public/), [DS01](../../data/DS01-pn40024-references/).

## References

- Massonnet et al. 2020. The genetic basis of sex determination in grapes. *Nature Communications*. [doi:10.1038/s41467-020-16700-z](https://doi.org/10.1038/s41467-020-16700-z)
- Badouin et al. 2020. The wild grape genome sequence provides insights into the transition from dioecy to hermaphroditism during grape domestication. *Genome Biology*. [doi:10.1186/s13059-020-02131-y](https://doi.org/10.1186/s13059-020-02131-y)
- Iocco-Corena et al. 2021. VviPLATZ1 is a major factor that controls female flower morphology determination in grapevine. *Nature Communications*. [doi:10.1038/s41467-021-27259-8](https://doi.org/10.1038/s41467-021-27259-8)
- Massonnet et al. 2025. Evolutionary conservation of the grape sex-determining region in angiosperms and emergence of dioecy in Vitaceae. *Nature Communications*. [doi:10.1038/s41467-025-61387-9](https://doi.org/10.1038/s41467-025-61387-9)
