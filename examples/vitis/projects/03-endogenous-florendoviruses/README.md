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
