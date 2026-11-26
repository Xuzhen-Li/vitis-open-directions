# 09. Graph genotyping of the berry colour locus

中文：果皮颜色位点的图基因组分型

Rank 9 of 22 (score F 3 + N 1 + E 3 = 7; see docs/RANKING.md) · Tier: Quick (E = 3, effort range ending at 6 weeks or less) · Origin: new · Status: draft v0.3.2, 2026-11-14

## Gap

The colour locus and its somatic sports are well described. Genotyping its structural haplotypes from short reads through a graph, across public panels, was not found [待确认].

**Existing work**

- [Kobayashi et al. 2004](https://doi.org/10.1126/science.1095011): retrotransposon-induced mutations at the colour locus.
- [Pelsy et al. 2015](https://doi.org/10.1371/journal.pgen.1005081): chromosome replacement and deletion in colour sports.
- [Carbonell-Bejerano et al. 2017](https://doi.org/10.1104/pp.17.00715): unbalanced rearrangements in colour loss.
- [Reynard et al. 2025](https://doi.org/10.1093/hr/uhaf069): a divergent haplotype with a large deletion at the colour locus.

**How this project differs**

Builds a locus graph from all near-complete haplotypes and genotypes structural haplotypes in public panels.

**Background survey (literature read for this plan)**

Berry skin colour in grape is controlled mainly by one locus on chromosome 2 with tandem MYB regulators. A retrotransposon (Gret1) inserted in the VvMybA1 promoter silences it in white cultivars ([Kobayashi et al. 2004](https://doi.org/10.1126/science.1095011)), and white grapes needed mutations in both of two adjacent genes, VvMYBA1 and VvMYBA2 ([Walker et al. 2007](https://doi.org/10.1111/j.1365-313X.2006.02997.x)). Allelic variation at VvmybA1 is associated with colour in wine cultivars ([This et al. 2007](https://doi.org/10.1007/s00122-006-0472-2)); genomic and genetic analysis of the Myb genes refined the haplotypes ([Azuma et al. 2008](https://doi.org/10.1007/s00122-008-0840-1)); and QTL plus association mapping explained part of quantitative anthocyanin variation ([Fournier-Level et al. 2009](https://doi.org/10.1534/genetics.109.103929)). A recent study showed that the VvMybA1_SUB allele lies on an ancient divergent haplotype with functional and non-functional subhaplotypes, one with a large deletion causing white skin ([Reynard et al. 2025](https://doi.org/10.1093/hr/uhaf069)).

Colour sports arise by somatic structural change: 33 Pinot clones showed chromosome replacement and deletion in the L2 layer ([Pelsy et al. 2015](https://doi.org/10.1371/journal.pgen.1005081)), and Tempranillo Blanco carries a catastrophic unbalanced rearrangement with a hemizygous deletion ([Carbonell-Bejerano et al. 2017](https://doi.org/10.1104/pp.17.00715)). Graph genomes now allow known structural variants to be genotyped from short reads: vg Giraffe genotyped known SVs in 5,202 human genomes ([Sirén et al. 2021](https://doi.org/10.1126/science.abg8871)), and PGGB builds unbiased pangenome graphs from assemblies ([Garrison et al. 2024](https://doi.org/10.1038/s41592-024-02430-3)). The colour locus is resolved in near-complete haplotypes ([Liu et al. 2024](https://doi.org/10.1038/s41588-024-01967-5)).

**Specific gap.** The colour haplotypes were defined with markers, PCR and single assemblies. No study was found that builds a graph of the locus from all near-complete haplotypes and genotypes the structural haplotypes from short reads across public panels with a check against recorded colour [待确认].

## Question

Can graph genotyping recover colour-locus haplotypes from short reads well enough to predict berry colour?

## Hypotheses, planned figures and criteria

No results are given here. Each row says what would count as support; the exact thresholds go into the preregistration.

| Figure or table | Hypothesis or purpose | Criterion |
|---|---|---|
| Fig 1. Locus graph | Not a hypothesis: graph of all haplotypes. | Built from near-complete haplotypes only. |
| Fig 2. Genotype vs recorded berry colour | Graph genotypes at VvMybA1 and VvMybA2 together predict recorded berry colour. | Accuracy per colour class with Wilson 95% intervals (classes are unbalanced); colour sports are listed separately and excluded from accuracy calculations. |
| Fig 3. Haplotype frequencies by group | Descriptive. | Counts by panel and group. |

**Expected results and how they will be read**

- Fig 1 shows every structural haplotype of the locus (Gret1 insertion, deletions, divergent haplotype F) as graph paths.
- Fig 2: if graph genotypes at VvMybA1 and VvMybA2 predict recorded colour with high accuracy (preregistered threshold), the graph is a usable genotyping tool for public data; misclassified samples are listed and checked for label error (project 08) or somatic sports before any biological reading.
- Fig 3 gives haplotype frequencies by wild, table and wine groups; it is descriptive.

## Preregistration

Before any data are analysed, fill in [`docs/PREREGISTRATION.md`](../../../../templates/PREREGISTRATION.md) for this project: hypotheses, primary outcome, sample inclusion rules, thresholds, stop rules and what will be reported if a hypothesis fails. Commit it with a date. Criteria from any earlier attempt are reference only and are not carried over.

## Data

| Module | Dataset |
|---|---|
| [DS02](../../data/DS02-grapepan-v1/) | Grapepan v1.0: T2T haplotypes, graphs and a 466-accession resequencing panel |
| [DS03](../../data/DS03-vitis-super-pangenome-72/) | Vitis super-pangenome: 72 haplotype-resolved accessions |
| [DS10](../../data/DS10-reseq-472-vitis/) | Resequencing of 472 Vitis accessions (and the 2017 domestication panel) |
| [DS12](../../data/DS12-reseq-204-magris2021/) | Resequencing of 204 V. vinifera accessions (Magris et al. 2021) |
| [DS01](../../data/DS01-pn40024-references/) | PN40024 references: PN_T2T (v5), PN40024.v4 and 12X |

**How each dataset is used**

| Module | Role in this project |
|---|---|
| DS01, DS02, DS03 | Near-complete haplotypes from which the locus graph is built |
| DS10, DS12 | Short-read panels to genotype |

New public data: none needed. Berry colour records come from VIVC and the panel papers [待确认: coverage per panel].

## Analysis steps

Shared modules, in order:

1. [AM01 · Download and verify](../../analyses/AM01-download-and-verify/)
2. [AM07 · Pangenome graph build and genotyping](../../analyses/AM07-graph-build-and-genotype/)
3. [AM03 · Short-read mapping and small-variant calling](../../analyses/AM03-short-read-variants/)

Project-specific steps:

- Extract the locus from each haplotype; build a PGGB graph (AM07).
- Genotype panel samples with vg giraffe and vg call.
- Compare with VIVC colour records.

**Stepwise work plan with tools**

| Step | Work | Tools (paper) | Output |
|---|---|---|---|
| 1 | Extract the colour locus (with flanks) from every near-complete haplotype | minimap2, samtools | Locus FASTA set |
| 2 | Annotate VvMybA1, VvMybA2, Gret1 and known deletions on each haplotype | miniprot, BLASTN | Haplotype labels |
| 3 | Build the locus graph | PGGB (AM07) | Locus graph |
| 4 | Test genotyping on samples with assemblies by downsampling their reads | vg giraffe, vg call | Accuracy table |
| 5 | Genotype the public panels (one sample per identity group from project 08) | vg giraffe, vg call (AM07) | Panel genotypes |
| 6 | Compare with VIVC colour; logistic model of colour on the two genes | R | Fig 2 |

## Paper design and split

| Paper | Working title | Type | Figures |
|---|---|---|---|
| J1 | Graph genotyping of the grape colour locus | short methods note | Fig 1–3 |

Each paper: introduction from the gap above; one results section per figure; methods with tool versions from the modules; data availability listing every accession used and the derived tables.

## Risks and novelty check

- Risk: Colour records may be inconsistent.
- Risk: Colour sports are periclinal chimeras: a change in one cell layer appears in leaf DNA as a lower VAF rather than an absence; which layer determines berry colour is checked against the colour-sport literature [待确认].
- Novelty: checked against the existing work above (Crossref-verified DOIs). Repeat the search before writing; anything marked [待确认] is not yet verified.

## Risks and how to handle them

Added 2026-11-26. Each row names a risk, the evidence behind it, and a concrete check or fallback. Sources cited here were read for this section and their DOIs were checked on Crossref; preprints are marked.

| Area | Risk | Check or mitigation |
|---|---|---|
| Data access and licence | Graph, assemblies and resequencing panels are listed as available ([data/DOWNLOADS.md](../../data/DOWNLOADS.md)); colour records come from VIVC and papers. | Freeze the panel and the date of the colour record export. |
| Haplotypes missing from the graph | The berry colour locus carries an ancient divergent haplotype F with two functional subhaplotypes and one with a large deletion that gives white skin ([Reynard et al. 2025](https://doi.org/10.1093/hr/uhaf069)). If no graph assembly carries a haplotype, short reads from it cannot be typed correctly. | List which assemblies carry each known haplotype before building; add an assembly carrying haplotype F or mark that class as untyped. |
| Colour sports and chimeras | In a study of 33 Pinot clones, at least six L2-layer haplotypes accounted for colour loss, four of them from replacement of 31 kb to 4.4 Mb sections of the coloured haplotype ([Pelsy et al. 2015](https://doi.org/10.1371/journal.pgen.1005081)); roots come from L2 only, so comparing root and leaf DNA detects periclinal chimeras ([Sichel et al. 2023](https://doi.org/10.1186/s12864-023-09453-8)). | Exclude known colour sports from the prediction test, analyse them separately, and use root data where public. |
| Graph construction | Graph builders differ in completeness and in how faithfully they keep SVs ([Kopalli et al. 2025](https://doi.org/10.1093/gigascience/giaf121)). | Build the locus graph with two pipelines and compare the paths of known haplotypes. |
| Complex SV genotyping | Large complex SVs can be genotyped from a 30-genome graph in chicken ([Rice et al. 2023](https://doi.org/10.1186/s12915-023-01758-0)), but repeats at the locus may reduce accuracy in grape. | Measure concordance against assemblies of the same accessions (truth set) before predicting colour. |
| Clones, synonyms and pedigree | Duplicate genotypes inflate prediction accuracy. | Collapse by genotype (project 08) and split train and test sets by genotype. |
| Sample size and power | Few white accessions carry rare haplotypes. | Report accuracy per haplotype class with counts. |
| Computing cost | Locus-only genotyping is small; whole-genome graph alignment is not. | Align only reads that map near the locus, after a check that this does not lose reads from divergent haplotypes. |

**Recent and competing work (search of 2024 to 2026 literature on 2026-11-26)**

- The most recent locus study already explains a white-skin case by a divergent haplotype ([Reynard et al. 2025](https://doi.org/10.1093/hr/uhaf069)). The remaining contribution is typing all known haplotypes from short reads at panel scale.

**What would end the idea, and the fallback.** If graph genotypes at the locus agree poorly with assembly truth, prediction from short reads is not reliable. The fallback is k-mer typing of known haplotype markers, or a descriptive haplotype catalogue from assemblies only.

**Journal-level realism.** Specialty plant genetics or horticulture journal, since the locus is already explained.

## Reference study in another species

Added 2026-11-26. Published studies that already did this kind of work in another species, to plan the grape version against. Every DOI was checked on Crossref. Figures are described, not copied; a figure redrawn for a grape paper would be marked "Redrawn after" its source. The last bullet for each study lists what a grape results section would need; it is a planning suggestion, not a finding of that study.

### Zhou et al. 2022

- **Paper:** [Zhou et al. 2022](https://doi.org/10.1038/s41586-022-04808-9), *Nature*.
- **Species:** Tomato and close relatives.
- **What was done:** A tomato graph pangenome was built; SVs were genotyped with short reads in 332 accessions; the contribution of SVs to heritability was estimated, and the graph was used for marker-assisted and genomic selection.
- **Figures:** Fig. 1 tomato genomes and the graph pangenome; Fig. 2 contribution of variant types to heritability; Fig. 3 allelic and locus heterogeneity; Fig. 4 the graph in marker-assisted and genomic selection; Extended Data Fig. 1 to 8 (framework, assembly features, graph versus linear mapping, heritability estimates, a gene structure example, an annotation error example, GWAS heterogeneity, a co-expression network).
- **What a grape results section would need:** structural haplotypes of the colour locus defined on the graph; graph versus linear mapping (as in Extended Data Fig. 3); haplotype frequencies in public panels; association with berry colour.

### You et al. 2026

- **Paper:** [You et al. 2026](https://doi.org/10.1038/s41467-026-69764-8), *Nature Communications* (PMC13039718). Licence CC BY 4.0: figures may be reused with credit; none are copied here.
- **Species:** eggplant, 226 accessions and a pangenome of 17 assemblies (11 new, 6 published).
- **What was done:** association scans on the pangenome found a 12.4 Mb inversion on chromosome 10, at 50.44% frequency, strongly associated with fruit colour, likely through hitchhiking with *SmMYB1*; variants linked to bacterial wilt resistance were also found.
- **Figures:** Fig. 1 geography and diversity; Fig. 2 pangenome; Fig. 3 structural variants per assembly; Fig. 4 association of the inversion with fruit colour; Fig. 5 diversity reduction and extended haplotype across the inversion; Fig. 6 wilt-resistance loci.
- **What its results section needed:** structural variants called from assemblies, an association between a structural haplotype and colour, and haplotype structure around the candidate MYB gene.
- **Grape version:** Fig. 4 and 5 equivalents for the berry colour locus: graph genotypes of the colour haplotypes across accessions, their association with recorded berry colour, and haplotype structure around the MYB genes, with long-read checks where a haplotype is missing from the graph (risk above).

### Q1-level bar

Target: a first-quartile (Q1) journal in plant science, genetics or evolution. Quartile lists change each year, so the journal is chosen from the current list at submission [to confirm]. To compete at that level, the grape paper needs: graph versus linear genotyping of the colour locus, with structural haplotypes confirmed in long-read assemblies and an association with berry colour in public panels. One locus alone fits a specialty journal; several trait loci tested the same way make a methods case at Q1 level.

## Rough estimates

- Compute: small [draft]
- Effort: 3–6 weeks for one person [draft]
- Target: plant genetics journal [draft]

## Suggested journal level (suggestion only)

**Specialty journal (plant genetics or horticulture).** Colour-locus papers read here span *Science* (the first molecular cause), *The Plant Journal*, *Theoretical and Applied Genetics*, *Genetics*, *PLOS Genetics*, *Plant Physiology* and *Horticulture Research*. A graph genotyping study of an already explained locus fits a specialty venue such as the last group. This is a suggestion, not a decision; impact factors are not used.

## Continue on HPC

Run each step as its own job, in this order. Every job writes `.DONE` or `.FAILED` and a log; the next step starts only after `.DONE`. Template and rules: [`docs/HPC_JOBS.md`](../../../../templates/HPC_JOBS.md).

| Order | Step | Main tools | Resources (rough) |
|---|---|---|---|
| 1 | [AM01](../../analyses/AM01-download-and-verify/) Download and verify | ncbi-datasets-cli, sra-tools, ENA FTP / Aspera | 1–4 CPU, 4 GB, network; array over files |
| 2 | [AM07](../../analyses/AM07-graph-build-and-genotype/) Pangenome graph build and genotyping | Minigraph-Cactus, PGGB, vg | 32–64 CPU, 256–512 GB for graph builds; 16 CPU, 64 GB per sample for giraffe |
| 3 | [AM03](../../analyses/AM03-short-read-variants/) Short-read mapping and small-variant calling | bwa-mem2, samtools, DeepVariant | 16 CPU, 64 GB, 6–24 h per sample (DeepVariant); joint step 32 CPU, 128 GB |

Public inputs: [DS02](../../data/DS02-grapepan-v1/), [DS03](../../data/DS03-vitis-super-pangenome-72/), [DS10](../../data/DS10-reseq-472-vitis/), [DS12](../../data/DS12-reseq-204-magris2021/), [DS01](../../data/DS01-pn40024-references/).

## References

- Kobayashi et al. 2004. Retrotransposon-Induced Mutations in Grape Skin Color. *Science*. [doi:10.1126/science.1095011](https://doi.org/10.1126/science.1095011)
- Pelsy et al. 2015. Chromosome Replacement and Deletion Lead to Clonal Polymorphism of Berry Color in Grapevine. *PLOS Genetics*. [doi:10.1371/journal.pgen.1005081](https://doi.org/10.1371/journal.pgen.1005081)
- Carbonell-Bejerano et al. 2017. Catastrophic Unbalanced Genome Rearrangements Cause Somatic Loss of Berry Color in Grapevine. *Plant Physiology*. [doi:10.1104/pp.17.00715](https://doi.org/10.1104/pp.17.00715)
- Reynard et al. 2025. A divergent haplotype with a large deletion at the berry color locus causes a white-skinned phenotype in grapevine. *Horticulture Research*. [doi:10.1093/hr/uhaf069](https://doi.org/10.1093/hr/uhaf069)
- Azuma et al. 2008. Genomic and genetic analysis of Myb-related genes that regulate anthocyanin biosynthesis in grape berry skin. *Theoretical and Applied Genetics*. [doi:10.1007/s00122-008-0840-1](https://doi.org/10.1007/s00122-008-0840-1)
- Fournier-Level et al. 2009. Quantitative Genetic Bases of Anthocyanin Variation in Grape (Vitis vinifera L. ssp. sativa) Berry: A Quantitative Trait Locus to Quantitative Trait Nucleotide Integrated Study. *Genetics*. [doi:10.1534/genetics.109.103929](https://doi.org/10.1534/genetics.109.103929)
- Garrison et al. 2024. Building pangenome graphs. *Nature Methods*. [doi:10.1038/s41592-024-02430-3](https://doi.org/10.1038/s41592-024-02430-3)
- Liu et al. 2024. Grapevine pangenome facilitates trait genetics and genomic breeding. *Nature Genetics*. [doi:10.1038/s41588-024-01967-5](https://doi.org/10.1038/s41588-024-01967-5)
- Sirén et al. 2021. Pangenomics enables genotyping of known structural variants in 5202 diverse genomes. *Science*. [doi:10.1126/science.abg8871](https://doi.org/10.1126/science.abg8871)
- This et al. 2007. Wine grape (Vitis vinifera L.) color associates with allelic variation in the domestication gene VvmybA1. *Theoretical and Applied Genetics*. [doi:10.1007/s00122-006-0472-2](https://doi.org/10.1007/s00122-006-0472-2)
- Walker et al. 2007. White grapes arose through the mutation of two similar and adjacent regulatory genes. *The Plant Journal*. [doi:10.1111/j.1365-313x.2006.02997.x](https://doi.org/10.1111/j.1365-313x.2006.02997.x)
- Sichel et al. 2023. Chimeras in Merlot grapevine revealed by phased assembly. *BMC Genomics*. [doi:10.1186/s12864-023-09453-8](https://doi.org/10.1186/s12864-023-09453-8)
- Kopalli et al. 2025. Toward a standardized framework for pangenome graph evaluation: assessing crop plant pangenome variation graph construction from multiple assemblies. *GigaScience*. [doi:10.1093/gigascience/giaf121](https://doi.org/10.1093/gigascience/giaf121)
- Rice et al. 2023. A pangenome graph reference of 30 chicken genomes allows genotyping of large and complex structural variants. *BMC Biology*. [doi:10.1186/s12915-023-01758-0](https://doi.org/10.1186/s12915-023-01758-0)
- Zhou et al. 2022. Graph pangenome captures missing heritability and empowers tomato breeding. *Nature*. [doi:10.1038/s41586-022-04808-9](https://doi.org/10.1038/s41586-022-04808-9)
- You et al. 2026. Sub-pangenome analysis reveals structural variants associated with fruit color and bacterial wilt resistance in eggplant. *Nature Communications*. [doi:10.1038/s41467-026-69764-8](https://doi.org/10.1038/s41467-026-69764-8)
