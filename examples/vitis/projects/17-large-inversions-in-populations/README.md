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

**Background survey (literature read for this plan)**

Chromosomal inversions suppress recombination in heterozygotes and can keep adaptive allele combinations together ([Kirkpatrick 2010](https://doi.org/10.1371/journal.pbio.1000501); [Wellenreuther and Bernatchez 2018](https://doi.org/10.1016/j.tree.2018.04.002)). Genomic methods show that inversions are common across plants ([Huang and Rieseberg 2020](https://doi.org/10.3389/fpls.2020.00296)). Resequencing of 1,506 wild sunflowers found 37 large non-recombining haplotype blocks (1 to 100 Mbp) tied to ecological traits ([Todesco et al. 2020](https://doi.org/10.1038/s41586-020-2467-6)), and long-read human work showed recurrent inversion polymorphisms linked to genomic instability ([Porubsky et al. 2022](https://doi.org/10.1016/j.cell.2022.04.017)). SyRI finds inversions and other rearrangements from whole-genome alignments ([Goel et al. 2019](https://doi.org/10.1186/s13059-019-1911-0)).

In grape, SV population genetics found purifying selection on inversions and large inversions at the sex and colour loci ([Zhou et al. 2019](https://doi.org/10.1038/s41477-019-0507-8)). Grapepan reported SVs among T2T haplotypes ([Liu et al. 2024](https://doi.org/10.1038/s41588-024-01967-5)), the *Vitis* super-pangenome extended this to wild species ([Guo et al. 2025](https://doi.org/10.1038/s41588-025-02111-7)), and T2T Cabernet Sauvignon haplotypes annotated a heterozygous inversion ([Khan et al. 2026](https://doi.org/10.1038/s41597-026-06910-3)). PN_T2T gives gap-free coordinates for breakpoints ([Shi et al. 2023](https://doi.org/10.1093/hr/uhad061)).

**Specific gap.** No population-scale inversion atlas for grape was found with breakpoint validation, short-read genotyping and a test of suppressed recombination between arrangements [待确认].

## Question

How many large inversions segregate in grape, and do they show the haplotype structure expected from suppressed recombination?

## Hypotheses, planned figures and criteria

No results are given here. Each row says what would count as support; the exact thresholds go into the preregistration.

| Figure or table | Hypothesis or purpose | Criterion |
|---|---|---|
| Fig 1. Inversion catalogue | Not a hypothesis: catalogue with validated breakpoints. | Breakpoints confirmed by long reads where available. |
| Fig 2. Graph genotypes vs assembly genotypes | Graph genotyping recovers assembly genotypes. | Concordance on samples with both. |
| Fig 3. Differentiation between arrangements | Inversions suppress recombination in heterozygotes, so the two arrangements differ most near the breakpoints and the inversion genotype is in LD with SNPs inside. | After keeping one sample per clone group (project 08): F_ST between arrangements along the inversion and LD between inversion genotype and SNPs; permutation by within-chromosome window blocks. |

**Expected results and how they will be read**

- Fig 1 is the validated catalogue; inversions without long-read support at both breakpoints are listed separately as candidates.
- Fig 2: high concordance between graph and assembly genotypes allows population frequencies; low concordance limits the study to assemblies.
- Fig 3: differentiation peaking at breakpoints and LD between inversion genotype and inner SNPs would confirm suppressed recombination; absence of the pattern suggests gene flux or recent origin.
- Any link to traits is left to a separate preregistered test.

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

**How each dataset is used**

| Module | Role in this project |
|---|---|
| DS02, DS03, DS07 | Haplotypes for discovery and long reads for breakpoint checks |
| DS10 | Short-read panel for genotyping |
| DS01 | PN_T2T coordinates |

New public data: none needed. The T2T Cabernet Sauvignon haplotypes (Khan et al. 2026) can be added to DS02/DS03 lists only after their accession is confirmed in a data module [待确认].

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

**Stepwise work plan with tools**

| Step | Work | Tools (paper) | Output |
|---|---|---|---|
| 1 | Assembly QC; pairwise alignment of haplotypes to PN_T2T | AM05, minimap2 | Alignments |
| 2 | Call inversions and merge across haplotypes | SyRI (AM06) | Inversion catalogue |
| 3 | Validate both breakpoints with long reads | AM18 | Validated set |
| 4 | Add to the graph; genotype the short-read panel | PanGenie or vg (AM07) | Genotypes |
| 5 | Concordance with assembly genotypes | custom | Fig 2 |
| 6 | FST and dXY between arrangements along the inversion; LD with inner SNPs | PLINK 2, pixy | Fig 3 |

## Paper design and split

| Paper | Working title | Type | Figures |
|---|---|---|---|
| Q1 | A population atlas of large inversions in grape | main paper | Fig 1–3 |

Each paper: introduction from the gap above; one results section per figure; methods with tool versions from the modules; data availability listing every accession used and the derived tables.

## Risks and novelty check

- Risk: Inversions flanked by repeats are hard to genotype from short reads.
- Risk: Uses the sample set from project 08.
- Novelty: checked against the existing work above (Crossref-verified DOIs). Repeat the search before writing; anything marked [待确认] is not yet verified.

## Risks and how to handle them

Added 2026-11-26. Each row names a risk, the evidence behind it, and a concrete check or fallback. Sources cited here were read for this section and their DOIs were checked on Crossref; preprints are marked.

| Area | Risk | Check or mitigation |
|---|---|---|
| Data access and licence | Assemblies, graph and INSDC panels are listed as available ([data/DOWNLOADS.md](../../data/DOWNLOADS.md)). | Freeze versions; the sample set comes from project 08. |
| Inversions are common but often neutral | Across 35 songbird species large inversion polymorphisms were widespread, and in genome-wide studies they are generally hard to link to phenotypes ([Pegan et al. 2025](https://doi.org/10.1093/gbe/evaf205)). | Do not assume selection; test suppressed recombination and haplotype structure first, and treat adaptive claims as a separate, optional step. |
| Genotyping from short reads | Large complex SVs can be genotyped from a pangenome graph ([Rice et al. 2023](https://doi.org/10.1186/s12915-023-01758-0)), but inversions with repeat-rich breakpoints are hard (see above). | Use two independent signals: graph genotypes at breakpoints and SNP-based haplotype blocks; keep only inversions where both agree. |
| Recombination tests | Structural context decided how inversions changed the recombination landscape in 374 F1 seedlings of a pineapple cross ([Fang et al. 2026](https://doi.org/10.1093/hr/uhag189)). | Where family data exist (project 24), compare crossovers inside and outside each inversion directly. |
| Reference bias and genome choice | Inversions are defined relative to the assemblies compared; between-haplotype inversions exist within single cultivars ([Djari et al. 2024](https://doi.org/10.1073/pnas.2403750121)). | Polarise each inversion with an outgroup assembly and report orientation per haplotype. |
| Clones, synonyms and pedigree | Related samples inflate haplotype frequencies. | One sample per genotype; account for known pedigrees. |
| Sample size and power | Rare inversions have few carriers for LD tests. | Fix a minimum carrier count. |
| Computing cost | Assembly comparisons are moderate; graph genotyping of panels is larger. | Genotype only candidate breakpoints, not whole genomes. |

**Recent and competing work (search of 2024 to 2026 literature on 2026-11-26)**

- A synthesis of recombination suppression in plants covers inversions, sex chromosomes and speciation ([Zhang et al. 2026](https://doi.org/10.1111/nph.71026)). Grape SV surveys of single cultivars ([Maestri et al. 2022](https://doi.org/10.1186/s12864-022-08389-9)), between-haplotype comparisons ([Djari et al. 2024](https://doi.org/10.1073/pnas.2403750121)) and haplotype-resolved 3D genomes ([Peng et al. 2026](https://doi.org/10.1002/advs.202521838)) cover only a few cultivars; a population-level inversion atlas for grape was not found.

**What would end the idea, and the fallback.** If few large inversions segregate within *V. vinifera* (most being fixed between species), there is little to test at population level. The fallback is a between-species inversion catalogue with breakpoint annotation.

**Journal-level realism.** Mid-field genome biology or evolution; a broad venue would need a clear trait or adaptation link (see the suggested journal level below).

## Rough estimates

- Compute: medium [draft]
- Effort: 2–4 months for one person [draft]
- Target: genome journal [draft]

## Suggested journal level (suggestion only)

**Mid-field journal (genome biology or evolution).** Inversion studies read here appeared in *Nature* and *Cell* when they linked inversions to ecotypes or disease, and in *Trends in Ecology & Evolution*, *PLoS Biology* and *Frontiers in Plant Science* for syntheses; grape SV resources in *Nature Plants*, *Nature Genetics* and *Scientific Data*. A grape atlas with recombination tests fits a mid-field venue. This is a suggestion, not a decision; impact factors are not used.

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
- Goel et al. 2019. SyRI: finding genomic rearrangements and local sequence differences from whole-genome assemblies. *Genome Biology*. [doi:10.1186/s13059-019-1911-0](https://doi.org/10.1186/s13059-019-1911-0)
- Guo et al. 2025. Super pangenome of Vitis empowers identification of downy mildew resistance genes for grapevine improvement. *Nature Genetics*. [doi:10.1038/s41588-025-02111-7](https://doi.org/10.1038/s41588-025-02111-7)
- Huang et al. 2020. Frequency, Origins, and Evolutionary Role of Chromosomal Inversions in Plants. *Frontiers in Plant Science*. [doi:10.3389/fpls.2020.00296](https://doi.org/10.3389/fpls.2020.00296)
- Kirkpatrick 2010. How and Why Chromosome Inversions Evolve. *PLoS Biology*. [doi:10.1371/journal.pbio.1000501](https://doi.org/10.1371/journal.pbio.1000501)
- Porubsky et al. 2022. Recurrent inversion polymorphisms in humans associate with genetic instability and genomic disorders. *Cell*. [doi:10.1016/j.cell.2022.04.017](https://doi.org/10.1016/j.cell.2022.04.017)
- Shi et al. 2023. The complete reference genome for grapevine (Vitis vinifera L.) genetics and breeding. *Horticulture Research*. [doi:10.1093/hr/uhad061](https://doi.org/10.1093/hr/uhad061)
- Todesco et al. 2020. Massive haplotypes underlie ecotypic differentiation in sunflowers. *Nature*. [doi:10.1038/s41586-020-2467-6](https://doi.org/10.1038/s41586-020-2467-6)
- Wellenreuther et al. 2018. Eco-Evolutionary Genomics of Chromosomal Inversions. *Trends in Ecology & Evolution*. [doi:10.1016/j.tree.2018.04.002](https://doi.org/10.1016/j.tree.2018.04.002)
- Pegan et al. 2025. Large Inversion Polymorphisms are Widespread in North American Songbirds. *Genome Biology and Evolution*. [doi:10.1093/gbe/evaf205](https://doi.org/10.1093/gbe/evaf205)
- Rice et al. 2023. A pangenome graph reference of 30 chicken genomes allows genotyping of large and complex structural variants. *BMC Biology*. [doi:10.1186/s12915-023-01758-0](https://doi.org/10.1186/s12915-023-01758-0)
- Fang et al. 2026. The heterozygous pineapple genome demonstrates the importance of haplotype-resolved plant genomes. *Horticulture Research*. [doi:10.1093/hr/uhag189](https://doi.org/10.1093/hr/uhag189)
- Djari et al. 2024. Haplotype-resolved genome assembly and implementation of VitExpress, an open interactive transcriptomic platform for grapevine. *Proceedings of the National Academy of Sciences*. [doi:10.1073/pnas.2403750121](https://doi.org/10.1073/pnas.2403750121)
- Zhang et al. 2026. Recombination suppression in plant adaptation and speciation. *New Phytologist*. [doi:10.1111/nph.71026](https://doi.org/10.1111/nph.71026)
- Maestri et al. 2022. ‘Nebbiolo’ genome assembly allows surveying the occurrence and functional implications of genomic structural variations in grapevines (Vitis vinifera L.). *BMC Genomics*. [doi:10.1186/s12864-022-08389-9](https://doi.org/10.1186/s12864-022-08389-9)
- Peng et al. 2026. Haplotype‐Resolved 3D Genomic Landscapes and Their Impacts on Agronomic Traits in Grapevine. *Advanced Science*. [doi:10.1002/advs.202521838](https://doi.org/10.1002/advs.202521838)
