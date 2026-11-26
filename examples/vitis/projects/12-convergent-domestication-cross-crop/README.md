# 12. Convergent domestication: grape compared with other crops in one pipeline

中文：葡萄与其他作物统一流程的趋同驯化比较

Rank 12 of 22 (score F 2 + N 3 + E 1 = 6; see docs/RANKING.md) · Tier: Large (E = 1, more than 4 months or a high-risk step) · Origin: new · Status: draft v0.3.2, 2026-11-14

## Gap

Domestication scans exist for many crops, but grape has not been compared with other fruit or field crops using one pipeline and a gene-matched null [待确认].

**Existing work**

- [Chen et al. 2022](https://doi.org/10.1126/science.abg7985): convergent selection of one gene in maize and rice.
- [Yu et al. 2018](https://doi.org/10.1038/s41467-018-07744-3): peach domestication from resequencing.
- [Duan et al. 2017](https://doi.org/10.1038/s41467-017-00336-7): apple domestication from resequencing.
- [Jaillon et al. 2007](https://doi.org/10.1038/nature06148): grape genome and the ancestral triplication shared by core eudicots.

**How this project differs**

Same scan for every crop, orthology that handles one-to-many cases, and a null built from matched gene bins.

**Background survey (literature read for this plan)**

Crop domestication has been described as repeated evolution under similar human selection ([Meyer and Purugganan 2013](https://doi.org/10.1038/nrg3605); [Purugganan 2019](https://doi.org/10.1016/j.cub.2019.05.053)), and convergent phenotypes have known molecular causes in several crops ([Lenser and Theißen 2013](https://doi.org/10.1016/j.tplants.2013.08.007)). Genome-wide convergence has been tested directly: maize KRN2 and its rice orthologue experienced convergent selection, and scans identified 490 pairs of orthologous genes under convergent selection in the two cereals ([Chen et al. 2022](https://doi.org/10.1126/science.abg7985)); in two distantly related conifers, 47 genes showed convergent local adaptation to climate ([Yeaman et al. 2016](https://doi.org/10.1126/science.aaf7812)). Demography (bottlenecks, gene flow) shapes crop genomes and can mimic or hide selection signals, so scans must be compared under a matched null ([Gaut et al. 2018](https://doi.org/10.1038/s41477-018-0210-1)).

Perennial fruit crops are domesticated differently from annuals: long generation times, clonal propagation and frequent gene flow with wild relatives ([Miller and Gross 2011](https://doi.org/10.3732/ajb.1000522); [McKey et al. 2010](https://doi.org/10.1111/j.1469-8137.2010.03210.x)). Resequencing histories exist for apple, which supports a two-stage model of fruit enlargement ([Duan et al. 2017](https://doi.org/10.1038/s41467-017-00336-7)), peach ([Yu et al. 2018](https://doi.org/10.1038/s41467-018-07744-3)) and citrus ([Wu et al. 2018](https://doi.org/10.1038/nature25447)). For grape, domestication scans come from the 2017 and 2019 panels and the 3,525-accession study ([Zhou et al. 2017](https://doi.org/10.1073/pnas.1709257114); [Liang et al. 2019](https://doi.org/10.1038/s41467-019-09135-8); [Dong et al. 2023](https://doi.org/10.1126/science.add8655)). The grape genome also anchors the ancestral eudicot triplication, which helps orthology across eudicot crops ([Jaillon et al. 2007](https://doi.org/10.1038/nature06148)). OrthoFinder gives phylogenetic orthology with one-to-many relations ([Emms and Kelly 2019](https://doi.org/10.1186/s13059-019-1832-y)).

**Specific gap.** No study was found that runs one scan pipeline on grape and on other fruit and field crops and tests gene and pathway overlap against a null matched for gene length, diversity and orthology class [待确认].

## Question

Do grape and other crops share selected genes or pathways more often than expected under a matched null?

## Scope update (2026-11-26)

Added 2026-11-26. This section narrows or reframes the plan above; where the two differ, this section applies. Earlier text is kept unchanged.

**Null result preregistered as publishable.** A null result is likely (see [Lai et al. 2018](https://doi.org/10.1111/tpj.13806) and the risk table below). The preregistration states that a well-powered null is a result: the paper then reports the upper bound on convergence that the data can exclude.

Target: a first-quartile (Q1) journal in plant science, genetics or evolution. Quartile lists change each year, so the journal is chosen from the current list at submission [to confirm]. The points below are what the paper needs to compete at that level.

- A matched null that controls for gene length, recombination rate, gene family size and ancient duplications.
- A power calculation before the scans: the smallest excess of shared genes the design can detect.
- A smaller, deeper scope if needed: grape and two or three crops with public wild and domestic panels, rather than many crops with uneven data.
- One worked locus shown only if it passes the null, as in the sheep and goat study used as the reference below.

**Fallback.** If the panels for the comparison crops are too uneven for a matched design, drop to grape plus one crop.

## Hypotheses, planned figures and criteria

No results are given here. Each row says what would count as support; the exact thresholds go into the preregistration.

| Figure or table | Hypothesis or purpose | Criterion |
|---|---|---|
| Fig 1. Gene-level overlap vs null | Overlap exceeds the null. | Permutation within bins of gene length, family size and recombination proxy; one-sided test fixed in advance. |
| Fig 2. Pathway-level overlap | Overlap is stronger at pathway than at gene level. | Same null at pathway level. |
| Fig 3. Sensitivity to orthology | Results hold across orthology definitions. | Repeat with two orthology definitions. |

**Expected results and how they will be read**

- Fig 1: overlap above the matched null supports shared targets; overlap at the null level means that published lists of shared genes reflect gene features, not convergence.
- Fig 2: a stronger pathway than gene signal would fit selection on the same functions through different genes.
- Fig 3: results that change with the orthology definition are reported as not robust.
- Perennial-versus-annual contrasts are described, not tested, unless at least three crops per group pass QC.

## Preregistration

Before any data are analysed, fill in [`docs/PREREGISTRATION.md`](../../../../templates/PREREGISTRATION.md) for this project: hypotheses, primary outcome, sample inclusion rules, thresholds, stop rules and what will be reported if a hypothesis fails. Commit it with a date. Criteria from any earlier attempt are reference only and are not carried over.

## Data

| Module | Dataset |
|---|---|
| [DS10](../../data/DS10-reseq-472-vitis/) | Resequencing of 472 Vitis accessions (and the 2017 domestication panel) |
| [DS12](../../data/DS12-reseq-204-magris2021/) | Resequencing of 204 V. vinifera accessions (Magris et al. 2021) |
| [DS21](../../data/DS21-other-crop-population-genomes/) | Population genomes of other domesticated plants (comparison set) |
| [DS01](../../data/DS01-pn40024-references/) | PN40024 references: PN_T2T (v5), PN40024.v4 and 12X |

**How each dataset is used**

| Module | Role in this project |
|---|---|
| DS10, DS12 | Grape wild and cultivated panels (one sample per identity group) |
| DS21 | Population genomes of the comparison crops |
| DS01 | PN_T2T gene models for orthology |

New public data: none added here; each comparison crop must be confirmed in DS21 with accession and wild/cultivated labels before use [待确认].

## Analysis steps

Shared modules, in order:

1. [AM01 · Download and verify](../../analyses/AM01-download-and-verify/)
2. [AM03 · Short-read mapping and small-variant calling](../../analyses/AM03-short-read-variants/)
3. [AM11 · Diversity and selection scans](../../analyses/AM11-diversity-and-selection/)
4. [AM23 · Cross-crop orthology and convergence tests](../../analyses/AM23-cross-crop-convergence/)

Project-specific steps:

- Confirm accessions for each comparison crop (DS21).
- Run AM03 and AM11 the same way for each crop.
- Map to orthogroups (AM23); build the null; test overlap.

**Stepwise work plan with tools**

| Step | Work | Tools (paper) | Output |
|---|---|---|---|
| 1 | Confirm crops, panels, references and labels | DS21 | Crop table |
| 2 | Call variants the same way for each crop | AM03 | VCFs |
| 3 | Same scans for each crop (diversity ratio, FST, XP-CLR or equivalent) with fixed windows | AM11 | Gene-level scores |
| 4 | Orthogroups across crops; one-to-many handled explicitly | OrthoFinder (AM23) | Orthology table |
| 5 | Null from matched gene bins (length, diversity, orthology class) | R | Null distributions |
| 6 | Gene and pathway overlap tests; sensitivity to orthology choice | R | Fig 1 to Fig 3 |

## Paper design and split

| Paper | Working title | Type | Figures |
|---|---|---|---|
| M1 | Convergent domestication signals in grape and other crops | main paper | Fig 1–3 |

Each paper: introduction from the gap above; one results section per figure; methods with tool versions from the modules; data availability listing every accession used and the derived tables.

## Risks and novelty check

- Risk: Lineage-specific duplications make orthology one-to-many.
- Risk: Different sample sizes change scan power; downsample to equal sizes.
- Risk: Novelty: no dedicated literature search on this topic has been done beyond the grape literature base yet [待确认: repeat the search before writing].
- Novelty: checked against the existing work above (Crossref-verified DOIs). Repeat the search before writing; anything marked [待确认] is not yet verified.

## Risks and how to handle them

Added 2026-11-26. Each row names a risk, the evidence behind it, and a concrete check or fallback. Sources cited here were read for this section and their DOIs were checked on Crossref; preprints are marked.

| Area | Risk | Check or mitigation |
|---|---|---|
| Data access and licence | Most other-crop panels have FASTQ on ENA, but the apple SNP file named in its paper was not found and the Pan-Potato portal was partly down on the check ([data/DOWNLOADS.md](../../data/DOWNLOADS.md)). | Use raw reads from INSDC for every crop and call variants the same way; do not depend on portal files. |
| A null result is likely | In maize and sorghum, the overall number of genes with parallel selection signatures was not different from chance, although several classic domestication genes did show them ([Lai et al. 2018](https://doi.org/10.1111/tpj.13806)). | Preregister the power of the matched null (how much excess sharing could be detected) so that a null result is interpretable. |
| Duplication history as a confounder | Genes retained from ancient whole-genome duplications were enriched among domestication candidates in 14 of 22 crops, while small-scale duplicates were under-represented ([McKibben et al. 2026](https://doi.org/10.64898/2026.03.09.710542), preprint). Grape and other crops differ in polyploidy history. | Match the null on paleolog status and copy number as well as on gene length and diversity. |
| Different domestication syndromes | Domestication syndromes and genetic architectures vary widely among crops ([Alam et al. 2024](https://doi.org/10.1093/plcell/koae013)); a perennial, clonally propagated fruit crop need not share targets with annual seed crops. | Group crops by life history and propagation and test within groups as well as overall. |
| Reference bias and genome choice | Reference choice changes which windows are outliers ([Thorburn et al. 2023](https://doi.org/10.1111/1755-0998.13838)). | Use one reference per crop, fixed in advance, and repeat the grape scan on a second reference. |
| Sample size and power | Scan power differs with panel size (see above). | Downsample every crop to the same number of wild and domesticated samples. |
| Clones, synonyms and pedigree | Clonally propagated crops may contain duplicate genotypes that inflate sample counts. | Remove duplicates by genotype before scans. |
| Computing cost | Re-calling variants for several crops from raw reads is the largest cost. | Use published VCFs where they can be checked against raw reads on a subset. |

**Recent and competing work (search of 2024 to 2026 literature on 2026-11-26)**

- The paleolog result across 22 crops ([McKibben et al. 2026](https://doi.org/10.64898/2026.03.09.710542), preprint) is the closest cross-crop analysis found; it tests gene classes rather than shared orthologues, so the orthologue-level question remains open.

**What would end the idea, and the fallback.** If sharing does not exceed the matched null, convergence at gene level is not supported. The fallback is a null-result paper with the power analysis, or a pathway-level test.

**Journal-level realism.** The maize and sorghum null result appeared in *The Plant Journal*; a grape-centred cross-crop test fits mid-field at most unless it finds strong excess sharing.

## Reference study in another species

Added 2026-11-26. Published studies that already did this kind of work in another species, to plan the grape version against. Every DOI was checked on Crossref. Figures are described, not copied; a figure redrawn for a grape paper would be marked "Redrawn after" its source. The last bullet for each study lists what a grape results section would need; it is a planning suggestion, not a finding of that study.

### Sow et al. 2025

- **Paper:** [Sow et al. 2025](https://doi.org/10.1038/s41477-025-02128-0), *Nature Plants*.
- **Species:** Wheat and barley, 1,203 accessions.
- **What was done:** Orthologous groups were defined from the reconstructed ancestral Triticeae karyotype; selection scans were run separately in barley, emmer, durum and bread wheat, and shared signals across crops (orthoSweeps) were tested for enrichment against a random expectation.
- **Figures:** Fig. 1 Triticeae palaeohistory from ancestral to modern karyotypes; Fig. 2 diversity structure of the 1,203 accessions; Fig. 3 orthoSweeps between wheat and barley; Fig. 4 synchronously differentiated orthologous SNPs; Fig. 5 variation of a diversity index compared with GWAS signals; Fig. 6 species-specific diversity; Fig. 7 a model of convergent selection history.
- **What a grape results section would need:** orthogroup definition and filters; independent scans per crop; observed versus expected enrichment of shared signals; candidate genes and annotation.

### Alberto et al. 2018

- **Paper:** [Alberto et al. 2018](https://doi.org/10.1038/s41467-018-03206-y), *Nature Communications* (PMC5840369). Licence CC BY 4.0: figures may be reused with credit; none are copied here.
- **Species:** sheep and goats, with wild Asiatic mouflon and Bezoar ibex from the domestication centre.
- **What was done:** wild genomes were compared with local, traditional and improved breeds; 20 sweep regions separating domestic from wild were common to both genera, while the patterns of selection differed between species.
- **Figures:** Fig. 1 sampling relative to the domestication centre; Fig. 2 genome-wide maps of selected regions, specific and shared; Fig. 3 a shared region at *KITLG* in detail.
- **What its results section needed:** wild-versus-domestic scans in each species, a mapping of regions between genomes, a count of shared regions, and one worked locus.
- **Grape version:** the same three figures for grape and the comparison crops, with the matched null and power calculation from the Scope update above; a worked locus is shown only if one passes the null.

### Q1-level bar

Target: a first-quartile (Q1) journal in plant science, genetics or evolution. Quartile lists change each year, so the journal is chosen from the current list at submission [to confirm]. To compete at that level, the grape paper needs the points listed in the Scope update section above, which applies to this project.

## Rough estimates

- Compute: large [draft]
- Effort: 4–6 months for one person [draft]
- Target: evolution journal [draft]

## Suggested journal level (suggestion only)

**Mid-field journal (evolutionary biology or plant genomics); broad only with a strong positive result.** Single-crop domestication histories read here appeared in *Nature Communications*, *Nature* and *PNAS*; the cross-crop convergence studies in *Science*; syntheses in *Nat Rev Genet*, *Current Biology* and *Trends in Plant Science*. A re-analysis across public panels with a matched null fits a mid-field venue. This is a suggestion, not a decision; impact factors are not used.

## Continue on HPC

Run each step as its own job, in this order. Every job writes `.DONE` or `.FAILED` and a log; the next step starts only after `.DONE`. Template and rules: [`docs/HPC_JOBS.md`](../../../../templates/HPC_JOBS.md).

| Order | Step | Main tools | Resources (rough) |
|---|---|---|---|
| 1 | [AM01](../../analyses/AM01-download-and-verify/) Download and verify | ncbi-datasets-cli, sra-tools, ENA FTP / Aspera | 1–4 CPU, 4 GB, network; array over files |
| 2 | [AM03](../../analyses/AM03-short-read-variants/) Short-read mapping and small-variant calling | bwa-mem2, samtools, DeepVariant | 16 CPU, 64 GB, 6–24 h per sample (DeepVariant); joint step 32 CPU, 128 GB |
| 3 | [AM11](../../analyses/AM11-diversity-and-selection/) Diversity and selection scans | pixy, vcftools, RAiSD | 8 CPU, 32 GB per chromosome |
| 4 | [AM23](../../analyses/AM23-cross-crop-convergence/) Cross-crop orthology and convergence tests | OrthoFinder, MAFFT, IQ-TREE | 32 CPU, 128 GB for OrthoFinder |

Public inputs: [DS10](../../data/DS10-reseq-472-vitis/), [DS12](../../data/DS12-reseq-204-magris2021/), [DS21](../../data/DS21-other-crop-population-genomes/), [DS01](../../data/DS01-pn40024-references/).

## References

- Chen et al. 2022. Convergent selection of a WD40 protein that enhances grain yield in maize and rice. *Science*. [doi:10.1126/science.abg7985](https://doi.org/10.1126/science.abg7985)
- Yu et al. 2018. Genome re-sequencing reveals the evolutionary history of peach fruit edibility. *Nature Communications*. [doi:10.1038/s41467-018-07744-3](https://doi.org/10.1038/s41467-018-07744-3)
- Duan et al. 2017. Genome re-sequencing reveals the history of apple and supports a two-stage model for fruit enlargement. *Nature Communications*. [doi:10.1038/s41467-017-00336-7](https://doi.org/10.1038/s41467-017-00336-7)
- The French–Italian Public Consortium for Grapevine Genome Characterization 2007. The grapevine genome sequence suggests ancestral hexaploidization in major angiosperm phyla. *Nature*. [doi:10.1038/nature06148](https://doi.org/10.1038/nature06148)
- Dong et al. 2023. Dual domestications and origin of traits in grapevine evolution. *Science*. [doi:10.1126/science.add8655](https://doi.org/10.1126/science.add8655)
- Emms et al. 2019. OrthoFinder: phylogenetic orthology inference for comparative genomics. *Genome Biology*. [doi:10.1186/s13059-019-1832-y](https://doi.org/10.1186/s13059-019-1832-y)
- Gaut et al. 2018. Demography and its effects on genomic variation in crop domestication. *Nature Plants*. [doi:10.1038/s41477-018-0210-1](https://doi.org/10.1038/s41477-018-0210-1)
- Lenser et al. 2013. Molecular mechanisms involved in convergent crop domestication. *Trends in Plant Science*. [doi:10.1016/j.tplants.2013.08.007](https://doi.org/10.1016/j.tplants.2013.08.007)
- Liang et al. 2019. Whole-genome resequencing of 472 Vitis accessions for grapevine diversity and demographic history analyses. *Nature Communications*. [doi:10.1038/s41467-019-09135-8](https://doi.org/10.1038/s41467-019-09135-8)
- McKey et al. 2010. The evolutionary ecology of clonally propagated domesticated plants. *New Phytologist*. [doi:10.1111/j.1469-8137.2010.03210.x](https://doi.org/10.1111/j.1469-8137.2010.03210.x)
- Meyer et al. 2013. Evolution of crop species: genetics of domestication and diversification. *Nat Rev Genet*. [doi:10.1038/nrg3605](https://doi.org/10.1038/nrg3605)
- Miller et al. 2011. From forest to field: Perennial fruit crop domestication. *American Journal of Botany*. [doi:10.3732/ajb.1000522](https://doi.org/10.3732/ajb.1000522)
- Purugganan 2019. Evolutionary Insights into the Nature of Plant Domestication. *Current Biology*. [doi:10.1016/j.cub.2019.05.053](https://doi.org/10.1016/j.cub.2019.05.053)
- Wu et al. 2018. Genomics of the origin and evolution of Citrus. *Nature*. [doi:10.1038/nature25447](https://doi.org/10.1038/nature25447)
- Yeaman et al. 2016. Convergent local adaptation to climate in distantly related conifers. *Science*. [doi:10.1126/science.aaf7812](https://doi.org/10.1126/science.aaf7812)
- Zhou et al. 2017. Evolutionary genomics of grape (Vitis vinifera ssp. vinifera) domestication. *Proceedings of the National Academy of Sciences*. [doi:10.1073/pnas.1709257114](https://doi.org/10.1073/pnas.1709257114)
- Lai et al. 2018. Largely unlinked gene sets targeted by selection for domestication syndrome phenotypes in maize and sorghum. *The Plant Journal*. [doi:10.1111/tpj.13806](https://doi.org/10.1111/tpj.13806)
- McKibben et al. 2026. The Genomic Legacy of Ancient Polyploidy in Crop Domestication. *bioRxiv* (preprint). [doi:10.64898/2026.03.09.710542](https://doi.org/10.64898/2026.03.09.710542)
- Alam et al. 2024. Domestication and the evolution of crops: variable syndromes, complex genetic architectures, and ecological entanglements. *The Plant Cell*. [doi:10.1093/plcell/koae013](https://doi.org/10.1093/plcell/koae013)
- Thorburn et al. 2023. Origin matters: Using a local reference genome improves measures in population genomics. *Molecular Ecology Resources*. [doi:10.1111/1755-0998.13838](https://doi.org/10.1111/1755-0998.13838)
- Sow et al. 2025. Striking convergent selection history of wheat and barley and its potential for breeding. *Nature Plants*. [doi:10.1038/s41477-025-02128-0](https://doi.org/10.1038/s41477-025-02128-0)
- Alberto et al. 2018. Convergent genomic signatures of domestication in sheep and goats. *Nature Communications*. [doi:10.1038/s41467-018-03206-y](https://doi.org/10.1038/s41467-018-03206-y)
