# 03. Endogenous florendovirus insertions across grape haplotypes

中文：葡萄泛基因组中的内源 florendovirus

Rank 3 of 22 (score F 3 + N 2 + E 2 = 7; see docs/RANKING.md) · Tier: Medium (E = 2, effort range ending after 6 weeks and by 4 months) · Origin: new · Status: draft v0.3.2, 2026-11-14

## Gap

Endogenous florendovirus insertions were described from single references. Presence/absence of each insertion across haplotypes and wild *Vitis* is not catalogued [待确认].

**Existing work**

- [Geering et al. 2014](https://doi.org/10.1038/ncomms6269): florendoviruses in many angiosperm genomes, including grape.
- [Bertsch et al. 2009](https://doi.org/10.1186/1745-6150-4-21): endogenous pararetrovirus sequences in grape.

**How this project differs**

Treats each insertion as a locus and genotypes it across haplotypes by flanking synteny.

**Background survey (literature read for this plan)**

Endogenous viral elements (EVEs) are viral sequences integrated into host nuclear genomes. Most plant EVEs come from pararetroviruses of the family *Caulimoviridae*, which lack an integrase and enter the genome by chance ([Staginnus and Richert-Pöggeler 2006](https://doi.org/10.1016/j.tplants.2006.08.008)). Some endogenous pararetroviruses can be reactivated and give infectious virus ([Chabannes and Iskra-Caruana 2013](https://doi.org/10.1016/j.coviro.2013.08.012)), and endogenous viruses more broadly record viral evolution over long time scales ([Feschotte and Gilbert 2012](https://doi.org/10.1038/nrg3199)).

Geering and colleagues described the genus *Florendovirus*, whose members colonised many flowering-plant genomes, sometimes at more than 0.5% of genome content, and dated the invasion of *Oryza* to more than 1.8 million years ago ([Geering et al. 2014](https://doi.org/10.1038/ncomms6269)). Refined search methods later showed that caulimovirid EVEs occur across tracheophytes and record the deep history of the family ([Diop et al. 2018](https://doi.org/10.1038/s41598-017-16399-x)), and a genome-wide search of reverse-transcriptase domains identified recently inserted endogenous pararetroviruses across many plant assemblies ([de Tomás and Vicient 2022](https://doi.org/10.3389/fpls.2022.1011565)). In grape, two nuclear genomes already showed several horizontal transfers of pararetrovirus sequence, which the authors proposed as a pathway to virus resistance ([Bertsch et al. 2009](https://doi.org/10.1186/1745-6150-4-21)).

These grape analyses used one or two reference assemblies. Haplotype-resolved assemblies now exist for cultivated and wild *Vitis* ([Liu et al. 2024](https://doi.org/10.1038/s41588-024-01967-5); [Guo et al. 2025](https://doi.org/10.1038/s41588-025-02111-7)) and North American species ([Cochetel et al. 2023](https://doi.org/10.1186/s13059-023-03133-2)).

**Specific gap.** No locus-by-locus presence/absence table of florendovirus insertions across grape haplotypes and species was found, so it is unknown which insertions are fixed, which are polymorphic, and whether sharing follows the species tree [待确认].

## Question

Which florendovirus insertions are shared by all grapes and which are polymorphic, and does sharing follow the species tree?

## Scope update (2026-11-26)

Added 2026-11-26. This section narrows or reframes the plan above; where the two differ, this section applies. Earlier text is kept unchanged.

**What grape adds beyond existing work.** The comparative *Prunus* study ([Vicient 2026](https://doi.org/10.3389/fpls.2026.1886618)) counts and classifies elements per genome across 15 species. Grape adds a locus-level view inside one genus: each insertion is genotyped as present or absent across cultivated and wild haplotypes and *Muscadinia*, so insertion age and sharing can be tested against the species tree and the domestication split.

Target: a first-quartile (Q1) journal in plant science, genetics or evolution. Quartile lists change each year, so the journal is chosen from the current list at submission [to confirm]. The points below are what the paper needs to compete at that level.

- A locus-by-haplotype presence and absence matrix with flanking-synteny evidence for every call.
- A test of whether sharing follows the species tree, with discordant loci explained (incomplete lineage sorting, introgression or deletion).
- Expression of insertions from public RNA-seq (project 19) as evidence of activity or silencing.
- A direct comparison with the *Prunus* and angiosperm-wide results, stating which patterns are general and which are grape-specific.

**Fallback.** If too few polymorphic insertions are found, report the catalogue and the tree test as a short resource paper and say so in the preregistration.

## Hypotheses, planned figures and criteria

No results are given here. Each row says what would count as support; the exact thresholds go into the preregistration.

| Figure or table | Hypothesis or purpose | Criterion |
|---|---|---|
| Fig 1. Insertion catalogue per haplotype | Not a hypothesis: catalogue. | Insertions defined by protein similarity plus flanking synteny; similarity and synteny thresholds fixed in advance. |
| Fig 2. Polymorphic vs fixed insertions | Polymorphic insertions are less degraded (younger) than fixed ones. | ORF integrity (complete or incomplete) compared between classes with Fisher's exact test or logistic regression, and divergence with a rank test; one-sided direction stated in advance. |
| Fig 3. Sharing pattern vs species tree | Orthologous insertions are shared consistently with the species tree. | Consistency index on the species tree compared with trees whose leaf labels are permuted (permutation scheme fixed in advance). |

**Expected results and how they will be read**

- Fig 1 gives the number of insertion loci per haplotype and their total length; this is a catalogue, reported with search sensitivity on PN_T2T.
- Fig 2: if polymorphic insertions have more intact ORFs and lower divergence than fixed ones, that supports ongoing or recent integration; if not, polymorphism is more likely due to deletion of old insertions.
- Fig 3: a consistency index above the permutation null supports vertical inheritance; loci that conflict with the tree are listed as candidates for introgression or independent integration.

## Preregistration

Before any data are analysed, fill in [`docs/PREREGISTRATION.md`](../../../../templates/PREREGISTRATION.md) for this project: hypotheses, primary outcome, sample inclusion rules, thresholds, stop rules and what will be reported if a hypothesis fails. Commit it with a date. Criteria from any earlier attempt are reference only and are not carried over.

## Data

| Module | Dataset |
|---|---|
| [DS01](../../data/DS01-pn40024-references/) | PN40024 references: PN_T2T (v5), PN40024.v4 and 12X |
| [DS02](../../data/DS02-grapepan-v1/) | Grapepan v1.0: T2T haplotypes, graphs and a 466-accession resequencing panel |
| [DS03](../../data/DS03-vitis-super-pangenome-72/) | Vitis super-pangenome: 72 haplotype-resolved accessions |
| [DS04](../../data/DS04-na-vitis-super-pangenome/) | North American Vitis super-pangenome and wild resequencing |
| [DS05](../../data/DS05-vitaceae-family-genomes/) | Vitaceae family chromosome-level genomes |
| [DS06](../../data/DS06-vitis-amurensis-pangenome/) | Vitis amurensis haplotype assemblies and 330-sample resequencing |

**How each dataset is used**

| Module | Role in this project |
|---|---|
| DS01 | PN_T2T: positive control and coordinate system |
| DS02, DS03 | Cultivated and wild *Vitis* haplotypes |
| DS04, DS06 | North American *Vitis* and *V. amurensis* haplotypes for the species-tree test |
| DS05 | Other Vitaceae genera as outgroups for insertion age |

New public data: none needed. Florendovirus reference proteins come from the published papers and public virus databases [待确认: exact protein set].

## Analysis steps

Shared modules, in order:

1. [AM01 · Download and verify](../../analyses/AM01-download-and-verify/)
2. [AM05 · Assembly QC](../../analyses/AM05-assembly-qc/)
3. [AM16 · Virus discovery in RNA-seq and endogenous viral elements in assemblies](../../analyses/AM16-virus-and-eve-search/)
4. [AM06 · Whole-genome alignment, synteny and SVs from assemblies](../../analyses/AM06-wga-and-sv/)

Project-specific steps:

- Search assemblies with florendovirus protein seeds (AM16, DIAMOND).
- Cluster hits into loci by flanking sequence (AM06).
- Score each locus present or absent per haplotype; build the matrix.

**Stepwise work plan with tools**

| Step | Work | Tools (paper) | Output |
|---|---|---|---|
| 1 | Collect haplotypes and pass AM05 QC | AM01, AM05 | Manifest |
| 2 | Build a seed set of *Caulimoviridae* proteins (reverse transcriptase, coat protein, movement protein) | public virus protein sets [待确认] | Seed FASTA |
| 3 | Protein-to-genome search in every haplotype | DIAMOND or miniprot (AM16) | Raw hits |
| 4 | Merge hits into insertions and define each locus by its flanks | bedtools, minimap2 (AM06) | Locus table |
| 5 | Score presence, absence or not assessable per haplotype from flank synteny | SyRI (AM06) | Presence/absence matrix |
| 6 | ORF integrity and divergence between copies; phylogeny of reverse-transcriptase domains | MAFFT, IQ-TREE | Fig 2 inputs |
| 7 | Consistency index against the species tree; permutation null | R phangorn | Fig 3 statistics |

## Paper design and split

| Paper | Working title | Type | Figures |
|---|---|---|---|
| C1 | Endogenous florendoviruses across the grape pangenome | short paper | Fig 1–3 |

Each paper: introduction from the gap above; one results section per figure; methods with tool versions from the modules; data availability listing every accession used and the derived tables.

## Risks and novelty check

- Risk: Fragmented viral copies may be missed or merged.
- Risk: Flanks inside repeats make orthology uncertain.
- Risk: Novelty: no dedicated literature search on this topic has been done beyond the grape literature base yet [待确认: repeat the search before writing].
- Novelty: checked against the existing work above (Crossref-verified DOIs). Repeat the search before writing; anything marked [待确认] is not yet verified.

## Risks and how to handle them

Added 2026-11-26. Each row names a risk, the evidence behind it, and a concrete check or fallback. Sources cited here were read for this section and their DOIs were checked on Crossref; preprints are marked.

| Area | Risk | Check or mitigation |
|---|---|---|
| Data access and licence | All assembly modules used here are listed as available ([data/DOWNLOADS.md](../../data/DOWNLOADS.md)); INSDC data are free and open ([INSDC 2024](https://doi.org/10.1093/nar/gkae1058)). The florendovirus protein set is still open. | Fix the reference protein set and its source release in the preregistration. |
| Sample size and power | The species-tree test needs enough species with near-complete assemblies; a handful of species gives little power to reject random sharing. | Count species and haplotypes per clade first; add the new Vitaceae assemblies ([Wang et al. 2026](https://doi.org/10.64898/2026.04.20.719760), preprint); if clades stay thin, report sharing descriptively. |
| Detection method | Two detection methods in strawberry genomes (homology search and genome alignment) found different sets of endogenous pararetroviruses ([Wang et al. 2024](https://doi.org/10.3390/v16081306)). | Run two independent detections (RT-domain search and CAULIFINDER) and report the overlap; only loci found by both enter the main tests. |
| Annotation failure | Standard repeat annotation programs are poor at finding and classifying caulimovirid elements ([Vassilieff et al. 2022](https://doi.org/10.1186/s13100-022-00288-w)), so TE masking before the search can hide them. | Search unmasked assemblies; record how many hits overlap TE annotations. |
| Orthology in repeats | Flanks inside repeats make orthology uncertain (see above). | Require unique flanks on both sides for orthology; report other loci as unresolved rather than forcing a call. |
| Reference bias and genome choice | Presence calls from short reads mapped to PN_T2T would miss insertions absent from that reference. | Call presence from assemblies only; use reads only to confirm assembled loci. |
| Clones, synonyms and pedigree | Repeated assemblies of one genotype inflate sharing. | Collapse by genotype using the project 08 table. |
| Computing cost | Small: protein searches and alignments on assemblies. | None needed beyond timing one genome. |
| Alternative methods and sensitivity | Age estimates from copy divergence depend on an assumed rate. | Report relative ages (divergence between copies) and give dates only as ranges. |

**Recent and competing work (search of 2024 to 2026 literature on 2026-11-26)**

- A comparative study of 30 chromosome-level *Prunus* assemblies from 15 species found 781 caulimovirid RT sequences, with Florendovirus-1 the main lineage, and rebuilt a consensus from complete elements ([Vicient 2026](https://doi.org/10.3389/fpls.2026.1886618)). The design of this project now has a direct template in another genus; a grape study is a parallel case and should compare with it.
- Endogenous caulimovirids have been surveyed broadly ([Vassilieff et al. 2023](https://doi.org/10.3390/biom13071069)); no grape-wide multi-haplotype study was found in this search.

**What would end the idea, and the fallback.** If almost all insertions are shared by every *Vitis* haplotype, the polymorphism and species-tree questions have no signal. The fallback is an age and integration catalogue for grape set against the *Prunus* results.

**Journal-level realism.** The *Prunus* study appeared in *Frontiers in Plant Science*; a grape counterpart fits the same specialty level unless it shows insertions with clear effects on nearby genes.

## Reference study in another species

Added 2026-11-26. Published studies that already did this kind of work in another species, to plan the grape version against. Every DOI was checked on Crossref. Figures are described, not copied; a figure redrawn for a grape paper would be marked "Redrawn after" its source. The last bullet for each study lists what a grape results section would need; it is a planning suggestion, not a finding of that study.

### Geering et al. 2014

- **Paper:** [Geering et al. 2014](https://doi.org/10.1038/ncomms6269), *Nature Communications*.
- **Note:** This paper includes grape; only its dating of orthologous loci in *Oryza* is the cross-species part.
- **Species:** Many angiosperms, including grape; orthologous loci in 12 *Oryza* species were used for dating.
- **What was done:** Endogenous florendovirus elements were found and assembled in many plant genomes and classified by phylogeny; insertions were placed on orthologous loci across *Oryza* to date them; their relation to transposable elements, genes, (TA)n repeats and small RNA origin was analysed.
- **Figures:** Fig. 1 genome organisation compared with other Caulimoviridae; Fig. 2 Caulimoviridae phylogeny; Fig. 3 bipartite florendovirus genomes, including grape, rice and sorghum examples; Fig. 4 54 rice florendovirus loci placed on the *Oryza* tree (insertion dating); Fig. 5 distance of elements to transposable elements and genes in Pinot Noir and rice; Fig. 6 co-location with (TA)n repeats.
- **What a grape results section would need:** a presence and absence matrix of each insertion across haplotypes and wild species; insertion dating by placing orthologous loci on the tree (as in Fig. 4); distances to transposable elements, genes and repeats; small RNA origin where data exist.

### Vicient 2026

- **Paper:** [Vicient 2026](https://doi.org/10.3389/fpls.2026.1886618), *Frontiers in Plant Science* (PMC13658181). Licence CC BY 4.0: figures may be reused with credit; none are copied here.
- **Species:** 30 chromosome-level assemblies of *Prunus* from 15 species, with almond for the detailed analysis.
- **What was done:** reverse transcriptase (RT) sequences of endogenous caulimovirids were found and classified across the assemblies, Florendovirus-1 was the main lineage, a consensus genome was rebuilt, and complete and fragmentary elements were described in almond.
- **Figures:** Fig. 1 maximum-likelihood tree of RT sequences from the 30 assemblies; Fig. 2 Florendovirus and Yendovirus RT density (copies per Mb) per assembly on the *Prunus* tree; Fig. 3 genome map of Florendovirus-1 in almond with ORFs and protein domains; Fig. 4 structure of complete and fragmentary elements and their integration breakpoints; Fig. 5 tree of Florendovirus-1 RT copies within almond.
- **What its results section needed:** lineage classification, copy density per genome against the species tree, a reconstructed consensus genome, element structure and a within-genome tree.
- **Grape version and what grape adds:** the same five panels for *Vitis* and *Muscadinia*, plus what the *Prunus* study did not do: each insertion is a locus genotyped as present or absent across haplotypes of one species and its wild relatives, so sharing can be tested against the species tree and the domestication split (see Scope update above).

### Coverage note

Geering et al. 2014 includes grape itself; only its dating of orthologous loci in *Oryza* is cross-species. The *Prunus* study is the closest template from another genus, but it does not genotype insertions as present or absent across a population.

### Q1-level bar

Target: a first-quartile (Q1) journal in plant science, genetics or evolution. Quartile lists change each year, so the journal is chosen from the current list at submission [to confirm]. To compete at that level, the grape paper needs the points listed in the Scope update section above, which applies to this project.

## Rough estimates

- Compute: small [draft]
- Effort: 1–2 months for one person [draft]
- Target: virology or genome journal [draft]

## Suggested journal level (suggestion only)

**Specialty journal (virology or plant genome evolution).** The grape and EVE papers read here appeared in *Biology Direct*, *Scientific Reports* and *Frontiers in Plant Science*; only the paper that defined a new genus across many plant genomes appeared in *Nature Communications*. A within-genus locus catalogue is a specialty contribution. This is a suggestion, not a decision; impact factors are not used.

## Continue on HPC

Run each step as its own job, in this order. Every job writes `.DONE` or `.FAILED` and a log; the next step starts only after `.DONE`. Template and rules: [`docs/HPC_JOBS.md`](../../../../templates/HPC_JOBS.md).

| Order | Step | Main tools | Resources (rough) |
|---|---|---|---|
| 1 | [AM01](../../analyses/AM01-download-and-verify/) Download and verify | ncbi-datasets-cli, sra-tools, ENA FTP / Aspera | 1–4 CPU, 4 GB, network; array over files |
| 2 | [AM05](../../analyses/AM05-assembly-qc/) Assembly QC | compleasm, BUSCO, Merqury | 16 CPU, 64 GB, 1–3 h per assembly; array |
| 3 | [AM16](../../analyses/AM16-virus-and-eve-search/) Virus discovery in RNA-seq and endogenous viral elements in assemblies | DIAMOND, MEGAHIT, SPAdes (rnaviralSPAdes) | 16 CPU, 64 GB per run for assembly |
| 4 | [AM06](../../analyses/AM06-wga-and-sv/) Whole-genome alignment, synteny and SVs from assemblies | minimap2, SyRI, AnchorWave | 16 CPU, 64 GB, 1–4 h per haplotype; array |

Public inputs: [DS01](../../data/DS01-pn40024-references/), [DS02](../../data/DS02-grapepan-v1/), [DS03](../../data/DS03-vitis-super-pangenome-72/), [DS04](../../data/DS04-na-vitis-super-pangenome/), [DS05](../../data/DS05-vitaceae-family-genomes/), [DS06](../../data/DS06-vitis-amurensis-pangenome/).

## References

- Geering et al. 2014. Endogenous florendoviruses are major components of plant genomes and hallmarks of virus evolution. *Nature Communications*. [doi:10.1038/ncomms6269](https://doi.org/10.1038/ncomms6269)
- Bertsch et al. 2009. Retention of the virus-derived sequences in the nuclear genome of grapevine as a potential pathway to virus resistance. *Biology Direct*. [doi:10.1186/1745-6150-4-21](https://doi.org/10.1186/1745-6150-4-21)
- Chabannes et al. 2013. Endogenous pararetroviruses—a reservoir of virus infection in plants. *Current Opinion in Virology*. [doi:10.1016/j.coviro.2013.08.012](https://doi.org/10.1016/j.coviro.2013.08.012)
- Cochetel et al. 2023. A super-pangenome of the North American wild grape species. *Genome Biology*. [doi:10.1186/s13059-023-03133-2](https://doi.org/10.1186/s13059-023-03133-2)
- de Tomás et al. 2022. Genome-wide identification of Reverse Transcriptase domains of recently inserted endogenous plant pararetrovirus (Caulimoviridae). *Frontiers in Plant Science*. [doi:10.3389/fpls.2022.1011565](https://doi.org/10.3389/fpls.2022.1011565)
- Diop et al. 2018. Tracheophyte genomes keep track of the deep evolution of the Caulimoviridae. *Scientific Reports*. [doi:10.1038/s41598-017-16399-x](https://doi.org/10.1038/s41598-017-16399-x)
- Feschotte et al. 2012. Endogenous viruses: insights into viral evolution and impact on host biology. *Nat Rev Genet*. [doi:10.1038/nrg3199](https://doi.org/10.1038/nrg3199)
- Guo et al. 2025. Super pangenome of Vitis empowers identification of downy mildew resistance genes for grapevine improvement. *Nature Genetics*. [doi:10.1038/s41588-025-02111-7](https://doi.org/10.1038/s41588-025-02111-7)
- Liu et al. 2024. Grapevine pangenome facilitates trait genetics and genomic breeding. *Nature Genetics*. [doi:10.1038/s41588-024-01967-5](https://doi.org/10.1038/s41588-024-01967-5)
- Staginnus et al. 2006. Endogenous pararetroviruses: two-faced travelers in the plant genome. *Trends in Plant Science*. [doi:10.1016/j.tplants.2006.08.008](https://doi.org/10.1016/j.tplants.2006.08.008)
- INSDC 2024. The international nucleotide sequence database collaboration (INSDC): enhancing global participation. *Nucleic Acids Research*. [doi:10.1093/nar/gkae1058](https://doi.org/10.1093/nar/gkae1058)
- Wang et al. 2026. Origin and evolution of grapevine genomes. *bioRxiv* (preprint). [doi:10.64898/2026.04.20.719760](https://doi.org/10.64898/2026.04.20.719760)
- Wang et al. 2024. Study of Endogenous Viruses in the Strawberry Plants. *Viruses*. [doi:10.3390/v16081306](https://doi.org/10.3390/v16081306)
- Vassilieff et al. 2022. CAULIFINDER: a pipeline for the automated detection and annotation of caulimovirid endogenous viral elements in plant genomes. *Mobile DNA*. [doi:10.1186/s13100-022-00288-w](https://doi.org/10.1186/s13100-022-00288-w)
- Vicient 2026. A comprehensive comparative genomic analysis of the endogenous Florendovirus-1 in Prunus. *Frontiers in Plant Science*. [doi:10.3389/fpls.2026.1886618](https://doi.org/10.3389/fpls.2026.1886618)
- Vassilieff et al. 2023. Endogenous Caulimovirids: Fossils, Zombies, and Living in Plant Genomes. *Biomolecules*. [doi:10.3390/biom13071069](https://doi.org/10.3390/biom13071069)
