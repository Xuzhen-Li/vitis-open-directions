# 01. Telomeres and interstitial telomeric repeats across near-complete grape haplotypes

中文：近完整葡萄单倍型的端粒与间质端粒重复

Rank 1 of 22 (score F 3 + N 2 + E 3 = 8; see docs/RANKING.md) · Tier: Quick (E = 3, effort range ending at 6 weeks or less) · Origin: continued: started earlier and restarted here from public data under a new preregistration · Status: draft v0.3.2, 2026-11-14

## Gap

Telomere arrays are reported one assembly at a time. A comparison of telomere array length and interstitial telomeric repeat (ITS) positions across all public near-complete *Vitis* and Vitaceae haplotypes, with assembly technology as a covariate, was not found [待确认: repeat the search before writing].

**Existing work**

- [Shi et al. 2023](https://doi.org/10.1093/hr/uhad061): PN_T2T reference with telomeres at chromosome ends.
- [Liu et al. 2024](https://doi.org/10.1038/s41588-024-01967-5): nine T2T diploid grapes.
- [Wang et al. 2026](https://doi.org/10.1038/s41477-026-02442-1): chromosome-level genomes across Vitaceae.

**How this project differs**

Uses every public near-complete haplotype with one scan and one QC rule, separates biology from assembly technology, and places ITS relative to known karyotype changes.

**Background survey (literature read for this plan)**

Most land plants carry the Arabidopsis-type telomere repeat TTTAGGG, but the motif has changed several times during plant evolution, so the motif must be checked for each lineage before scanning ([Peška et al. 2020](https://doi.org/10.3389/fpls.2020.00117)). The community database TeloBase collects confirmed telomere motifs across the tree of life ([Lyčka et al. 2024](https://doi.org/10.1093/nar/gkad672)), and T2T-Hub gathers telomere-to-telomere plant and animal genomes ([Chao et al. 2026](https://doi.org/10.1093/nar/gkag423)). Telomere length varies among natural accessions: 229 *Arabidopsis thaliana* accessions showed accession-specific lengths, and loci for the variation were mapped ([Fulcher et al. 2015](https://doi.org/10.1534/genetics.114.172163)); resequencing and restriction-fragment assays found intraspecific variation in *A. thaliana*, rice and maize, with an association signal at the telomerase (TERT) region and a link to flowering time ([Choi et al. 2021](https://doi.org/10.1093/plcell/koab022)). These studies estimated length from reads or by molecular assays, not from many near-complete haplotypes of one genus.

Interstitial telomeric repeats (ITS) are short telomere-like arrays away from chromosome ends. In the *Arabidopsis* genome eight ITS of 300 to 1200 bp were identified and grouped by how degenerate their repeats are ([Uchida et al. 2002](https://doi.org/10.1266/ggs.77.63)); in vertebrates they are traced to chromosome fusions, repair of double-strand breaks and repeat expansion, and some are unstable ([Bolzán 2017](https://doi.org/10.1016/j.mrrev.2017.04.002)). Fusion-derived karyotype change has been reconstructed across Brassicaceae with chromosome-level genomes ([Jiang et al. 2025](https://doi.org/10.1038/s41467-025-59640-2)). Scanning tools now exist for assemblies and reads: tidk finds telomere repeats in genomic data ([Brown et al. 2025](https://doi.org/10.1093/bioinformatics/btaf049)), quarTeT reports telomeres and centromeric repeats in T2T workflows ([Lin et al. 2023](https://doi.org/10.1093/hr/uhad127)), and Tandem Repeats Finder remains the general tandem-repeat detector ([Benson 1999](https://doi.org/10.1093/nar/27.2.573)).

In grape, PN_T2T reports telomeres at chromosome ends ([Shi et al. 2023](https://doi.org/10.1093/hr/uhad061)), the Grapepan study released T2T haplotypes of nine grapes ([Liu et al. 2024](https://doi.org/10.1038/s41588-024-01967-5)), the *Vitis* super-pangenome released 72 haplotype-resolved accessions ([Guo et al. 2025](https://doi.org/10.1038/s41588-025-02111-7)), and chromosome-level genomes now span Vitaceae ([Wang et al. 2026](https://doi.org/10.1038/s41477-026-02442-1)). The *Muscadinia* assembly supports a chromosome fusion that formed *Vitis* chr7 ([Cochetel et al. 2021](https://doi.org/10.1093/g3journal/jkab033)), which gives a known breakpoint to test ITS against.

**Specific gap.** Each grape assembly reports its own telomeres. No study was found that scans all public near-complete Vitaceae haplotypes with one rule, separates assembly technology from biology, and tests whether ITS sit at known karyotype breakpoints such as the chr7 fusion point [待确认: repeat the search before writing].

## Question

How much do telomere array lengths and ITS positions vary among grape haplotypes, and are ITS clusters found where karyotype changes are known?

## Hypotheses, planned figures and criteria

No results are given here. Each row says what would count as support; the exact thresholds go into the preregistration.

| Figure or table | Hypothesis or purpose | Criterion |
|---|---|---|
| Fig 1. Telomere presence at every chromosome end, by assembly and technology | Not a hypothesis: a completeness table. | Share of chromosome ends with a telomere array; completeness cut-off and minimum array length (in repeat units) fixed in advance; assemblies below the cut-off are excluded from length analyses. |
| Fig 2. Telomere array length within accession (haplotype 1 vs 2) and between accessions | Between-accession variance exceeds within-accession variance after adjusting for technology. | Mixed model with technology as a fixed effect and haplotype nested in accession; variance components estimated by REML and tested by likelihood ratio or parametric bootstrap; supported if the 95% interval for the between-accession component excludes zero. |
| Fig 3. ITS positions on chromosomes | ITS loci are enriched near known rearrangement breakpoints, including the fusion point on *Vitis* chr7, where the segments homologous to *Muscadinia* chr7 and chr20 meet (located on Cabernet Sauvignon and PN40024 chr7 by Cochetel et al. 2021). | Within-chromosome permutation against positions matched for GC content, repeat class, and chromosome position; one-sided test fixed in advance. |
| Table 1. Per-haplotype telomere and ITS catalogue | Resource table. | Every row traceable to an accession and a tool version. |

**Expected results and how they will be read**

- Fig 1 gives the share of chromosome ends with a telomere array per assembly; it decides which assemblies enter Fig 2. If most ends lack arrays in an older assembly, that assembly is used only for ITS positions.
- Fig 2: if the between-accession variance component excludes zero after technology is modelled, telomere length is treated as an accession trait worth a follow-up with read-level lengths; if not, the paper reports that assembled length mainly reflects technology.
- Fig 3: enrichment at breakpoints would support fusion-derived ITS; no enrichment would point to other origins (repeat expansion or repair) and is reported as a negative result.
- Table 1 is released whatever the test outcomes are.

## Preregistration

Before any data are analysed, fill in [`docs/PREREGISTRATION.md`](../../../../templates/PREREGISTRATION.md) for this project: hypotheses, primary outcome, sample inclusion rules, thresholds, stop rules and what will be reported if a hypothesis fails. Commit it with a date. Criteria from any earlier attempt are reference only and are not carried over.

## Data

| Module | Dataset |
|---|---|
| [DS01](../../data/DS01-pn40024-references/) | PN40024 references: PN_T2T (v5), PN40024.v4 and 12X |
| [DS02](../../data/DS02-grapepan-v1/) | Grapepan v1.0: T2T haplotypes, graphs and a 466-accession resequencing panel |
| [DS03](../../data/DS03-vitis-super-pangenome-72/) | Vitis super-pangenome: 72 haplotype-resolved accessions |
| [DS05](../../data/DS05-vitaceae-family-genomes/) | Vitaceae family chromosome-level genomes |
| [DS07](../../data/DS07-cultivated-16-pangenome/) | Cultivated grapevine pangenome (16 cultivars, Plastivigne) |
| [DS08](../../data/DS08-muscadinia-genomes/) | Muscadinia rotundifolia assemblies and reads |
| [DS16](../../data/DS16-vitaceae-assembly-index/) | Index of all Vitaceae assemblies in NCBI |
| [DS17](../../data/DS17-angiosperm-near-complete-assemblies/) | Near-complete angiosperm assemblies (comparison set) |

**How each dataset is used**

| Module | Role in this project |
|---|---|
| DS01 | PN_T2T as the coordinate system and first positive control for telomere calls |
| DS02, DS03, DS07 | Near-complete *V. vinifera* and wild *Vitis* haplotypes; same-accession haplotype pairs give the within-accession variance |
| DS05, DS08 | Other Vitaceae genera and *Muscadinia*; needed for the chr7 fusion test |
| DS16 | Assembly list and assembly technology for every Vitaceae entry |
| DS17 | Comparison set of near-complete angiosperm assemblies with confirmed motifs |

New public data: none needed. Read-level telomere length needs raw long reads; which of the assemblies above have public reads is [待确认] per accession in the module pages.

## Analysis steps

Shared modules, in order:

1. [AM01 · Download and verify](../../analyses/AM01-download-and-verify/)
2. [AM05 · Assembly QC](../../analyses/AM05-assembly-qc/)
3. [AM10 · Telomeres, centromeric satellites and rDNA arrays](../../analyses/AM10-repeat-arrays/)

Project-specific steps:

- Pick near-complete assemblies from DS16 (Vitaceae) and, as a comparison set, DS17.
- Run AM05 QC; drop assemblies that fail the preregistered completeness cut-off.
- Run tidk and TRF (AM10) on every haplotype; record array start, end and length.
- Map ITS positions to PN_T2T through whole-genome alignment and test enrichment at breakpoints, including the *Vitis* chr7 fusion point (shared with the centromere project).

**Stepwise work plan with tools**

| Step | Work | Tools (paper) | Output |
|---|---|---|---|
| 1 | List near-complete assemblies with technology, contig N50 and gap count | ncbi-datasets-cli, DS16 table | Assembly manifest with sha256 |
| 2 | Assembly QC and completeness cut-off fixed in the preregistration | compleasm or BUSCO, Merqury ([Rhie et al. 2020](https://doi.org/10.1186/s13059-020-02134-9)) | Pass/fail list |
| 3 | Confirm the motif per lineage from TeloBase before scanning | TeloBase | Motif table |
| 4 | Scan ends and interior on both strands; record array start, end, length and purity | tidk, quarTeT, TRF | Per-haplotype array table |
| 5 | Decoy-motif and shuffled-sequence controls; Arabidopsis T2T positive control | custom scan with fixed decoys | Control report (gate) |
| 6 | Map ITS to PN_T2T by whole-genome alignment and place them on the Vitaceae karyotype | minimap2, SyRI (AM06) | ITS coordinates on PN_T2T |
| 7 | Mixed model for length (technology fixed, accession and haplotype random); permutation test for ITS at breakpoints | R lme4, bootstrap | Fig 2, Fig 3 statistics |
| 8 | Release Table 1 and all scan outputs | Zenodo deposit | Resource table |

## Paper design and split

| Paper | Working title | Type | Figures |
|---|---|---|---|
| A1 | Telomere and ITS variation across near-complete grape haplotypes | short paper or data note | Fig 1–3, Table 1 |
| A2 | Joint repeat-array paper with project 02 (rDNA) | optional merger | Figures of both projects |

Each paper: introduction from the gap above; one results section per figure; methods with tool versions from the modules; data availability listing every accession used and the derived tables.

## Risks and novelty check

- Risk: Array length in an assembly is a lower bound when reads do not span the array.
- Risk: Assemblers can trim telomeres; technology must be modelled.
- Risk: Novelty: no dedicated literature search on this topic has been done beyond the grape literature base yet [待确认: repeat the search before writing].
- Novelty: checked against the existing work above (Crossref-verified DOIs). Repeat the search before writing; anything marked [待确认] is not yet verified.

## Risks and how to handle them

Added 2026-11-26. Each row names a risk, the evidence behind it, and a concrete check or fallback. Sources cited here were read for this section and their DOIs were checked on Crossref; preprints are marked.

| Area | Risk | Check or mitigation |
|---|---|---|
| Data access and licence | DS01 to DS08 and DS16 are listed as available, but DS17 is an open query rather than a closed accession list ([data/DOWNLOADS.md](../../data/DOWNLOADS.md)). INSDC records are free and open to reuse ([INSDC 2024](https://doi.org/10.1093/nar/gkae1058)). | Freeze the assembly list (accession and version) on the day of the scan and store it with the results; cite each assembly paper. |
| Sample size and power | The within-accession variance needs both haplotypes of one accession; only haplotype-resolved sets give that. | Before any test, count accessions with two haplotypes that both reach a telomere at the same chromosome end; below the preregistered minimum, report lengths descriptively only. |
| Technology and source differences | Telomere length read from an assembly depends on the reads: assemblies from Oxford Nanopore reads matched laboratory length estimates in *Arabidopsis* and rice ([Colt et al. 2024](https://doi.org/10.1101/2024.03.27.586973), preprint), while arrays that reads do not span are only lower bounds. | Model technology (HiFi, ONT, hybrid) as a covariate and compare accessions within one technology first. Where public long reads exist, estimate length from reads as well; allele-specific telomere lengths can be read from long reads ([Stephens et al. 2024](https://doi.org/10.1186/s12859-024-05807-5)). |
| Biological noise | Grapevine telomere length changed within one season and differed between rainfed and irrigated field vines measured by qPCR ([Iannuzzi et al. 2026](https://doi.org/10.3390/plants15131988)). Public genomes come from different tissues, ages and growing conditions. | Treat differences between accessions as descriptive, not genetic, unless the two haplotypes of one accession agree with each other; do not interpret absolute lengths across studies. |
| Reference bias and genome choice | Not a mapping problem here, but the motif is: plant telomere motifs changed several times ([Peška et al. 2020](https://doi.org/10.3389/fpls.2020.00117)). | Run a motif-discovery pass (tidk explore) on each genus before the fixed-motif scan. |
| Clones, synonyms and pedigree | Several public assemblies can be the same genotype: a medieval pip was genetically identical to modern Pinot noir ([Noraz et al. 2026](https://doi.org/10.1038/s41467-026-70166-z)), so cultivar names do not guarantee independent samples. | Collapse assemblies of one genotype (identity table of project 08) before population statistics; keep repeated assemblies of one genotype as a technical replicate of length calls. |
| Annotation and method failure | ITS calls depend on how degenerate a repeat may be; in wheat, re-mapping tandem repeats on a T2T assembly resolved several disagreements between genome and FISH maps ([Garrido-Ramos et al. 2026](https://doi.org/10.1007/s11103-026-01745-3)). | Fix the degeneracy threshold in the preregistration; report ITS counts at two thresholds; compare with published cytogenetic positions where they exist. |
| Computing cost | Scans run on assemblies only. | Read-based length estimates are limited to accessions with public long reads; time one accession first and extrapolate before scheduling the rest. |
| Alternative methods and sensitivity | One scanner can miss arrays split by assembly gaps. | Run tidk and quarTeT on every assembly and Tandem Repeats Finder on discordant ends; report agreement per end. |

**Recent and competing work (search of 2024 to 2026 literature on 2026-11-26)**

- Telomere length by chromosome has been estimated from long-read assemblies across many plant species ([Colt et al. 2024](https://doi.org/10.1101/2024.03.27.586973), preprint). The method itself is therefore not new; the contribution here must come from same-accession haplotype pairs within one genus and from the ITS test.
- A family-wide phylogenomic study released 27 new Vitaceae assemblies and reconstructed the chromosome rearrangements of Vitaceae karyotype evolution ([Wang et al. 2026](https://doi.org/10.64898/2026.04.20.719760), preprint). Its assemblies should enter the scan, and its rearrangement map is the reference for placing ITS. Check its full text for any ITS analysis before writing.

**What would end the idea, and the fallback.** If the two haplotypes of one accession differ as much as different accessions, or if length tracks sequencing technology only, telomere length is not a usable trait here. The fallback is a short technical note on telomere recovery in grape assemblies plus the ITS catalogue, or the joint repeat-array paper with project 02.

**Journal-level realism.** With a cross-species long-read telomere survey already public as a preprint, a grape-only length table fits a specialty journal. Only a clear ITS signal at known fusion or rearrangement points would support a higher venue.

## Rough estimates

- Compute: small [draft]
- Effort: 3–6 weeks for one person [draft]
- Target: genome or plant genetics journal [draft]

## Suggested journal level (suggestion only)

**Specialty journal (plant genomics or chromosome biology).** Telomere-motif and telomere-length surveys read for this plan appeared in specialty or field journals (*Frontiers in Plant Science*, *Genetics*, *The Plant Cell*), and the tool and database papers in *Bioinformatics*, *Horticulture Research* and *Nucleic Acids Research*. A descriptive cross-haplotype catalogue fits a specialty venue; a mid-field venue becomes realistic only if Fig 2 or Fig 3 gives a clear positive result. This is a suggestion, not a decision; impact factors are not used.

## Continue on HPC

Run each step as its own job, in this order. Every job writes `.DONE` or `.FAILED` and a log; the next step starts only after `.DONE`. Template and rules: [`docs/HPC_JOBS.md`](../../../../templates/HPC_JOBS.md).

| Order | Step | Main tools | Resources (rough) |
|---|---|---|---|
| 1 | [AM01](../../analyses/AM01-download-and-verify/) Download and verify | ncbi-datasets-cli, sra-tools, ENA FTP / Aspera | 1–4 CPU, 4 GB, network; array over files |
| 2 | [AM05](../../analyses/AM05-assembly-qc/) Assembly QC | compleasm, BUSCO, Merqury | 16 CPU, 64 GB, 1–3 h per assembly; array |
| 3 | [AM10](../../analyses/AM10-repeat-arrays/) Telomeres, centromeric satellites and rDNA arrays | tidk, TRF, TRASH | 8 CPU, 16 GB per assembly |

Public inputs: [DS01](../../data/DS01-pn40024-references/), [DS02](../../data/DS02-grapepan-v1/), [DS03](../../data/DS03-vitis-super-pangenome-72/), [DS05](../../data/DS05-vitaceae-family-genomes/), [DS07](../../data/DS07-cultivated-16-pangenome/), [DS08](../../data/DS08-muscadinia-genomes/), [DS16](../../data/DS16-vitaceae-assembly-index/), [DS17](../../data/DS17-angiosperm-near-complete-assemblies/).

## References

- Shi et al. 2023. The complete reference genome for grapevine ( Vitis vinifera L.) genetics and breeding. *Horticulture Research*. [doi:10.1093/hr/uhad061](https://doi.org/10.1093/hr/uhad061)
- Liu et al. 2024. Grapevine pangenome facilitates trait genetics and genomic breeding. *Nature Genetics*. [doi:10.1038/s41588-024-01967-5](https://doi.org/10.1038/s41588-024-01967-5)
- Wang et al. 2026. Chromosome-level phylogenomics and genome evolution of the grape family. *Nature Plants*. [doi:10.1038/s41477-026-02442-1](https://doi.org/10.1038/s41477-026-02442-1)
- Benson 1999. Tandem repeats finder: a program to analyze DNA sequences. *Nucleic Acids Research*. [doi:10.1093/nar/27.2.573](https://doi.org/10.1093/nar/27.2.573)
- Bolzán 2017. Interstitial telomeric sequences in vertebrate chromosomes: Origin, function, instability and evolution. *Mutat Res Rev Mutat Res*. [doi:10.1016/j.mrrev.2017.04.002](https://doi.org/10.1016/j.mrrev.2017.04.002)
- Brown et al. 2025. tidk: a toolkit to rapidly identify telomeric repeats from genomic datasets. *Bioinformatics*. [doi:10.1093/bioinformatics/btaf049](https://doi.org/10.1093/bioinformatics/btaf049)
- Chao et al. 2026. T2T-Hub: a central platform for analyzing plant and animal telomere-to-telomere genomes. *Nucleic Acids Research*. [doi:10.1093/nar/gkag423](https://doi.org/10.1093/nar/gkag423)
- Choi et al. 2021. Natural variation in plant telomere length is associated with flowering time. *The Plant Cell*. [doi:10.1093/plcell/koab022](https://doi.org/10.1093/plcell/koab022)
- Cochetel et al. 2021. Diploid chromosome-scale assembly of the Muscadinia rotundifolia genome supports chromosome fusion and disease resistance gene expansion during Vitis and Muscadinia divergence. *G3 Genes|Genomes|Genetics*. [doi:10.1093/g3journal/jkab033](https://doi.org/10.1093/g3journal/jkab033)
- Fulcher et al. 2015. Genetic Architecture of Natural Variation of Telomere Length in Arabidopsis thaliana. *Genetics*. [doi:10.1534/genetics.114.172163](https://doi.org/10.1534/genetics.114.172163)
- Guo et al. 2025. Super pangenome of Vitis empowers identification of downy mildew resistance genes for grapevine improvement. *Nature Genetics*. [doi:10.1038/s41588-025-02111-7](https://doi.org/10.1038/s41588-025-02111-7)
- Jiang et al. 2025. Chromosome fusions shaped karyotype evolution and evolutionary relationships in the model family Brassicaceae. *Nature Communications*. [doi:10.1038/s41467-025-59640-2](https://doi.org/10.1038/s41467-025-59640-2)
- Lin et al. 2023. quarTeT: a telomere-to-telomere toolkit for gap-free genome assembly and centromeric repeat identification. *Horticulture Research*. [doi:10.1093/hr/uhad127](https://doi.org/10.1093/hr/uhad127)
- Lyčka et al. 2024. TeloBase: a community-curated database of telomere sequences across the tree of life. *Nucleic Acids Research*. [doi:10.1093/nar/gkad672](https://doi.org/10.1093/nar/gkad672)
- Peska et al. 2020. Origin, Diversity, and Evolution of Telomere Sequences in Plants. *Frontiers in Plant Science*. [doi:10.3389/fpls.2020.00117](https://doi.org/10.3389/fpls.2020.00117)
- Rhie et al. 2020. Merqury: reference-free quality, completeness, and phasing assessment for genome assemblies. *Genome Biology*. [doi:10.1186/s13059-020-02134-9](https://doi.org/10.1186/s13059-020-02134-9)
- Uchida et al. 2002. Interstitial telomere-like repeats in the Arabidopsis thaliana genome. *Genes & Genetic Systems*. [doi:10.1266/ggs.77.63](https://doi.org/10.1266/ggs.77.63)
- INSDC 2024. The international nucleotide sequence database collaboration (INSDC): enhancing global participation. *Nucleic Acids Research*. [doi:10.1093/nar/gkae1058](https://doi.org/10.1093/nar/gkae1058)
- Colt et al. 2024. Telomere Length in Plants Estimated with Long Read Sequencing. *bioRxiv* (preprint). [doi:10.1101/2024.03.27.586973](https://doi.org/10.1101/2024.03.27.586973)
- Stephens et al. 2024. Characterization of telomere variant repeats using long reads enables allele-specific telomere length estimation. *BMC Bioinformatics*. [doi:10.1186/s12859-024-05807-5](https://doi.org/10.1186/s12859-024-05807-5)
- Iannuzzi et al. 2026. Association Between Contrasting Water Regimes and Telomere Length Variation in Field-Grown Grapevines: An Integrated Physiological, Metabolomic and Molecular Approach. *Plants*. [doi:10.3390/plants15131988](https://doi.org/10.3390/plants15131988)
- Noraz et al. 2026. Ancient DNA reveals 4000 years of grapevine diversity, viticulture and clonal propagation in France. *Nature Communications*. [doi:10.1038/s41467-026-70166-z](https://doi.org/10.1038/s41467-026-70166-z)
- Garrido-Ramos et al. 2026. Detailed re-analysis of satellitome mapping facilitated by the telomere-to-telomere (T2T) assembly of bread wheat genome. *Plant Molecular Biology*. [doi:10.1007/s11103-026-01745-3](https://doi.org/10.1007/s11103-026-01745-3)
- Wang et al. 2026. Origin and evolution of grapevine genomes. *bioRxiv* (preprint). [doi:10.64898/2026.04.20.719760](https://doi.org/10.64898/2026.04.20.719760)
