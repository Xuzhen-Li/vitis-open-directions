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

**Background survey (literature read for this plan)**

Plant 45S (18S-5.8S-26S) and 5S rDNA are tandem arrays whose number and chromosomal position have mostly been recorded by cytogenetics. The Plant rDNA database collects locus number, position and unit arrangement across land plants and relates them to chromosome number, genome size and ploidy ([Garcia et al. 2017](https://doi.org/10.1111/tpj.13442)). In *Arabidopsis thaliana* the two nucleolus organizer regions (NORs) were mapped to the tips of chromosomes 2 and 4 ([Copenhaver and Pikaard 1996](https://doi.org/10.1046/j.1365-313X.1996.09020259.x)), and copy-number variation in 45S rRNA genes explains much of the genome-size variation among accessions but is inherited unstably ([Rabanal et al. 2017](https://doi.org/10.1534/g3.117.040204)). Telomeres and rDNA arrays share chromatin features and often sit next to each other ([Dvořáčková et al. 2015](https://doi.org/10.1111/tpj.12822)).

Long reads have recently made full NOR sequences possible. NOR2 of *Arabidopsis* was sequenced with long and short reads ([Sims et al. 2021](https://doi.org/10.1038/s41467-020-20728-6)), and ultralong reads gave about 5.5 and 3.9 Mbp sequences for NOR2 and NOR4 with active and silent regions mapped ([Fultz et al. 2023](https://doi.org/10.1126/sciadv.adj4509)). The maize Mo17 T2T assembly traversed every chromosome in one contig, including its repetitive regions ([Chen et al. 2023](https://doi.org/10.1038/s41588-023-01419-6)). Ribotin assembles and phases full-length rDNA units (morphs) from accurate long reads, because standard assemblers still collapse most arrays ([Rautiainen 2024](https://doi.org/10.1093/bioinformatics/btae124)).

For grape, PN_T2T is gap-free ([Shi et al. 2023](https://doi.org/10.1093/hr/uhad061)) and Grapepan added T2T haplotypes of nine grapes ([Liu et al. 2024](https://doi.org/10.1038/s41588-024-01967-5)); chromosome-level genomes now cover other Vitaceae genera ([Wang et al. 2026](https://doi.org/10.1038/s41477-026-02442-1)). How completely the rDNA arrays were assembled in these haplotypes was not reported as a comparison.

**Specific gap.** No public table was found that gives, for every near-complete Vitaceae haplotype, the position of each 45S and 5S array, whether it is closed by unique flanks, and its assembled length, nor one that compares assembled arrays with read-based copy number [待确认].

## Question

Where are the 45S and 5S rDNA arrays in grape haplotypes, how often are they fully assembled, and are their positions conserved across Vitaceae?

## Hypotheses, planned figures and criteria

No results are given here. Each row says what would count as support; the exact thresholds go into the preregistration.

| Figure or table | Hypothesis or purpose | Criterion |
|---|---|---|
| Fig 1. Array positions across haplotypes | Array positions are conserved within *Vitis*. | Positions compared after mapping to PN_T2T; conservation is called when a locus is present in all complete haplotypes of a species; the number of complete haplotypes (denominator) is reported per species. |
| Fig 2. Assembled array length vs assembly technology | Array length is limited by assembly technology. | Assembled length is a lower bound, so length is modelled with censored regression (Tobit) on technology and read length; arrays closed by unique flanks on both sides are reported separately. |
| Fig 3. Family-wide comparison | Positions differ between *Vitis* and other Vitaceae genera. | Descriptive; positions placed on the ancestral karyotype of the Vitaceae study. |

**Expected results and how they will be read**

- Fig 1: if the same array positions are found in all complete haplotypes of a species, positions are reported as conserved; a locus missing from some haplotypes is reported as a candidate presence/absence polymorphism only when both flanks are assembled.
- Fig 2: a positive technology effect on assembled length (censored model) would show that assembled length is a lower bound and that copy number must come from reads; a null effect allows cautious use of assembled lengths.
- Fig 3: if *Vitis* and other Vitaceae genera differ in array number or position on the ancestral karyotype, the difference is described, not dated.
- A read-depth copy-number table (Step 6) is a secondary output and is reported with its error from technical replicates.

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

**How each dataset is used**

| Module | Role in this project |
|---|---|
| DS01 | PN_T2T coordinates; seed sequences for the 45S and 5S units |
| DS02, DS03 | Near-complete *Vitis* haplotypes; long reads, where public, for read-based copy number |
| DS05, DS08 | Other Vitaceae genera and *Muscadinia* for the family comparison |
| DS16 | Assembly list and assembly technology |
| DS17 | Angiosperm T2T comparison set with published NOR descriptions |

New public data: none needed. Which assemblies have matching public long reads is [待确认] per accession.

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

**Stepwise work plan with tools**

| Step | Work | Tools (paper) | Output |
|---|---|---|---|
| 1 | Reuse the assembly manifest and QC pass list of project 01 | AM01, AM05 | Shared manifest |
| 2 | Build 45S and 5S seed units from PN_T2T and check them against public rRNA models | BLASTN, nhmmer, barrnap | Seed set |
| 3 | Find arrays; record start, end, unit count and orientation | BLASTN or nhmmer (AM10), TRF ([Benson 1999](https://doi.org/10.1093/nar/27.2.573)) | Array table |
| 4 | Classify each array as closed (unique flank on both sides) or open; check flanks with Merqury k-mers | Merqury ([Rhie et al. 2020](https://doi.org/10.1186/s13059-020-02134-9)) | Closed/open flag |
| 5 | Map array positions to PN_T2T and to the Vitaceae ancestral karyotype | minimap2, SyRI (AM06) | Position matrix |
| 6 | Read-based copy number from long or short reads relative to single-copy genes; unit variants (morphs) where HiFi reads exist | mosdepth, ribotin | Copy-number table |
| 7 | Censored (Tobit) model of assembled length on technology and read length | R survival or censReg | Fig 2 statistics |

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

## Risks and how to handle them

Added 2026-11-26. Each row names a risk, the evidence behind it, and a concrete check or fallback. Sources cited here were read for this section and their DOIs were checked on Crossref; preprints are marked.

| Area | Risk | Check or mitigation |
|---|---|---|
| Data access and licence | Assemblies are listed as available, but the angiosperm comparison set (DS17) is an open query and long reads exist only for some accessions ([data/DOWNLOADS.md](../../data/DOWNLOADS.md)). INSDC data are free and open ([INSDC 2024](https://doi.org/10.1093/nar/gkae1058)). | Freeze the assembly list with versions; list, per accession, whether raw long reads exist before promising read-based copy numbers. |
| Sample size and power | Fully closed NORs may be found in only a few assemblies, so position conservation may rest on few points. | Report the number of closed, partly closed and absent arrays per chromosome before any comparison; if closed arrays are rare, treat positions as presence of a unit, not as array structure. |
| Copy number versus activity | In Hominidae, rDNA copy number and activity form an individual fingerprint, and whole arrays can be silent and methylated ([Potapova et al. 2025](https://doi.org/10.1016/j.xgen.2025.101031)). | Do not infer how many copies are active from DNA copy numbers; if public methylation data exist for an accession (DS18), report them only as a note. |
| rDNA outside NORs | In *Nicotiana benthamiana* rDNA was a major origin of centromeric satellites ([Chen et al. 2024](https://doi.org/10.1038/s41477-024-01849-y)), so rDNA-like hits can lie far from NORs. | Separate full 45S or 5S units from fragments; report fragments as their own class and cross-check them against the satellite calls of project 18. |
| Technology and source differences | Assemblers and read types differ in how much of an array they keep. | Model technology as a covariate; compare read-depth copy numbers only between libraries of the same platform. |
| Clones, synonyms and pedigree | Repeated assemblies of one genotype are not independent ([Noraz et al. 2026](https://doi.org/10.1038/s41467-026-70166-z) found clonal identity across centuries). | Collapse by genotype (project 08 table); use the repeats as a technical replicate of array recovery. |
| Annotation and method failure | Cytogenetic and assembly maps of tandem repeats can disagree; a T2T re-mapping in wheat resolved several such cases ([Garrido-Ramos et al. 2026](https://doi.org/10.1007/s11103-026-01745-3)). | Compare assembled NOR positions with published FISH counts where they exist; a mismatch is reported, not silently resolved. |
| Computing cost | Read-depth copy number needs alignment of raw reads, the costly step. | Use a k-mer or subsampled alignment for copy number and time one accession first. |
| Alternative methods and sensitivity | Copy number from depth depends on the single-copy genes used for normalisation. | Repeat with two sets of single-copy genes and report the spread. |

**Recent and competing work (search of 2024 to 2026 literature on 2026-11-26)**

- The search returned no grape-specific rDNA array study for 2024 to 2026; this is not proof of absence. In other plants, T2T papers treat rDNA as a side result, for example as a source of centromeric satellites ([Chen et al. 2024](https://doi.org/10.1038/s41477-024-01849-y)), so a grape catalogue is a descriptive extension rather than a first.
- New Vitaceae assemblies ([Wang et al. 2026](https://doi.org/10.64898/2026.04.20.719760), preprint) add genera for the family comparison.

**What would end the idea, and the fallback.** If almost no assembly closes a NOR and long reads are missing for most, the array catalogue is not possible. The fallback is the joint repeat-array paper with project 01 that reports only presence and position of units.

**Journal-level realism.** A specialty plant cytogenetics or genomics journal. Broader venues published NOR assembly when it was a first for a model species, which this project is not.

## Rough estimates

- Compute: small [draft]
- Effort: 3–6 weeks for one person [draft]
- Target: cytogenetics or genome journal [draft]

## Suggested journal level (suggestion only)

**Specialty journal (plant cytogenetics or plant genomics).** The rDNA database and inheritance papers read here appeared in *The Plant Journal* and *G3*, and NOR assembly papers in *Nature Communications* and *Science Advances*. Those broader papers assembled NORs for the first time in a model species; a grape catalogue of assembled arrays is a descriptive extension and fits a specialty venue, or a joint repeat-array paper with project 01 (A2). This is a suggestion, not a decision; impact factors are not used.

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
- Benson 1999. Tandem repeats finder: a program to analyze DNA sequences. *Nucleic Acids Research*. [doi:10.1093/nar/27.2.573](https://doi.org/10.1093/nar/27.2.573)
- Chen et al. 2023. A complete telomere-to-telomere assembly of the maize genome. *Nature Genetics*. [doi:10.1038/s41588-023-01419-6](https://doi.org/10.1038/s41588-023-01419-6)
- Copenhaver et al. 1996. RFLP and physical mapping with an rDNA‐specific endonuclease reveals that nucleolus organizer regions of Arabidopsis thaliana adjoin the telomeres on chromosomes 2 and 4. *The Plant Journal*. [doi:10.1046/j.1365-313x.1996.09020259.x](https://doi.org/10.1046/j.1365-313x.1996.09020259.x)
- Dvořáčková et al. 2015. Chromatin dynamics of plant telomeres and ribosomal genes. *The Plant Journal*. [doi:10.1111/tpj.12822](https://doi.org/10.1111/tpj.12822)
- Fultz et al. 2023. Sequence and epigenetic landscapes of active and silent nucleolus organizer regions in Arabidopsis. *Science Advances*. [doi:10.1126/sciadv.adj4509](https://doi.org/10.1126/sciadv.adj4509)
- Garcia et al. 2017. Cytogenetic features of rRNA genes across land plants: analysis of the Plant rDNA database. *The Plant Journal*. [doi:10.1111/tpj.13442](https://doi.org/10.1111/tpj.13442)
- Rabanal et al. 2017. Unstable Inheritance of 45S rRNA Genes in Arabidopsis thaliana. *G3 Genes|Genomes|Genetics*. [doi:10.1534/g3.117.040204](https://doi.org/10.1534/g3.117.040204)
- Rautiainen 2024. Ribotin: automated assembly and phasing of rDNA morphs. *Bioinformatics*. [doi:10.1093/bioinformatics/btae124](https://doi.org/10.1093/bioinformatics/btae124)
- Rhie et al. 2020. Merqury: reference-free quality, completeness, and phasing assessment for genome assemblies. *Genome Biology*. [doi:10.1186/s13059-020-02134-9](https://doi.org/10.1186/s13059-020-02134-9)
- Sims et al. 2021. Sequencing of the Arabidopsis NOR2 reveals its distinct organization and tissue-specific rRNA ribosomal variants. *Nature Communications*. [doi:10.1038/s41467-020-20728-6](https://doi.org/10.1038/s41467-020-20728-6)
- Wang et al. 2026. Chromosome-level phylogenomics and genome evolution of the grape family. *Nature Plants*. [doi:10.1038/s41477-026-02442-1](https://doi.org/10.1038/s41477-026-02442-1)
- INSDC 2024. The international nucleotide sequence database collaboration (INSDC): enhancing global participation. *Nucleic Acids Research*. [doi:10.1093/nar/gkae1058](https://doi.org/10.1093/nar/gkae1058)
- Potapova et al. 2025. Chromosome-specific epigenetic control and transmission of ribosomal DNA arrays in Hominidae genomes. *Cell Genomics*. [doi:10.1016/j.xgen.2025.101031](https://doi.org/10.1016/j.xgen.2025.101031)
- Chen et al. 2024. The complete genome assembly of Nicotiana benthamiana reveals the genetic and epigenetic landscape of centromeres. *Nature Plants*. [doi:10.1038/s41477-024-01849-y](https://doi.org/10.1038/s41477-024-01849-y)
- Noraz et al. 2026. Ancient DNA reveals 4000 years of grapevine diversity, viticulture and clonal propagation in France. *Nature Communications*. [doi:10.1038/s41467-026-70166-z](https://doi.org/10.1038/s41467-026-70166-z)
- Garrido-Ramos et al. 2026. Detailed re-analysis of satellitome mapping facilitated by the telomere-to-telomere (T2T) assembly of bread wheat genome. *Plant Molecular Biology*. [doi:10.1007/s11103-026-01745-3](https://doi.org/10.1007/s11103-026-01745-3)
- Wang et al. 2026. Origin and evolution of grapevine genomes. *bioRxiv* (preprint). [doi:10.64898/2026.04.20.719760](https://doi.org/10.64898/2026.04.20.719760)
