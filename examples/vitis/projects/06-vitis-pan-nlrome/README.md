# 06. A genus-wide NLR catalogue with integrated domains and collapse checks

中文：带塌缩核查和整合结构域的葡萄属泛 NLR 组

Rank 6 of 22 (score F 3 + N 2 + E 2 = 7; see docs/RANKING.md) · Tier: Medium (E = 2, effort range ending after 6 weeks and by 4 months) · Origin: continued: started earlier and restarted here from public data under a new preregistration · Status: draft v0.3.2, 2026-11-14

## Gap

NLR genes were catalogued for single references, selected loci, or within one pangenome. A catalogue across the whole genus, with integrated decoy domains and checks for collapsed arrays, was not found.

**Existing work**

- [Guo et al. 2025](https://doi.org/10.1038/s41588-025-02111-7): resistance genes from the Vitis super-pangenome.
- [Massonnet et al. 2022](https://doi.org/10.1093/g3journal/jkac148): haplotype-resolved powdery mildew resistance loci in Muscadinia.
- [Van de Weyer et al. 2019](https://doi.org/10.1016/j.cell.2019.07.038): pan-NLRome method in Arabidopsis.

**How this project differs**

One annotation pipeline across lineages, read-depth checks for collapsed NLR clusters, and integrated-domain discovery.

**Background survey (literature read for this plan)**

Plant NLR immune receptors are the main class of cloned resistance genes ([Kourelis and van der Hoorn 2018](https://doi.org/10.1105/tpc.17.00579)). Some NLRs carry extra domains that act as integrated decoys for pathogen effectors; comparative surveys found such domains widely across plant genomes ([Sarris et al. 2016](https://doi.org/10.1186/s12915-016-0228-7); [Kroj et al. 2016](https://doi.org/10.1111/nph.13869)). At species scale, the *Arabidopsis* pan-NLRome largely saturates with about 40 well-chosen wild accessions, with half of the pan-NLRome present in most accessions ([Van de Weyer et al. 2019](https://doi.org/10.1016/j.cell.2019.07.038)), and an analysis of 62 accessions found a subset of highly variable NLRs whose variable residues predict binding sites ([Prigozhin and Krasileva 2021](https://doi.org/10.1093/plcell/koab013)). NLR-Annotator ([Steuernagel et al. 2020](https://doi.org/10.1104/pp.19.01273)) and the RefPlantNLR collection of experimentally validated receptors ([Kourelis et al. 2021](https://doi.org/10.1371/journal.pbio.3001124)) give standard annotation and benchmarks.

In grape, NBS-LRR genes were catalogued in the reference and linked to powdery mildew response ([Goyal et al. 2020](https://doi.org/10.1016/j.ygeno.2019.02.011)). Cloned resistance loci come mostly from *Muscadinia*: the MrRUN1/MrRPV1 TIR-NB-LRR locus ([Feechan et al. 2013](https://doi.org/10.1111/tpj.12327)), haplotype-resolved Run1.2 and Run2.2 loci ([Massonnet et al. 2022](https://doi.org/10.1093/g3journal/jkac148)) and the Rpv2 NLR cluster specific to *V. rotundifolia* ([Marsan et al. 2025](https://doi.org/10.1007/s00122-025-04959-z)). The *Vitis* super-pangenome and the North American super-pangenome both described resistance genes across many haplotypes ([Guo et al. 2025](https://doi.org/10.1038/s41588-025-02111-7); [Cochetel et al. 2023](https://doi.org/10.1186/s13059-023-03133-2)), and the *Muscadinia* assembly showed expansion of resistance genes ([Cochetel et al. 2021](https://doi.org/10.1093/g3journal/jkab033)).

**Specific gap.** No genus-wide NLR catalogue with one annotation pipeline across cultivated, wild Eurasian, North American, East Asian *Vitis* and *Muscadinia*, with integrated-domain discovery and read-depth checks of clustered arrays, was found [待确认].

## Question

How large is the grape NLR repertoire across lineages, which integrated domains occur, and does the repertoire saturate?

## Hypotheses, planned figures and criteria

No results are given here. Each row says what would count as support; the exact thresholds go into the preregistration.

| Figure or table | Hypothesis or purpose | Criterion |
|---|---|---|
| Fig 1. NLR count per haplotype before and after collapse checks | Raw counts underestimate clustered NLRs. | Read-depth ratio over clusters; a cluster is flagged when depth exceeds the preregistered multiple of the genome median. |
| Fig 2. Integrated domains by lineage | Some integrated domains are lineage-specific. | A domain is counted only if found in at least two haplotypes of the lineage; the number of haplotypes per lineage is reported because small lineages have a lower chance of passing. |
| Fig 3. Saturation curves by lineage | At equal numbers of haplotypes, the cultivated repertoire is closer to saturation than wild lineages. | Orthogroup accumulation compared at the same number of haplotypes per lineage (rarefied), with bootstrap resampling by accession. |

**Expected results and how they will be read**

- Fig 1: if counts rise after collapse correction, raw pangenome NLR counts are lower bounds; the size of the correction per lineage is reported.
- Fig 2: integrated domains found in one lineage only are listed as candidates for lineage-specific effector recognition; no function is claimed.
- Fig 3: saturation curves at equal numbers of haplotypes show whether more wild sampling would add many new orthogroups; if cultivated grapes saturate earlier, that is read as reduced diversity, not as fewer genes in the genus.

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
| [DS08](../../data/DS08-muscadinia-genomes/) | Muscadinia rotundifolia assemblies and reads |

**How each dataset is used**

| Module | Role in this project |
|---|---|
| DS01 | PN_T2T NLR set as anchor |
| DS02, DS03 | Cultivated and wild *Vitis* haplotypes |
| DS04 | North American species haplotypes |
| DS06 | *V. amurensis* haplotypes (East Asian lineage) |
| DS08 | *Muscadinia* haplotypes carrying cloned loci (positive controls) |

New public data: none needed. Long reads for collapse checks exist for some haplotypes only [待确认 per accession].

## Analysis steps

Shared modules, in order:

1. [AM01 · Download and verify](../../analyses/AM01-download-and-verify/)
2. [AM05 · Assembly QC](../../analyses/AM05-assembly-qc/)
3. [AM08 · Gene-family search across haplotypes](../../analyses/AM08-gene-family-annotation/)
4. [AM09 · Gene presence/absence and copy number](../../analyses/AM09-gene-pav-and-cnv/)
5. [AM18 · Long-read SV calling](../../analyses/AM18-long-read-sv/)

Project-specific steps:

- Annotate NLRs with miniprot, HMMER and InterProScan (AM08).
- Check clusters with long-read depth (AM18) where reads exist.
- Cluster into orthogroups; list integrated domains; build saturation curves.

**Stepwise work plan with tools**

| Step | Work | Tools (paper) | Output |
|---|---|---|---|
| 1 | Collect haplotypes; QC | AM01, AM05 | Manifest |
| 2 | Annotate NLR loci from genome sequence and from proteins | NLR-Annotator, miniprot, HMMER, InterProScan (AM08) | NLR table per haplotype |
| 3 | Benchmark on cloned grape loci (Run1, Rpv1, Run1.2, Run2.2, Rpv2) and RefPlantNLR | BLASTP | Recall on known genes |
| 4 | Check clustered arrays with long-read depth and k-mer copy number | minimap2, mosdepth (AM18) | Collapse flags and corrected counts |
| 5 | List non-canonical (integrated) domains | InterProScan, Pfam | Domain table |
| 6 | Orthogroups and saturation curves by lineage | OrthoFinder ([Emms and Kelly 2019](https://doi.org/10.1186/s13059-019-1832-y)), R | Fig 3 |

## Paper design and split

| Paper | Working title | Type | Figures |
|---|---|---|---|
| G1 | A genus-wide grape NLR catalogue | main paper | Fig 1–3 |

Each paper: introduction from the gap above; one results section per figure; methods with tool versions from the modules; data availability listing every accession used and the derived tables.

## Risks and novelty check

- Risk: Collapsed clusters remain where long reads are not public.
- Risk: Integrated-domain calls depend on domain database versions.
- Novelty: checked against the existing work above (Crossref-verified DOIs). Repeat the search before writing; anything marked [待确认] is not yet verified.

## Rough estimates

- Compute: medium [draft]
- Effort: 2–3 months for one person [draft]
- Target: plant pathology or genome journal [draft]

## Suggested journal level (suggestion only)

**Mid-field journal (plant pathology or plant genomics).** NLR resource and method papers read here appeared in *Plant Physiology*, *PLOS Biology*, *New Phytologist* and *BMC Biology*; species-wide NLRome studies appeared in *Cell* and *The Plant Cell*; grape resistance-locus papers in *The Plant Journal*, *G3* and *Theoretical and Applied Genetics*. A genus-wide grape catalogue with collapse checks fits a mid-field plant journal; a broad venue would need new biology beyond the catalogue. This is a suggestion, not a decision; impact factors are not used.

## Continue on HPC

Run each step as its own job, in this order. Every job writes `.DONE` or `.FAILED` and a log; the next step starts only after `.DONE`. Template and rules: [`docs/HPC_JOBS.md`](../../../../templates/HPC_JOBS.md).

| Order | Step | Main tools | Resources (rough) |
|---|---|---|---|
| 1 | [AM01](../../analyses/AM01-download-and-verify/) Download and verify | ncbi-datasets-cli, sra-tools, ENA FTP / Aspera | 1–4 CPU, 4 GB, network; array over files |
| 2 | [AM05](../../analyses/AM05-assembly-qc/) Assembly QC | compleasm, BUSCO, Merqury | 16 CPU, 64 GB, 1–3 h per assembly; array |
| 3 | [AM08](../../analyses/AM08-gene-family-annotation/) Gene-family search across haplotypes | miniprot, HMMER, InterProScan | 16 CPU, 32 GB, < 2 h per haplotype |
| 4 | [AM09](../../analyses/AM09-gene-pav-and-cnv/) Gene presence/absence and copy number | Liftoff, OrthoFinder, mosdepth | 8 CPU, 32 GB per haplotype |
| 5 | [AM18](../../analyses/AM18-long-read-sv/) Long-read SV calling | Sniffles2, cuteSV, pbsv | 16 CPU, 64 GB per sample |

Public inputs: [DS01](../../data/DS01-pn40024-references/), [DS02](../../data/DS02-grapepan-v1/), [DS03](../../data/DS03-vitis-super-pangenome-72/), [DS04](../../data/DS04-na-vitis-super-pangenome/), [DS06](../../data/DS06-vitis-amurensis-pangenome/), [DS08](../../data/DS08-muscadinia-genomes/).

## References

- Guo et al. 2025. Super pangenome of Vitis empowers identification of downy mildew resistance genes for grapevine improvement. *Nature Genetics*. [doi:10.1038/s41588-025-02111-7](https://doi.org/10.1038/s41588-025-02111-7)
- Massonnet et al. 2022. Haplotype-resolved powdery mildew resistance loci reveal the impact of heterozygous structural variation on NLR genes in Muscadinia rotundifolia. *G3 Genes|Genomes|Genetics*. [doi:10.1093/g3journal/jkac148](https://doi.org/10.1093/g3journal/jkac148)
- Van de Weyer et al. 2019. A Species-Wide Inventory of NLR Genes and Alleles in Arabidopsis thaliana. *Cell*. [doi:10.1016/j.cell.2019.07.038](https://doi.org/10.1016/j.cell.2019.07.038)
- Cochetel et al. 2021. Diploid chromosome-scale assembly of the Muscadinia rotundifolia genome supports chromosome fusion and disease resistance gene expansion during Vitis and Muscadinia divergence. *G3 Genes|Genomes|Genetics*. [doi:10.1093/g3journal/jkab033](https://doi.org/10.1093/g3journal/jkab033)
- Cochetel et al. 2023. A super-pangenome of the North American wild grape species. *Genome Biology*. [doi:10.1186/s13059-023-03133-2](https://doi.org/10.1186/s13059-023-03133-2)
- Emms et al. 2019. OrthoFinder: phylogenetic orthology inference for comparative genomics. *Genome Biology*. [doi:10.1186/s13059-019-1832-y](https://doi.org/10.1186/s13059-019-1832-y)
- Feechan et al. 2013. Genetic dissection of a TIR ‐ NB ‐ LRR locus from the wild N orth A merican grapevine species M uscadinia rotundifolia identifies paralogous genes conferring resistance to major fungal and oomycete pathogens in cultivated grapevine. *The Plant Journal*. [doi:10.1111/tpj.12327](https://doi.org/10.1111/tpj.12327)
- Goyal et al. 2020. Genome-wide characterization revealed role of NBS-LRR genes during powdery mildew infection in Vitis vinifera. *Genomics*. [doi:10.1016/j.ygeno.2019.02.011](https://doi.org/10.1016/j.ygeno.2019.02.011)
- Kourelis et al. 2018. Defended to the Nines: 25 Years of Resistance Gene Cloning Identifies Nine Mechanisms for R Protein Function. *The Plant Cell*. [doi:10.1105/tpc.17.00579](https://doi.org/10.1105/tpc.17.00579)
- Kourelis et al. 2021. RefPlantNLR is a comprehensive collection of experimentally validated plant disease resistance proteins from the NLR family. *PLOS Biology*. [doi:10.1371/journal.pbio.3001124](https://doi.org/10.1371/journal.pbio.3001124)
- Kroj et al. 2016. Integration of decoy domains derived from protein targets of pathogen effectors into plant immune receptors is widespread. *New Phytologist*. [doi:10.1111/nph.13869](https://doi.org/10.1111/nph.13869)
- Marsan et al. 2025. Rpv2 is part of a cluster of NLRs specific to Vitis rotundifolia and confers total resistance to grapevine downy mildew. *Theoretical and Applied Genetics*. [doi:10.1007/s00122-025-04959-z](https://doi.org/10.1007/s00122-025-04959-z)
- Prigozhin et al. 2021. Analysis of intraspecies diversity reveals a subset of highly variable plant immune receptors and predicts their binding sites. *The Plant Cell*. [doi:10.1093/plcell/koab013](https://doi.org/10.1093/plcell/koab013)
- Sarris et al. 2016. Comparative analysis of plant immune receptor architectures uncovers host proteins likely targeted by pathogens. *BMC Biology*. [doi:10.1186/s12915-016-0228-7](https://doi.org/10.1186/s12915-016-0228-7)
- Steuernagel et al. 2020. The NLR-Annotator Tool Enables Annotation of the Intracellular Immune Receptor Repertoire. *Plant Physiology*. [doi:10.1104/pp.19.01273](https://doi.org/10.1104/pp.19.01273)
