# 26. Grapevine mitochondrial genomes, nuclear mitochondrial insertions and heteroplasmy

中文：葡萄线粒体基因组、核内线粒体插入与异质性

Not scored (see docs/RANKING.md; projects 23 to 26 were added after the ranking) · Tier: Medium [draft] · Origin: new · Status: draft, 2026-11-25; the defining question is open · Progress: [STATUS.md](STATUS.md)

## Gap

A grape pan-mitogenome and NUMT and NUPT counts already exist for 33 accessions. What was not found is a systematic analysis on PN_T2T that (i) keeps recombination-derived mitochondrial configurations as assembly graphs, (ii) exports NUMT and NUPT masks for nuclear variant calling, and (iii) tests heteroplasmy only after organelle-derived nuclear reads are filtered out [待确认: repeat the search before writing].

**Existing work and background survey**

Plant mitochondrial genomes are large and dynamic because repeats recombine, producing subgenomic forms and variation within a species ([Gualberto and Newton 2017](https://doi.org/10.1146/annurev-arplant-043015-112232)); one circular map rarely describes the molecules present ([Kozik et al. 2019](https://doi.org/10.1371/journal.pgen.1008373)); in *Silene*, mitochondrial genomes became enormous and multichromosomal ([Sloan et al. 2012](https://doi.org/10.1371/journal.pbio.1001241)).

In grape, the reference mitochondrial genome is 773,279 nt with a large share of plastid-derived DNA ([Goremykin et al. 2008](https://doi.org/10.1093/molbev/msn226)); the plastid genome is 160,928 bp ([Jansen et al. 2006](https://doi.org/10.1186/1471-2148-6-32)); both organelle genomes of the rootstock Börner were assembled from long reads and were maternally inherited from *V. riparia* ([Frommer et al. 2020](https://doi.org/10.1128/mra.01471-19)); a pan-mitogenome and pan-plastome of 33 wild and domesticated accessions found 212 to 431 NUMTs and 95 to 205 NUPTs per genome and more NUMTs in cultivated grapes ([Hou et al. 2025](https://doi.org/10.1111/jipb.13968)). NUMTs and NUPTs were compared across six plant species ([Michalovova et al. 2013](https://doi.org/10.1038/hdy.2013.51)).

Tools: GetOrganelle assembles organelle genomes from whole-genome reads and reports all circular configurations ([Jin et al. 2020](https://doi.org/10.1186/s13059-020-02154-5)); Oatk uses syncmer-based graphs and profile HMMs for complex plant organelle genomes ([Zhou et al. 2025](https://doi.org/10.1186/s13059-025-03676-6)); PMAT assembles plant mitogenomes from low-coverage HiFi data ([Bi et al. 2024](https://doi.org/10.1093/hr/uhae023)); Flye builds repeat graphs from long reads ([Kolmogorov et al. 2019](https://doi.org/10.1038/s41587-019-0072-8)).

**How this project differs**

Assembly graphs and alternative configurations are kept, not only one circle. The first deliverable is a NUMT and NUPT mask on PN_T2T that the nuclear projects can use. Heteroplasmy is attempted only after the mask and the catalogue pass their checks.

## Question

Candidate questions, one to be fixed in the preregistration [待确认]: (a) a catalogue of complete mitochondrial assembly graphs across *Vitis* and *Muscadinia* from public long reads; (b) NUMT and NUPT masks on PN_T2T; (c) a maternal phylogeny from organelle sequences; (d) heteroplasmy, only after (a) and (b).

## Hypotheses, planned figures and criteria

No results are given here. Each row says what would count as support; the exact thresholds go into the preregistration.

| Figure or table | Hypothesis or purpose | Criterion |
|---|---|---|
| Fig 1. Positive control | Public PN40024 long reads reproduce NC_012119.1. | Assembly graph covers NC_012119.1 (773,279 bp) at a preregistered identity and coverage; differences explained by repeat-mediated configurations are listed, not counted as errors. |
| Table 1. Mitochondrial catalogue | Resource. | Each accession: graph, configurations, gene and tRNA annotation, plastid-derived segments; read support for each repeat junction. |
| Fig 2. NUMT and NUPT masks on PN_T2T | Masking reduces false organelle-like heterozygous calls in nuclear variant sets. | Compare calls in masked and unmasked runs on DS10 samples. |
| Fig 3. Maternal phylogeny (optional) | Organelle trees differ from nuclear trees where hybrid origin is known. | Trees with support values; comparison with the nuclear tree. |
| Fig 4. Heteroplasmy (optional) | Minor-allele sites remain after NUMT reads are filtered out. | Only sites above a preregistered depth and fraction that are absent from the nuclear mask. |

## Preregistration

Before any data are analysed, fill in [`docs/PREREGISTRATION.md`](../../../../templates/PREREGISTRATION.md) for this project: hypotheses, primary outcome, sample inclusion rules, thresholds, stop rules and what will be reported if a hypothesis fails. Commit it with a date. Criteria from any earlier attempt are reference only and are not carried over.

## Data

| Module | Dataset |
|---|---|
| [DS01](../../data/DS01-pn40024-references/) | PN40024 references: PN_T2T (v5), PN40024.v4 and 12X |
| [DS02](../../data/DS02-grapepan-v1/) | Grapepan v1.0: T2T haplotypes, graphs and a 466-accession resequencing panel |
| [DS03](../../data/DS03-vitis-super-pangenome-72/) | Vitis super-pangenome: 72 haplotype-resolved accessions |
| [DS08](../../data/DS08-muscadinia-genomes/) | Muscadinia rotundifolia assemblies and reads |
| [DS10](../../data/DS10-reseq-472-vitis/) | Resequencing of 472 Vitis accessions (and the 2017 domestication panel) |
| [DS16](../../data/DS16-vitaceae-assembly-index/) | Index of all Vitaceae assemblies in NCBI |

PN40024 long reads (DS01) are used for the pilot; DS10 short reads for the mask test. Positive control: RefSeq NC_012119.1. Public organelle records (RefSeq and INSDC) are listed from DS16 [待确认: complete list]. The 33-accession pan-mitogenome sequences may be added to a data module only after their accessions are confirmed [待确认]. New public data: none needed.

## Analysis steps

Shared modules, in order:

1. [AM01 · Download and verify](../../analyses/AM01-download-and-verify/)
2. [AM05 · Assembly QC](../../analyses/AM05-assembly-qc/)
3. [AM06 · Whole-genome alignment, synteny and SVs from assemblies](../../analyses/AM06-wga-and-sv/)
4. [AM03 · Short-read mapping and small-variant calling](../../analyses/AM03-short-read-variants/)

**Stepwise work plan with tools**

| Step | Work | Tools (paper) | Output |
|---|---|---|---|
| 1 | Inventory public organelle records and long-read sets | DS16, AM01 | Inventory table |
| 2 | Pilot: assemble PN40024 and two DS02 accessions; compare with NC_012119.1 | Oatk, PMAT, Flye with graph inspection | Fig 1 |
| 3 | Scale to other public long-read sets; annotate genes, tRNAs, rRNAs, repeats, plastid-derived segments | Oatk or PMAT; annotation tools [待确认] | Table 1 |
| 4 | Align organelle sequences to PN_T2T; build NUMT and NUPT masks with depth and synteny checks | minimap2 (AM06) | Masks |
| 5 | Nuclear calls with and without masks | AM03 | Fig 2 |
| 6 | Optional: maternal phylogeny; heteroplasmy after mask filtering | IQ-TREE 2; custom pileup | Fig 3, Fig 4 |

## Expected results and how they will be read

- Fig 1: failure on the positive control stops the scale-up; tool settings are changed only under a written deviation.
- Table 1 complements the 33-accession pan-mitogenome by keeping graphs and configurations; overlap with that study is reported per accession.
- Fig 2: fewer organelle-like heterozygous calls after masking would make the masks useful to the nuclear projects; no change is also reported.
- Fig 4 is reported only if sites pass the NUMT filter; minor-allele sites near NUMTs are treated as artefacts by default.

## Paper design and split

| Paper | Working title | Type | Figures |
|---|---|---|---|
| O1 | Grape mitochondrial assembly graphs and organelle-derived nuclear masks on PN_T2T | data note or short paper | Fig 1–2, Table 1 |
| O2 | Maternal lineages and heteroplasmy in grape (only if O1 passes) | follow-up | Fig 3–4 |

Each paper: introduction from the gap above; one results section per figure; methods with tool versions from the modules; data availability listing every accession used and the derived tables.

## Risks and novelty check

- Risk: The 33-accession pan-mitogenome covers much of (a); novelty rests on graphs, masks and heteroplasmy.
- Risk: NUMT reads mimic heteroplasmy; filtering must come first.
- Risk: Which assembly tools install on the compute site is open [待确认].
- Novelty: checked against the existing work above (Crossref-verified DOIs). Repeat the search before writing; anything marked [待确认] is not yet verified.

## Rough estimates

- Compute: small to medium [draft]
- Effort: 6–10 weeks for one person [draft]
- Target: plant genomics or organelle genetics journal [draft]

## Suggested journal level (suggestion only)

**Specialty journal (plant genomics or organelle biology).** Grape organelle papers read here appeared in *Molecular Biology and Evolution*, *BMC Evolutionary Biology*, *Microbiology Resource Announcements* and *Journal of Integrative Plant Biology*; organelle tool papers in *Genome Biology* and *Horticulture Research*. With the 33-accession pan-mitogenome already published, a graph and mask resource fits a specialty venue. This is a suggestion, not a decision; impact factors are not used.

## Continue on HPC

Run each step as its own job, in this order. Every job writes `.DONE` or `.FAILED` and a log; the next step starts only after `.DONE`. Template and rules: [`docs/HPC_JOBS.md`](../../../../templates/HPC_JOBS.md).

| Order | Step | Main tools | Resources (rough) |
|---|---|---|---|
| 1 | [AM01](../../analyses/AM01-download-and-verify/) Download and verify | ncbi-datasets-cli, sra-tools, ENA FTP / Aspera | 1–4 CPU, 4 GB, network; array over files |
| 2 | Organelle assembly | Oatk, PMAT, Flye | 16 CPU, 64 GB per accession; array |
| 3 | [AM06](../../analyses/AM06-wga-and-sv/) Alignment to PN_T2T and masks | minimap2 | 8 CPU, 32 GB |
| 4 | [AM03](../../analyses/AM03-short-read-variants/) Masked and unmasked nuclear calls | bwa-mem2, GATK or DeepVariant | 16 CPU, 64 GB per sample; array |

Public inputs: [DS01](../../data/DS01-pn40024-references/), [DS02](../../data/DS02-grapepan-v1/), [DS03](../../data/DS03-vitis-super-pangenome-72/), [DS08](../../data/DS08-muscadinia-genomes/), [DS10](../../data/DS10-reseq-472-vitis/), [DS16](../../data/DS16-vitaceae-assembly-index/).

## References

- Bi et al. 2024. PMAT: an efficient plant mitogenome assembly toolkit using low-coverage HiFi sequencing data. *Horticulture Research*. [doi:10.1093/hr/uhae023](https://doi.org/10.1093/hr/uhae023)
- Frommer et al. 2020. Genome Sequences of Both Organelles of the Grapevine Rootstock Cultivar ‘Börner’. *Microbiology Resource Announcements*. [doi:10.1128/mra.01471-19](https://doi.org/10.1128/mra.01471-19)
- Goremykin et al. 2008. Mitochondrial DNA of Vitis vinifera and the Issue of Rampant Horizontal Gene Transfer. *Molecular Biology and Evolution*. [doi:10.1093/molbev/msn226](https://doi.org/10.1093/molbev/msn226)
- Gualberto et al. 2017. Plant Mitochondrial Genomes: Dynamics and Mechanisms of Mutation. *Annu Rev Plant Biol*. [doi:10.1146/annurev-arplant-043015-112232](https://doi.org/10.1146/annurev-arplant-043015-112232)
- Hou et al. 2025. The cytonuclear interactions during grapevine domestication. *Journal of Integrative Plant Biology*. [doi:10.1111/jipb.13968](https://doi.org/10.1111/jipb.13968)
- Jansen et al. 2006. Phylogenetic analyses of Vitis (Vitaceae) based on complete chloroplast genome sequences: effects of taxon sampling and phylogenetic methods on resolving relationships among rosids. *BMC Evolutionary Biology*. [doi:10.1186/1471-2148-6-32](https://doi.org/10.1186/1471-2148-6-32)
- Jin et al. 2020. GetOrganelle: a fast and versatile toolkit for accurate de novo assembly of organelle genomes. *Genome Biology*. [doi:10.1186/s13059-020-02154-5](https://doi.org/10.1186/s13059-020-02154-5)
- Kolmogorov et al. 2019. Assembly of long, error-prone reads using repeat graphs. *Nature Biotechnology*. [doi:10.1038/s41587-019-0072-8](https://doi.org/10.1038/s41587-019-0072-8)
- Kozik et al. 2019. The alternative reality of plant mitochondrial DNA: One ring does not rule them all. *PLOS Genetics*. [doi:10.1371/journal.pgen.1008373](https://doi.org/10.1371/journal.pgen.1008373)
- Michalovova et al. 2013. Analysis of plastid and mitochondrial DNA insertions in the nucleus (NUPTs and NUMTs) of six plant species: size, relative age and chromosomal localization. *Heredity*. [doi:10.1038/hdy.2013.51](https://doi.org/10.1038/hdy.2013.51)
- Sloan et al. 2012. Rapid Evolution of Enormous, Multichromosomal Genomes in Flowering Plant Mitochondria with Exceptionally High Mutation Rates. *PLoS Biology*. [doi:10.1371/journal.pbio.1001241](https://doi.org/10.1371/journal.pbio.1001241)
- Zhou et al. 2025. Oatk: a de novo assembly tool for complex plant organelle genomes. *Genome Biology*. [doi:10.1186/s13059-025-03676-6](https://doi.org/10.1186/s13059-025-03676-6)
