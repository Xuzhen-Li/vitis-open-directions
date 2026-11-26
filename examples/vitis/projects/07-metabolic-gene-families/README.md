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

**Background survey (literature read for this plan)**

Grape has unusually large specialised-metabolism gene families. Stilbene synthase (STS), which makes resveratrol, evolved from chalcone synthase several times, and grape carries an unusually large STS family in tandem clusters ([Parage et al. 2012](https://doi.org/10.1104/pp.112.202705); [Vannozzi et al. 2012](https://doi.org/10.1186/1471-2229-12-130)). The terpene synthase (TPS) family was annotated and functionally characterised in the reference ([Martin et al. 2010](https://doi.org/10.1186/1471-2229-10-226)) and later compared on the phased genomes of Cabernet Sauvignon, Carménère and Chardonnay, where haplotigs revealed allelic variants ([Smit et al. 2020](https://doi.org/10.3389/fgene.2020.00421)). Carotenoid cleavage dioxygenases (CCD) produce aroma norisoprenoids and three members were characterised ([Lashbrooke et al. 2013](https://doi.org/10.1186/1471-2229-13-156)); lipoxygenase activity and LOX-mediated membrane changes mark the onset of berry ripening ([Pilati et al. 2014](https://doi.org/10.1186/1471-2229-14-87)).

Allelic variation in these pathways affects grape and wine traits. VvDXS co-localises with the major monoterpene QTL ([Battilana et al. 2009](https://doi.org/10.1007/s00122-008-0927-8)), and association mapping linked VvDXS variants to Muscat flavour ([Emanuelli et al. 2010](https://doi.org/10.1186/1471-2229-10-241)); a new TPS24 allele (VvGuaS) produces the precursor of the peppery compound rotundone ([Drew et al. 2016](https://doi.org/10.1093/jxb/erv491)). Gene-family birth and death can be estimated on a species tree with CAFE 5, which allows rates to vary among families ([Mendes et al. 2021](https://doi.org/10.1093/bioinformatics/btaa1022)). Near-complete grape haplotypes now exist in several pangenomes ([Liu et al. 2024](https://doi.org/10.1038/s41588-024-01967-5); [Guo et al. 2025](https://doi.org/10.1038/s41588-025-02111-7)).

**Specific gap.** STS and TPS were catalogued in single references or a few cultivars. No study was found that counts STS, TPS, CCD and LOX copies across many near-complete haplotypes with array-collapse checks and estimates their turnover against single-copy controls [待确认].

## Question

How variable are STS, TPS, CCD and LOX copy numbers among grape haplotypes, and do tandem families turn over faster than single-copy controls?

## Hypotheses, planned figures and criteria

No results are given here. Each row says what would count as support; the exact thresholds go into the preregistration.

| Figure or table | Hypothesis or purpose | Criterion |
|---|---|---|
| Fig 1. Copy number per haplotype | Tandem families (STS, TPS) vary more than single-copy controls. | Coefficient of variation with bootstrap intervals, against BUSCO single-copy genes. |
| Fig 2. Birth–death rates on the species tree | Between species, birth–death rates for STS and TPS exceed the genome-wide rate. | CAFE 5 run on one haplotype per species with a genome-wide background model; likelihood-ratio tests corrected across families. Copy-number differences among haplotypes of the same species reflect polymorphism rather than species-tree rates and are analysed separately (Fig 3). |
| Fig 3. Within-species copy-number polymorphism, wild vs cultivated | Copy number differs between wild and cultivated groups. | Permutation within species with the accession as the unit. |

**Expected results and how they will be read**

- Fig 1: a larger copy-number variance for STS and TPS than for matched single-copy controls supports tandem families as the variable part; the result is reported per family.
- Fig 2: CAFE 5 rates above the genome-wide rate for STS or TPS would support fast turnover between species; overlapping intervals are reported as no difference.
- Fig 3: wild versus cultivated copy-number differences are described with clone and relatedness filters applied; they are not interpreted as selection without a separate test.
- Known functional alleles (VvDXS, TPS24) serve as anchors to show that the catalogue recovers documented variants.

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

**How each dataset is used**

| Module | Role in this project |
|---|---|
| DS01 | Reference family annotations used as seeds |
| DS02, DS03, DS07 | Near-complete haplotypes for copy counts |
| DS08 | *Muscadinia* as outgroup for the species tree |
| DS10 | Short-read panel for within-species copy-number polymorphism by depth |

New public data: none needed.

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

**Stepwise work plan with tools**

| Step | Work | Tools (paper) | Output |
|---|---|---|---|
| 1 | Collect haplotypes; QC | AM01, AM05 | Manifest |
| 2 | Annotate STS, TPS, CCD, LOX and matched single-copy controls with family HMMs and reference proteins | miniprot ([Li 2023](https://doi.org/10.1093/bioinformatics/btad014)), HMMER (AM08) | Family tables |
| 3 | Check tandem arrays for collapse with read depth | minimap2, mosdepth | Corrected counts |
| 4 | Gene trees and orthogroups | MAFFT, IQ-TREE, OrthoFinder | Trees |
| 5 | Birth-death rates with a background model on the species tree | CAFE 5 | Fig 2 |
| 6 | Depth-based copy number in the short-read panel (one sample per clone group) | mosdepth, AM04 filters | Fig 3 |

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

## Risks and how to handle them

Added 2026-11-26. Each row names a risk, the evidence behind it, and a concrete check or fallback. Sources cited here were read for this section and their DOIs were checked on Crossref; preprints are marked.

| Area | Risk | Check or mitigation |
|---|---|---|
| Data access and licence | Assemblies and annotations used here are listed as available ([data/DOWNLOADS.md](../../data/DOWNLOADS.md)). | Freeze versions; record per haplotype whether long reads exist for collapse checks. |
| Assembly collapse | Draft assemblies get gene numbers wrong in a large share of gene families, both adding and losing copies ([Denton et al. 2014](https://doi.org/10.1371/journal.pcbi.1003998)); tandem STS and TPS arrays are exposed to the same problem (see above). | Count copies only in arrays that pass a completeness check (no gap, even read depth); report other arrays as minimum counts. |
| Annotation and naming | Gene models and names differ between studies (see above). | Count copies from protein-domain searches on the genome, not from each annotation, and keep a name-mapping table. |
| Reference bias and genome choice | Copy numbers projected from PN_T2T miss copies absent from it. | Count from each assembly directly. |
| Clones, synonyms and pedigree | Repeated genotypes and close relatives bias birth-death rates. | Collapse by genotype; fit rates on a tree that includes relatedness. |
| Sample size and power | Rate comparisons between families need enough complete arrays. | Fix the minimum number of complete arrays per family; below it, report counts only. |
| Computing cost | Small. | None beyond timing one haplotype. |
| Alternative methods and sensitivity | Birth-death estimates depend on the tree and on the model. | Compare a count-based model with a gene-tree reconciliation on the same families. |

**Recent and competing work (search of 2024 to 2026 literature on 2026-11-26)**

- TPS copy number variation has already been linked to monoterpene QTL in a grapevine mapping population ([Bosman et al. 2023](https://doi.org/10.3389/fpls.2023.1112214)); a copy-number-trait link for TPS is therefore not new, while multi-haplotype turnover is.
- A cluster of six UDP-glycosyltransferase genes was linked to stilbene glucoside (piceid) accumulation in wood ([Chepca et al. 2026](https://doi.org/10.64898/2026.10.24.761503), preprint). Stilbene modification genes are a natural extra family if the STS analysis works.

**What would end the idea, and the fallback.** If most STS and TPS arrays fail the completeness check outside T2T haplotypes, multi-haplotype rates are not reliable. The fallback is an STS-only study on T2T haplotypes.

**Journal-level realism.** Specialty plant biology or horticultural genomics journal, as for the grape gene-family papers read here.

## Reference study in another species

Added 2026-11-26. Published studies that already did this kind of work in another species, to plan the grape version against. Every DOI was checked on Crossref. Figures are described, not copied; a figure redrawn for a grape paper would be marked "Redrawn after" its source. The last bullet for each study lists what a grape results section would need; it is a planning suggestion, not a finding of that study.

### Lynch et al. 2025

- **Paper:** [Lynch et al. 2025](https://doi.org/10.1038/s41586-025-09065-0), *Nature*.
- **Species:** *Cannabis sativa*, 193 genomes (181 new and 12 published) from 144 samples.
- **What was done:** A cannabis pangenome was built; population structure, transposons and SVs were described; the cannabinoid synthase genes showed very low diversity although they sit in a variable region with pseudogenised paralogues, SVs and distinct transposon arrangements; copy numbers of pathway genes and terpene synthases were counted per assembly.
- **Figures:** Fig. 1 pangenome architecture and at least five populations; Fig. 2 transposons shape the pangenome; Fig. 3 SV frequencies by population and their non-random distribution; Fig. 4 the cannabinoid pathway, with gene copy numbers per assembly, diversity and synteny; Fig. 5 duplication and diversification of acyl-lipid thioesterase genes and the varin cannabinoid phenotype; Extended Data Fig. 7 terpene synthase copy number across the pangenome (chromosomes 5 and 6 are copy-number hotspots); other Extended Data figures cover genome similarity, the anchor genome, assembly quality, centromeres and telomeres, SV caller comparison, disease resistance genes, expression by sex and SV range. Licence CC BY 4.0 (PMC12286863).
- **What a grape results section would need:** copy number per assembly for each pathway gene family (STS, TPS, CCD, LOX); diversity and synteny of each cluster region; pseudogenised paralogues and transposon arrangement around clusters; a link from copy-number or sequence variants to a metabolite phenotype.

### Külheim et al. 2015

- **Paper:** [Külheim et al. 2015](https://doi.org/10.1186/s12864-015-1598-x), *BMC Genomics*.
- **Note:** Method reference only: the journal is not first-quartile, and the study uses one genome without birth-death rates.
- **Species:** *Eucalyptus grandis*, with *E. globulus*.
- **What was done:** 113 putatively functional terpene synthase (TPS) genes were identified in the *E. grandis* genome; clusters, gene structure, expression in tissues and phylogeny compared with grape and *Arabidopsis* were analysed, and products of some enzymes were tested in vitro.
- **Figures:** Fig. 1 phylogeny of the 113 TPS genes; Fig. 2 a 400 kb multi-gene cluster; Fig. 3 gene structure and motifs; Fig. 4 expression heatmap in seven tissues; Fig. 5 to 7 subfamily phylogenies compared with grape and *Arabidopsis*; Fig. 8 GC traces of in vitro products.
- **What a grape results section would need:** TPS and STS copy number and cluster structure per haplotype; subfamily phylogeny; collapse checks in cluster regions; expression support.

### Tong et al. 2025

- **Paper:** [Tong et al. 2025](https://doi.org/10.1016/j.xplc.2024.101190), *Plant Communications* (PMC11783906). Licence CC BY 4.0: figures may be reused with credit; none are copied here.
- **Species:** barley, 20 genome assemblies (the bHLH transcription factor family).
- **What was done:** 161 to 176 bHLH genes per genome were grouped into 201 orthologous gene groups (140 core, 12 softcore, 29 shell, 20 cloud); a genome scan found on average 1.5 un-annotated core bHLH genes per genome; whole-genome and segmental duplicates explained most core expansion, small-scale duplication most dispensable genes; genes with copy-number variation had more nearby transposable elements; selection and expression were compared between core and dispensable genes.
- **Figures:** Fig. 1 genes per assembly and the core and dispensable split; Fig. 2 phylogeny with rice; Fig. 3 copy-number heatmap; Fig. 4 duplication types and nearby transposable elements; Fig. 5 Ka, Ks and Ka/Ks for core and dispensable genes; Fig. 6 pantranscriptome expression.
- **What its results section needed:** a family census on every assembly with a scan for un-annotated copies, a core and dispensable split, duplication mode, selection and expression.
- **Grape version:** the same six panels for STS, TPS, CCD and LOX across grape haplotypes; the genome scan for un-annotated copies doubles as the annotation check, and read depth over tandem arrays addresses the collapse risk above; expression comes from project 19.

### Coverage note

Külheim et al. 2015 analyses a single genome and gives no birth-death rates. Lynch et al. 2025 adds gene copy number across a pangenome, but its full text does not use a birth-death rate model; a template with such rates is still to be found [to confirm].

### Q1-level bar

Target: a first-quartile (Q1) journal in plant science, genetics or evolution. Quartile lists change each year, so the journal is chosen from the current list at submission [to confirm]. To compete at that level, the grape paper needs: copy number per haplotype with collapse checks in each cluster, a rate or selection estimate across *Vitis* that the single-genome studies lack, and a link to expression or to a trait such as aroma or stilbene content.

## Rough estimates

- Compute: medium [draft]
- Effort: 2–3 months for one person [draft]
- Target: plant biology or genome journal [draft]

## Suggested journal level (suggestion only)

**Specialty journal (plant biology or horticultural genomics).** The grape STS, TPS, CCD and LOX papers read here appeared in *BMC Plant Biology*, *Plant Physiology*, *Frontiers in Genetics*, *Journal of Experimental Botany* and *Theoretical and Applied Genetics*. A multi-haplotype copy-number and turnover study extends this line and fits the same level. This is a suggestion, not a decision; impact factors are not used.

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
- Battilana et al. 2009. The 1-deoxy-d-xylulose 5-phosphate synthase gene co-localizes with a major QTL affecting monoterpene content in grapevine. *Theoretical and Applied Genetics*. [doi:10.1007/s00122-008-0927-8](https://doi.org/10.1007/s00122-008-0927-8)
- Drew et al. 2016. Two key polymorphisms in a newly discovered allele of the Vitis vinifera TPS24 gene are responsible for the production of the rotundone precursor α-guaiene. *Journal of Experimental Botany*. [doi:10.1093/jxb/erv491](https://doi.org/10.1093/jxb/erv491)
- Emanuelli et al. 2010. A candidate gene association study on muscat flavor in grapevine (Vitis vinifera L.). *BMC Plant Biology*. [doi:10.1186/1471-2229-10-241](https://doi.org/10.1186/1471-2229-10-241)
- Guo et al. 2025. Super pangenome of Vitis empowers identification of downy mildew resistance genes for grapevine improvement. *Nature Genetics*. [doi:10.1038/s41588-025-02111-7](https://doi.org/10.1038/s41588-025-02111-7)
- Lashbrooke et al. 2013. Functional characterisation of three members of the Vitis viniferaL. carotenoid cleavage dioxygenase gene family. *BMC Plant Biology*. [doi:10.1186/1471-2229-13-156](https://doi.org/10.1186/1471-2229-13-156)
- Li 2023. Protein-to-genome alignment with miniprot. *Bioinformatics*. [doi:10.1093/bioinformatics/btad014](https://doi.org/10.1093/bioinformatics/btad014)
- Liu et al. 2024. Grapevine pangenome facilitates trait genetics and genomic breeding. *Nature Genetics*. [doi:10.1038/s41588-024-01967-5](https://doi.org/10.1038/s41588-024-01967-5)
- Mendes et al. 2021. CAFE 5 models variation in evolutionary rates among gene families. *Bioinformatics*. [doi:10.1093/bioinformatics/btaa1022](https://doi.org/10.1093/bioinformatics/btaa1022)
- Parage et al. 2012. Structural, Functional, and Evolutionary Analysis of the Unusually Large Stilbene Synthase Gene Family in Grapevine. *Plant Physiology*. [doi:10.1104/pp.112.202705](https://doi.org/10.1104/pp.112.202705)
- Pilati et al. 2014. The onset of grapevine berry ripening is characterized by ROS accumulation and lipoxygenase-mediated membrane peroxidation in the skin. *BMC Plant Biology*. [doi:10.1186/1471-2229-14-87](https://doi.org/10.1186/1471-2229-14-87)
- Denton et al. 2014. Extensive Error in the Number of Genes Inferred from Draft Genome Assemblies. *PLoS Computational Biology*. [doi:10.1371/journal.pcbi.1003998](https://doi.org/10.1371/journal.pcbi.1003998)
- Bosman et al. 2023. Grapevine genome analysis demonstrates the role of gene copy number variation in the formation of monoterpenes. *Frontiers in Plant Science*. [doi:10.3389/fpls.2023.1112214](https://doi.org/10.3389/fpls.2023.1112214)
- Chepca et al. 2026. Genetic analysis of grapevine wood composition identifies glycosyltransferases involved in the biosynthesis of stilbene glycosides. *bioRxiv* (preprint). [doi:10.64898/2026.10.24.761503](https://doi.org/10.64898/2026.10.24.761503)
- Lynch et al. 2025. Domesticated cannabinoid synthases amid a wild mosaic cannabis pangenome. *Nature*. [doi:10.1038/s41586-025-09065-0](https://doi.org/10.1038/s41586-025-09065-0)
- Külheim et al. 2015. The Eucalyptus terpene synthase gene family. *BMC Genomics*. [doi:10.1186/s12864-015-1598-x](https://doi.org/10.1186/s12864-015-1598-x)
- Tong et al. 2025. Pangenome and pantranscriptome as the new reference for gene-family characterization: A case study of basic helix-loop-helix (bHLH) genes in barley. *Plant Communications*. [doi:10.1016/j.xplc.2024.101190](https://doi.org/10.1016/j.xplc.2024.101190)
