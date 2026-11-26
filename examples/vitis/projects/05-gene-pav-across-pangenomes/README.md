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

**Background survey (literature read for this plan)**

Pangenomes moved crop genomics from one reference to many ([Bayer et al. 2020](https://doi.org/10.1038/s41477-020-0733-0)). Early crop pangenomes reported large dispensable gene sets, for example in *Brassica oleracea* ([Golicz et al. 2016](https://doi.org/10.1038/ncomms13390)), tomato, where a pan-genome found new genes and a rare flavour allele ([Gao et al. 2019](https://doi.org/10.1038/s41588-019-0410-2)), and 33 rice accessions ([Qin et al. 2021](https://doi.org/10.1016/j.cell.2021.04.046)). Each study used its own annotation pipeline, so gene absence can be an annotation artefact rather than missing sequence; projection tools such as Liftoff ([Shumate and Salzberg 2021](https://doi.org/10.1093/bioinformatics/btaa1016)) and protein-to-genome alignment with miniprot ([Li 2023](https://doi.org/10.1093/bioinformatics/btad014)) allow every haplotype to be checked against the same gene set.

Grape now has several pangenomes. Hemizygous genes were first shown at scale in Chardonnay within a study of structural variants ([Zhou et al. 2019](https://doi.org/10.1038/s41477-019-0507-8)). Grapepan reported gene presence/absence among T2T haplotypes ([Liu et al. 2024](https://doi.org/10.1038/s41588-024-01967-5)); the *Vitis* super-pangenome covered wild species ([Guo et al. 2025](https://doi.org/10.1038/s41588-025-02111-7)); a North American super-pangenome covered wild species of that continent ([Cochetel et al. 2023](https://doi.org/10.1186/s13059-023-03133-2)); population comparative genomics described gene gain and loss during domestication ([Long et al. 2024](https://doi.org/10.1093/plphys/kiae039)); and a cultivated pangenome of 15 varieties (nine newly assembled) confirmed high collinearity and a large dispensable share ([Pierre et al. 2026](https://doi.org/10.1093/g3journal/jkag168)) [待确认: 15 in the abstract, 16 in DS07].

**Specific gap.** These resources were annotated separately. No study was found that projects one gene set onto all public grape haplotypes, confirms each absence by sequence search and by read depth, and reports how much published presence/absence survives [待确认].

## Question

How much reported gene PAV in grape is reproduced when all haplotypes are processed the same way, and which gene classes are truly variable?

## Scope update (2026-11-26)

Added 2026-11-26. This section narrows or reframes the plan above; where the two differ, this section applies. Earlier text is kept unchanged.

**What grape adds beyond existing work.** Annotation-driven inflation of gene PAV is already shown in general ([Brůna et al. 2026](https://doi.org/10.1093/nargab/lqag011)). Grape adds a measured split, in a heterozygous clonal crop, between gene PAV that holds at the sequence level and gene PAV that disappears when every haplotype is annotated the same way.

Target: a first-quartile (Q1) journal in plant science, genetics or evolution. Quartile lists change each year, so the journal is chosen from the current list at submission [to confirm]. The points below are what the paper needs to compete at that level.

- One annotation pipeline on all haplotypes, plus sequence-level confirmation of every absence on the graph (see the reference study below).
- The fraction of published grape PAV that is reproduced, with the reasons for each class of loss.
- Functional classes of true PAV, tested against a background matched for gene length and family size.
- A released corrected PAV table, and joint publication with project 06 as two parts of one paper (already suggested in the direction map).

**Fallback.** If most published PAV is reproduced, the paper reports that grape PAV is robust and gives the corrected table; this is preregistered as a valid outcome.

## Hypotheses, planned figures and criteria

No results are given here. Each row says what would count as support; the exact thresholds go into the preregistration.

| Figure or table | Hypothesis or purpose | Criterion |
|---|---|---|
| Fig 1. Concordance of PAV calls between original and uniform annotation | A measurable share of reported absences are annotation artefacts. | Each absence re-tested by sequence search and read depth; categories fixed in advance. |
| Fig 2. Confirmed absences by gene class | Confirmed absences are enriched in NLR, TPS and other clustered families. | Enrichment against length- and GC-matched background; BH FDR applied within the family of gene classes fixed in advance. |
| Fig 3. Pangenome growth curves before and after correction | Corrected curves saturate earlier. | Curves with bootstrap intervals; the resampling unit is the accession (both haplotypes of an accession together). |

**Expected results and how they will be read**

- Fig 1: the share of published absences not confirmed under the uniform pipeline is the main number; a high share means that pangenome gene counts should not be compared across studies, a low share means published sets are usable as they are.
- Fig 2: enrichment of confirmed absences in NLR, TPS and other clustered families would agree with tandem families being the main source of real presence/absence; no enrichment is reported as such.
- Fig 3: corrected growth curves are reported with the fitted saturation parameter and its interval; no claim of a closed pangenome is made from curves alone.

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
| [DS07](../../data/DS07-cultivated-16-pangenome/) | Cultivated grapevine pangenome (16 cultivars, Plastivigne) |

**How each dataset is used**

| Module | Role in this project |
|---|---|
| DS01 | PN_T2T gene set (RefSeq annotation) projected onto every haplotype |
| DS02 | Grapepan T2T haplotypes and their published presence/absence |
| DS03 | Super-pangenome haplotypes of cultivated and wild *Vitis* |
| DS04, DS06 | North American species and *V. amurensis* haplotypes |
| DS07 | Cultivated pangenome and its published dispensable set |

New public data: none needed. Short reads for depth checks exist only for some haplotypes [待确认 per accession].

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

**Stepwise work plan with tools**

| Step | Work | Tools (paper) | Output |
|---|---|---|---|
| 1 | Collect haplotypes, published annotations and published presence/absence tables | AM01 | Manifest |
| 2 | Assembly QC; drop haplotypes below the completeness cut-off | compleasm or BUSCO (AM05) | Pass list |
| 3 | Project PN_T2T genes with Liftoff; align proteins with miniprot | Liftoff, miniprot (AM09) | Uniform gene models per haplotype |
| 4 | Call presence, absence, partial and copy number per gene | AM09 rules | Presence/absence matrix |
| 5 | Confirm absences by sequence search in the whole haplotype and by short-read depth | BLASTN, mosdepth | Confirmed matrix |
| 6 | Compare with each published table; classify disagreements | R | Fig 1 |
| 7 | Enrichment by gene family and growth curves before and after correction | InterProScan, R | Fig 2, Fig 3 |

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

## Risks and how to handle them

Added 2026-11-26. Each row names a risk, the evidence behind it, and a concrete check or fallback. Sources cited here were read for this section and their DOIs were checked on Crossref; preprints are marked.

| Area | Risk | Check or mitigation |
|---|---|---|
| Data access and licence | Assemblies and annotations are listed as available; short reads for depth checks exist only for some haplotypes ([data/DOWNLOADS.md](../../data/DOWNLOADS.md)). | List per haplotype which evidence exists (assembly, annotation, short reads, RNA-seq) before choosing the PAV test set. |
| Annotation source differences | In cotton and soybean, PAV computed from public annotations mostly reflected differences in annotation methods, not sequence; one shared pipeline removed most of this, but identical sequences still received different gene models ([Brůna et al. 2026](https://doi.org/10.1093/nargab/lqag011)). | Re-annotate every haplotype with one pipeline before any PAV call; report PAV from public annotations and from the shared pipeline side by side. |
| Assembly errors | Comparing draft and finished assemblies, upwards of 40% of gene families had the wrong gene number in drafts, with both added and lost genes ([Denton et al. 2014](https://doi.org/10.1371/journal.pcbi.1003998)). | Mark collapsed and duplicated regions (read depth, k-mer QC) and exclude PAV calls inside them from the main estimate. |
| Reference bias and genome choice | Projection from PN_T2T under-calls presence in diverged wild haplotypes (see above). | Confirm absence by whole-genome alignment; syntenic pangenes from genome alignments help confirm PAV ([Contreras-Moreira et al. 2023](https://doi.org/10.1186/s13059-023-03071-z)). |
| Clones, synonyms and pedigree | Some cultivars are assembled more than once in different resources. | Use repeated assemblies of one genotype as a positive control: any PAV between them estimates pipeline noise. |
| Sample size and power | Gene-class enrichment needs enough variable genes per class. | Fix classes and minimum counts in the preregistration; merge small classes. |
| Computing cost | Re-annotating every haplotype with one pipeline is the largest cost. | Time two haplotypes first; use liftover plus gap-filling annotation if full re-annotation is too slow, and say so. |
| Alternative methods and sensitivity | PAV depends on identity and coverage cut-offs. | Report PAV at two cut-offs and with and without the excluded regions. |

**Recent and competing work (search of 2024 to 2026 literature on 2026-11-26)**

- The general point, that PAV taken from public annotations is inflated by annotation methods, is now published for cotton and soybean ([Brůna et al. 2026](https://doi.org/10.1093/nargab/lqag011)). This supports the project but removes the general claim; the grape-specific size of the effect remains open.
- A long-read study of 16 *Vitis* genomes reported only about 7% of gene families shared by all and about 8% specific to each accession ([Long et al. 2024](https://doi.org/10.1093/plphys/kiae039)); these numbers are the main target for re-testing under one pipeline.

**What would end the idea, and the fallback.** If the shared pipeline reproduces the published PAV levels, the artefact hypothesis fails; that is still a validation result worth a short paper. If a shared pipeline cannot be run on wild haplotypes (no transcript evidence), fall back to liftover-based PAV with alignment confirmation.

**Journal-level realism.** The cross-crop methods paper appeared in *NAR Genomics and Bioinformatics*. A grape re-analysis is now specialty to mid-field; mid-field needs a clear change in the number of truly variable genes.

## Reference study in another species

Added 2026-11-26. Published studies that already did this kind of work in another species, to plan the grape version against. Every DOI was checked on Crossref. Figures are described, not copied; a figure redrawn for a grape paper would be marked "Redrawn after" its source. The last bullet for each study lists what a grape results section would need; it is a planning suggestion, not a finding of that study.

### Hufford et al. 2021

- **Paper:** [Hufford et al. 2021](https://doi.org/10.1126/science.abg5289), *Science*.
- **Species:** Maize, 26 founder lines of the nested association mapping population.
- **What was done:** The 26 genomes were assembled and annotated with one pipeline; a pan-gene set was built, and fractionation, structural variants and variation in unmethylated regions were analysed.
- **Figures:** Fig. 1 pan-genome of gene space, with pan-genes split by annotation method and by phylogenetic age; Fig. 2 tempo of fractionation; Fig. 3 structural variants among the founders; Fig. 4 variation in unmethylated regions (full text read from the author manuscript in PubMed Central).
- **What a grape results section would need:** a PAV matrix after uniform annotation; PAV split by annotation evidence or method, to separate artefacts; core and dispensable curves; the relation of SVs to PAV.

### Lian et al. 2024

- **Paper:** [Lian et al. 2024](https://doi.org/10.1038/s41588-024-01715-9), *Nature Genetics*.
- **Species:** *Arabidopsis thaliana*, 69 accessions.
- **What was done:** Chromosome-level assemblies of 69 accessions showed a nearly fixed karyotype across the species range; a gene-level pan-genome, structural variants and population analyses followed.
- **Figures:** Fig. 1 geography and population analysis of 72 accessions; Fig. 2 assembly and annotation evaluation; Fig. 3 whole-genome alignment of the 69 assemblies; Fig. 4 synteny landscape; Fig. 5 pan-genome (core, softcore, dispensable, private); Extended Data Fig. 1 to 6 (tree, assembled and estimated genome and centromere sizes, SV length and frequency, long-read check of an inversion breakpoint, variants along chromosomes, presence and absence of pan-gene families).
- **What a grape results section would need:** core and dispensable composition under one pipeline; assembly completeness checks and filters; PAV in relation to SVs and population structure.

### MacNish et al. 2025

- **Paper:** [MacNish et al. 2025](https://doi.org/10.1002/tpg2.20535), *The Plant Genome* (PMC11730171). Licence CC BY-NC-ND 4.0: figures are not copied here; any redraw is marked "Redrawn after MacNish et al. 2025".
- **Species:** *Brassica rapa*, *B. oleracea* and *B. napus* in one multi-species graph pangenome.
- **What was done:** a graph pangenome was built and presence-absence variation (PAV) was read both as graph segments and as genes, with a browser (Panache) for exploration.
- **Figures:** Fig. 1 size distribution of graph segments; Fig. 2 sequence of each assembly that aligns to the graph; Fig. 3 unique segments per assembly; Fig. 4 number of genes shared by a given number of individuals, per species and for all three; Fig. 5 and 6 segment and gene length shared among species; Fig. 7 and 8 browser views of species-specific segments.
- **What its results section needed:** PAV at two levels (sequence segments and genes), per-assembly unique sequence, sharing curves, and a browsable resource.
- **Grape version and what grape adds:** the same two-level view for all grape haplotypes, used as a test: a gene called absent from an annotation while its sequence is present in the graph is counted as an annotation artefact. That split, measured in a heterozygous clonal crop, is the result the general studies cited above do not give for grape.

### Q1-level bar

Target: a first-quartile (Q1) journal in plant science, genetics or evolution. Quartile lists change each year, so the journal is chosen from the current list at submission [to confirm]. To compete at that level, the grape paper needs the points listed in the Scope update section above, which applies to this project.

## Rough estimates

- Compute: medium [draft]
- Effort: 2–3 months for one person [draft]
- Target: genome journal [draft]

## Suggested journal level (suggestion only)

**Mid-field journal (genome biology or plant genomics).** The grape pangenome resources read here appeared in broad or high-level venues (*Nature Genetics*, *Nature Plants*), and follow-up comparative studies in *Plant Physiology*, *Genome Biology* and *G3*. A re-analysis that quantifies annotation artefacts across resources is a methods-and-resource contribution at the mid-field level. This is a suggestion, not a decision; impact factors are not used.

## Continue on HPC

Run each step as its own job, in this order. Every job writes `.DONE` or `.FAILED` and a log; the next step starts only after `.DONE`. Template and rules: [`docs/HPC_JOBS.md`](../../../../templates/HPC_JOBS.md).

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
- Bayer et al. 2020. Plant pan-genomes are the new reference. *Nature Plants*. [doi:10.1038/s41477-020-0733-0](https://doi.org/10.1038/s41477-020-0733-0)
- Cochetel et al. 2023. A super-pangenome of the North American wild grape species. *Genome Biology*. [doi:10.1186/s13059-023-03133-2](https://doi.org/10.1186/s13059-023-03133-2)
- Gao et al. 2019. The tomato pan-genome uncovers new genes and a rare allele regulating fruit flavor. *Nature Genetics*. [doi:10.1038/s41588-019-0410-2](https://doi.org/10.1038/s41588-019-0410-2)
- Golicz et al. 2016. The pangenome of an agronomically important crop plant Brassica oleracea. *Nature Communications*. [doi:10.1038/ncomms13390](https://doi.org/10.1038/ncomms13390)
- Li 2023. Protein-to-genome alignment with miniprot. *Bioinformatics*. [doi:10.1093/bioinformatics/btad014](https://doi.org/10.1093/bioinformatics/btad014)
- Qin et al. 2021. Pan-genome analysis of 33 genetically diverse rice accessions reveals hidden genomic variations. *Cell*. [doi:10.1016/j.cell.2021.04.046](https://doi.org/10.1016/j.cell.2021.04.046)
- Shumate et al. 2021. Liftoff: accurate mapping of gene annotations. *Bioinformatics*. [doi:10.1093/bioinformatics/btaa1016](https://doi.org/10.1093/bioinformatics/btaa1016)
- Brůna et al. 2026. Evolutionary and methodological considerations when interpreting gene presence–absence variation in pangenomes. *NAR Genomics and Bioinformatics*. [doi:10.1093/nargab/lqag011](https://doi.org/10.1093/nargab/lqag011)
- Denton et al. 2014. Extensive Error in the Number of Genes Inferred from Draft Genome Assemblies. *PLoS Computational Biology*. [doi:10.1371/journal.pcbi.1003998](https://doi.org/10.1371/journal.pcbi.1003998)
- Contreras-Moreira et al. 2023. GET_PANGENES: calling pangenes from plant genome alignments confirms presence-absence variation. *Genome Biology*. [doi:10.1186/s13059-023-03071-z](https://doi.org/10.1186/s13059-023-03071-z)
- Hufford et al. 2021. De novo assembly, annotation, and comparative analysis of 26 diverse maize genomes. *Science*. [doi:10.1126/science.abg5289](https://doi.org/10.1126/science.abg5289)
- Lian et al. 2024. A pan-genome of 69 Arabidopsis thaliana accessions reveals a conserved genome structure throughout the global species range. *Nature Genetics*. [doi:10.1038/s41588-024-01715-9](https://doi.org/10.1038/s41588-024-01715-9)
- MacNish et al. 2025. Brassica Panache: A multi‐species graph pangenome representing presence absence variation across forty‐one Brassica genomes. *The Plant Genome*. [doi:10.1002/tpg2.20535](https://doi.org/10.1002/tpg2.20535)
