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

**Background survey (literature read for this plan)**

Wild grapes are dioecious and cultivated grapes mostly hermaphrodite. Polymorphisms in a small XY region on chromosome 2 explained sex in wild and cultivated *V. vinifera* ([Picq et al. 2014](https://doi.org/10.1186/s12870-014-0229-z)), and candidate genes were listed in a 143 kb interval ([Fechter et al. 2012](https://doi.org/10.1007/s00438-012-0674-z)). Assembled haplotypes defined the sex-determining region and its genes ([Massonnet et al. 2020](https://doi.org/10.1038/s41467-020-16700-z); [Badouin et al. 2020](https://doi.org/10.1186/s13059-020-02131-y)), VviPLATZ1 was shown to control female flower morphology ([Iocco-Corena et al. 2021](https://doi.org/10.1038/s41467-021-27259-8)), and the region was traced to a locus conserved across angiosperms, with haplotypes phased in six Vitaceae species and *Leea* ([Massonnet et al. 2025](https://doi.org/10.1038/s41467-025-61387-9)).

At population level, 556 wild and domesticated accessions showed high LD at the region in wild species and two hermaphrodite haplotypes, H1 and H2, in cultivars, with H1 and H2 estimated to have diverged about 6 million years ago, before domestication ([Zou et al. 2021](https://doi.org/10.1073/pnas.2023548118)). This is the published H relationship that the open item in Fig 2 refers to. Plant sex chromosome theory predicts suppressed recombination and specific diversity patterns on the male-specific haplotype ([Charlesworth 2016](https://doi.org/10.1146/annurev-arplant-043015-111911)). For the optional Fig 3, 24-nt reproductive phasiRNAs triggered by miR2275 were found to be widely present in eudicots, not only grasses ([Xia et al. 2019](https://doi.org/10.1038/s41467-019-08543-0)), and their timing in anthers was described in maize ([Zhai et al. 2015](https://doi.org/10.1073/pnas.1418918112)).

**Specific gap.** Diversity of M and F haplotypes in wild panels with recorded sex, compared with the copy-number expectation, was not found [待确认].

## Question

What are the haplotype diversity and genealogical relationships of wild M and F haplotypes and cultivated H and F haplotypes of the sex-determining region?

## Hypotheses, planned figures and criteria

No results are given here. Each row says what would count as support; the exact thresholds go into the preregistration.

| Figure or table | Hypothesis or purpose | Criterion |
|---|---|---|
| Fig 1. Diversity of M, F and H haplotypes | M diversity relative to F departs from the neutral expectation. | With a 1:1 sex ratio, F has about three times as many copies as M, so F is expected to be more diverse under neutrality; the test is the deviation of the M/F diversity ratio from the expectation set by the copy-number (Ne) ratio and autosomal controls. M does not recombine, so linked selection (background selection and hitchhiking) is expected to lower its diversity further below one third of F; a low M/F ratio is therefore expected and is not interpreted as evidence for another mechanism. Sex types inferred from region genotypes and validated on the recorded subset; minimum samples per group fixed in advance. |
| Fig 2. Genealogy of H relative to M and F | Descriptive: where H haplotypes sit among wild M and F haplotypes [待确认: published H–M relationship]. | Haplotype networks and trees with bootstrap support. |
| Fig 3. Anther phasiRNA (optional, exploratory) | 24-nt phasiRNAs are linked to anther development, mainly in grasses [待确认: evidence in eudicots], so their abundance may differ between female (F/F) flowers, whose pollen is sterile, and male (M/F) or hermaphrodite flowers; no link to the region's genes is assumed. | Only if flower small-RNA libraries by sex type exist [待确认]; descriptive. |

**Expected results and how they will be read**

- Fig 1: an M/F diversity ratio below the copy-number expectation and autosomal controls would suggest linked selection on the non-recombining M haplotype; a ratio near the expectation is consistent with neutrality.
- Fig 2 places H haplotypes relative to wild M and F; agreement with the published H1/H2 split is the positive control.
- Fig 3 runs only if small-RNA libraries by sex type exist; it is descriptive.

## Preregistration

Before any data are analysed, fill in [`docs/PREREGISTRATION.md`](../../../../templates/PREREGISTRATION.md) for this project: hypotheses, primary outcome, sample inclusion rules, thresholds, stop rules and what will be reported if a hypothesis fails. Commit it with a date. Criteria from any earlier attempt are reference only and are not carried over.

## Data

| Module | Dataset |
|---|---|
| [DS09](../../data/DS09-sex-locus-haplotypes/) | Sex-determination region haplotypes and reads |
| [DS10](../../data/DS10-reseq-472-vitis/) | Resequencing of 472 Vitis accessions (and the 2017 domestication panel) |
| [DS20](../../data/DS20-small-rna-public/) | Public grape small-RNA data |
| [DS01](../../data/DS01-pn40024-references/) | PN40024 references: PN_T2T (v5), PN40024.v4 and 12X |

**How each dataset is used**

| Module | Role in this project |
|---|---|
| DS09 | Region haplotypes and reads |
| DS10 | Wild and cultivated short-read panels; samples with recorded sex where available |
| DS20 | Flower small-RNA libraries for the optional Fig 3 |
| DS01 | PN_T2T coordinates and autosomal control windows |

New public data: none needed. Which panels record sex per sample is listed in DS10 [待确认].

## Analysis steps

Shared modules, in order:

1. [AM01 · Download and verify](../../analyses/AM01-download-and-verify/)
2. [AM03 · Short-read mapping and small-variant calling](../../analyses/AM03-short-read-variants/)
3. [AM25 · Small-RNA and phasiRNA loci](../../analyses/AM25-small-rna-phasirna/)

Project-specific steps:

- Select wild samples (M, F) and cultivated samples (H, F); infer sex types from region genotypes and check against recorded sex.
- Genotype the region (AM03); build haplotype networks.
- Optional: phasiRNA from small RNA by flower sex type (AM25).

**Stepwise work plan with tools**

| Step | Work | Tools (paper) | Output |
|---|---|---|---|
| 1 | Download and verify | AM01 | Read sets |
| 2 | Map and call variants in the region and autosomal controls | AM03 | VCFs |
| 3 | Infer sex genotypes; check against recorded sex | custom | Sample table |
| 4 | Phase region haplotypes; diversity by class | WhatsHap or SHAPEIT5, pixy | Fig 1 |
| 5 | Haplotype networks and trees | PopART-type networks, IQ-TREE 2 | Fig 2 |
| 6 | Optional phasiRNA loci by sex type | ShortStack (AM25) | Fig 3 |

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

## Risks and how to handle them

Added 2026-11-26. Each row names a risk, the evidence behind it, and a concrete check or fallback. Sources cited here were read for this section and their DOIs were checked on Crossref; preprints are marked.

| Area | Risk | Check or mitigation |
|---|---|---|
| Data access and licence | Sex-locus haplotypes (DS09) and the small-RNA atlas (DS20) are available; other small-RNA libraries are an open query ([data/DOWNLOADS.md](../../data/DOWNLOADS.md)). | Freeze the run list; record flower sex source for every sample. |
| Few sexed wild samples | Public resequencing of wild grapevine with recorded sex is sparse; one study compared a single male and a single female *sylvestris* ([Ramos et al. 2020](https://doi.org/10.1038/s41598-020-76012-6)). | Count wild samples with recorded sex before any analysis; below the preregistered minimum the project stays demoted. |
| Circular sex calls | Validated KASP markers for male sterility (*VviINP1*) now exist across *Vitis*, *Muscadinia* and wide hybrids ([Vaughn et al. 2026](https://doi.org/10.21273/jashs05580-25)). Inferring sex from SDR genotypes and then studying the SDR would be circular. | Use recorded phenotypes for analysis; use marker-based sex only as a consistency check. |
| Reference bias and genome choice | SDR haplotypes vary in size, largely through repetitive elements ([Massonnet et al. 2025](https://doi.org/10.1038/s41467-025-61387-9)); mapping to one haplotype may bias diversity. | Map to all phased SDR haplotypes (graph or multi-reference) and compare. |
| Clones, synonyms and pedigree | Cultivated H haplotypes may trace to few origins and be shared by relatives. | Collapse by genotype and account for pedigree. |
| Computing cost | Small (one region). | None. |

**Recent and competing work (search of 2024 to 2026 literature on 2026-11-26)**

- The SDR was traced to a locus conserved across angiosperms, with phased haplotypes from six Vitaceae species and suppressed recombination shared by *Vitis* and *Muscadinia* ([Massonnet et al. 2025](https://doi.org/10.1038/s41467-025-61387-9)). A synthesis covers candidate sex-determining genes now known in about a dozen flowering plants ([Marais et al. 2025](https://doi.org/10.1093/jxb/eraf224)). The cross-genus question is answered; only the population-level part remains.

**What would end the idea, and the fallback.** If sexed wild samples stay below the minimum, the project remains demoted. The fallback is a short haplotype-diversity note on cultivated H haplotypes only.

**Journal-level realism.** Specialty plant evolution journal; the cross-genus result already sits in *Nature Communications*.

## Rough estimates

- Compute: small [draft]
- Effort: 1–2 months for one person [draft]
- Target: plant evolution journal [draft]

## Suggested journal level (suggestion only)

**Specialty to mid-field journal (plant evolution or plant genetics).** Grape sex-region papers read here appeared in *Nature Communications*, *PNAS*, *Genome Biology*, *BMC Plant Biology* and *Molecular Genetics and Genomics*. A population-level follow-up with no new assemblies fits a specialty or mid-field venue. This is a suggestion, not a decision; impact factors are not used.

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
- Charlesworth 2016. Plant Sex Chromosomes. *Annu Rev Plant Biol*. [doi:10.1146/annurev-arplant-043015-111911](https://doi.org/10.1146/annurev-arplant-043015-111911)
- Fechter et al. 2012. Candidate genes within a 143 kb region of the flower sex locus in Vitis. *Molecular Genetics and Genomics*. [doi:10.1007/s00438-012-0674-z](https://doi.org/10.1007/s00438-012-0674-z)
- Picq et al. 2014. A small XY chromosomal region explains sex determination in wild dioecious V. vinifera and the reversal to hermaphroditism in domesticated grapevines. *BMC Plant Biology*. [doi:10.1186/s12870-014-0229-z](https://doi.org/10.1186/s12870-014-0229-z)
- Xia et al. 2019. 24-nt reproductive phasiRNAs are broadly present in angiosperms. *Nature Communications*. [doi:10.1038/s41467-019-08543-0](https://doi.org/10.1038/s41467-019-08543-0)
- Zhai et al. 2015. Spatiotemporally dynamic, cell-type–dependent premeiotic and meiotic phasiRNAs in maize anthers. *Proceedings of the National Academy of Sciences*. [doi:10.1073/pnas.1418918112](https://doi.org/10.1073/pnas.1418918112)
- Zou et al. 2021. Multiple independent recombinations led to hermaphroditism in grapevine. *Proceedings of the National Academy of Sciences*. [doi:10.1073/pnas.2023548118](https://doi.org/10.1073/pnas.2023548118)
- Ramos et al. 2020. Portuguese wild grapevine genome re-sequencing (Vitis vinifera sylvestris). *Scientific Reports*. [doi:10.1038/s41598-020-76012-6](https://doi.org/10.1038/s41598-020-76012-6)
- Vaughn et al. 2026. Diagnostic KASP Markers for Flower Sex and Stenospermocarpic Seedlessness in Diverse Vitis, Muscadinia, and Wide Hybrid Populations. *J. Amer. Soc. Hort. Sci*. [doi:10.21273/jashs05580-25](https://doi.org/10.21273/jashs05580-25)
- Marais et al. 2025. Plant sex-determining genes and the genetics of the evolution towards dioecy. *Journal of Experimental Botany*. [doi:10.1093/jxb/eraf224](https://doi.org/10.1093/jxb/eraf224)
