# 19. Public RNA-seq on PN_T2T: expression atlas, eQTL/sQTL and allele-specific expression

中文：公开 RNA-seq 在 T2T 上重算：表达图谱、eQTL/sQTL 与等位特异表达

Rank 19 of 22 (score F 2 + N 2 + E 2 = 6; see docs/RANKING.md) · Tier: Medium (E = 2, effort range ending after 6 weeks and by 4 months) · Origin: new · Status: draft v0.3.2, 2026-11-14

## Gap

Grape expression atlases were built on older references, and eQTL studies are small or tied to one condition. Splicing QTL were not found for grape. A multi-tissue pan-eQTL on graph genotypes is limited by the lack of matched genotypes and expression.

**Existing work**

- [Fasoli et al. 2012](https://doi.org/10.1105/tpc.112.100230): grape expression atlas (microarray).
- [Djari et al. 2024](https://doi.org/10.1073/pnas.2403750121): VitExpress transcriptomic platform.
- [Guo et al. 2025](https://doi.org/10.1038/s41588-025-02111-7): SV-eQTL in 113 accessions under downy mildew infection.
- [Martínez-García et al. 2022](https://doi.org/10.1038/s41598-022-11689-5): cis-eQTL from RNA-seq during ripening.
- [Huang et al. 2013](https://doi.org/10.1016/j.plantsci.2013.02.011): eQTL in a mapping population.
- [Cochetel et al. 2025](https://doi.org/10.1186/s13059-025-03858-2): phased epigenomics in a Cabernet Sauvignon trio.

**How this project differs**

Uniform re-quantification on PN_T2T with one fixed annotation, sQTL within single-study, single-tissue subsets, and ASE on WASP-filtered alignments with DNA-phased heterozygous sites, using genotype × tissue as the unit.

## Question

What does a uniform T2T expression atlas show, are sQTL detectable in grape, and how common is allele-specific expression in heterozygous cultivars?

## Hypotheses, planned figures and criteria

No results are given here. Each row says what would count as support; the exact thresholds go into the preregistration.

| Figure or table | Hypothesis or purpose | Criterion |
|---|---|---|
| Fig 1. Atlas on PN_T2T | Not a hypothesis: resource. | Every run traceable to its accession and to the fixed annotation (DS01); a study × tissue collinearity matrix is reported, and comparisons are made within strata rather than by regressing out study. |
| Fig 2. cis-eQTL and sQTL | sQTL are detectable at a preregistered FDR. | Unit: genotype × tissue; primary eQTL and sQTL analyses use only samples with DNA genotypes, while RNA-seq genotypes enter a sensitivity run only; clones merged using AM04 thresholds; mapping performed only within one study and one tissue, combined across studies by meta-analysis; genetic PCs plus a kinship-aware deduplicated sensitivity run; number of hidden factors set by a sample-size rule in advance; gene-level permutation (beta approximation) followed by Storey q-values, with sQTL at the intron-cluster level; minimum genotypes per tissue fixed in advance, below which the tissue is descriptive only. |
| Fig 3. ASE across cultivars | ASE genes overlap known SVs more than expected. | ASE computed only from WASP-filtered STAR alignments to PN_T2T with heterozygous sites called and phased from DNA of the same genotype; residual reference bias estimated on the trio; beta-binomial test with overdispersion and gene-level BH; genes matched by expression, number of heterozygous sites, gene length, and mappability. |

## Preregistration

Before any data are analysed, fill in [`docs/PREREGISTRATION.md`](../../../../templates/PREREGISTRATION.md) for this project: hypotheses, primary outcome, sample inclusion rules, thresholds, stop rules and what will be reported if a hypothesis fails. Commit it with a date. Criteria from any earlier attempt are reference only and are not carried over.

## Data

| Module | Dataset |
|---|---|
| [DS15](../../data/DS15-rnaseq-public-vitis/) | Public Vitis RNA-seq and the expression atlas |
| [DS01](../../data/DS01-pn40024-references/) | PN40024 references: PN_T2T (v5), PN40024.v4 and 12X |
| [DS02](../../data/DS02-grapepan-v1/) | Grapepan v1.0: T2T haplotypes, graphs and a 466-accession resequencing panel |
| [DS10](../../data/DS10-reseq-472-vitis/) | Resequencing of 472 Vitis accessions (and the 2017 domestication panel) |
| [DS18](../../data/DS18-methylome-and-trio/) | Public grape methylomes and a phased Cabernet Sauvignon trio |

## Analysis steps

Shared modules, in order:

1. [AM01 · Download and verify](../../analyses/AM01-download-and-verify/)
2. [AM02 · Read QC and trimming](../../analyses/AM02-read-qc/)
3. [AM04 · Sample identity, clones and relatedness](../../analyses/AM04-sample-identity/)
4. [AM03 · Short-read mapping and small-variant calling](../../analyses/AM03-short-read-variants/)
5. [AM26 · Phasing, ancestral states and recombination rates](../../analyses/AM26-phasing-polarisation-recombination/)
6. [AM15 · RNA-seq quantification and allele-specific expression](../../analyses/AM15-rnaseq-quant-and-ase/)
7. [AM21 · eQTL and splicing QTL](../../analyses/AM21-eqtl-and-sqtl/)

Project-specific steps:

- Curate metadata (DS15); assign each run to a genotype with AM04 (using DNA genotypes from DS02/DS10 where the genotype is in a panel).
- Fix the annotation (DS01: RefSeq GCF_030704535.1-RS_2023_09 by default); build transcripts.fa, tx2gene, and a gene ID map to v4/12X.
- Atlas: salmon + tximport (AM15). Splicing and ASE: STAR with WASP and XS tags (AM15).
- Genotypes from DNA; RNA-seq genotypes used only for samples without DNA, checked for concordance and included only in the sensitivity run; map eQTL and sQTL within study × tissue subsets (AM21).
- Count allele-specific reads on WASP-passed reads at DNA-phased sites (the phasing part of AM26 only; per-sample heterozygous VCFs extracted for WASP); use the trio (DS18) to estimate residual bias.

## Paper design and split

| Paper | Working title | Type | Figures |
|---|---|---|---|
| S1 | A uniform T2T expression atlas from public RNA-seq | resource paper | Fig 1 |
| S2 | Expression and splicing QTL from public grape RNA-seq | paper | Fig 2 |
| S3 | Allele-specific expression in heterozygous grape cultivars | paper | Fig 3 |

Each paper: introduction from the gap above; one results section per figure; methods with tool versions from the modules; data availability listing every accession used and the derived tables.

## Risks and novelty check

- Risk: Few studies sample many genotypes in one tissue; eQTL power may be low.
- Risk: Study, tissue, and genotype are highly collinear in public data.
- Risk: Metadata are inconsistent.
- Risk: The default annotation may differ from the Grapedia release; gene IDs are mapped rather than assumed equal.
- Novelty: checked against the existing work above (Crossref-verified DOIs). Repeat the search before writing; anything marked [待确认] is not yet verified.

## Rough estimates

- Compute: medium to large [draft]
- Effort: 2–4 months for one person [draft]
- Target: plant genomics journal [draft]

## Continue on HPC

Run each step as its own job, in this order. Every job writes `.DONE` or `.FAILED` and a log; the next step starts only after `.DONE`. Template and rules: [`docs/HPC_JOBS.md`](../../../../templates/HPC_JOBS.md).

| Order | Step | Main tools | Resources (rough) |
|---|---|---|---|
| 1 | [AM01](../../analyses/AM01-download-and-verify/) Download and verify | ncbi-datasets-cli, sra-tools, ENA FTP / Aspera | 1–4 CPU, 4 GB, network node; array over files |
| 2 | [AM02](../../analyses/AM02-read-qc/) Read QC and trimming | fastp, MultiQC, seqkit | 8 CPU, 16 GB, 1–2 h per run; array over runs |
| 3 | [AM04](../../analyses/AM04-sample-identity/) Sample identity, clones and relatedness | plink2, KING, VIVC | 8 CPU, 32 GB, < 2 h |
| 4 | [AM03](../../analyses/AM03-short-read-variants/) Short-read mapping and small-variant calling (DNA) | bwa-mem2, samtools, DeepVariant | 16 CPU, 64 GB, 6–24 h per sample (DeepVariant); joint step 32 CPU, 128 GB |
| 5 | [AM26](../../analyses/AM26-phasing-polarisation-recombination/) Phasing only, then per-sample heterozygous VCFs | SHAPEIT5, bcftools | 8–16 CPU, 32–64 GB per chromosome |
| 6 | [AM15](../../analyses/AM15-rnaseq-quant-and-ase/) RNA-seq quantification and allele-specific expression | salmon, STAR, gffread | 16 CPU, 48 GB per run (STAR); salmon 8 CPU, 16 GB |
| 7 | [AM21](../../analyses/AM21-eqtl-and-sqtl/) eQTL and splicing QTL | tensorQTL, LeafCutter, regtools | 8 CPU, 32 GB; GPU optional for tensorQTL |

Public inputs: [DS15](../../data/DS15-rnaseq-public-vitis/), [DS01](../../data/DS01-pn40024-references/), [DS02](../../data/DS02-grapepan-v1/), [DS10](../../data/DS10-reseq-472-vitis/), [DS18](../../data/DS18-methylome-and-trio/).

## References

- Fasoli et al. 2012. The Grapevine Expression Atlas Reveals a Deep Transcriptome Shift Driving the Entire Plant into a Maturation Program. *The Plant Cell*. [doi:10.1105/tpc.112.100230](https://doi.org/10.1105/tpc.112.100230)
- Djari et al. 2024. Haplotype-resolved genome assembly and implementation of VitExpress, an open interactive transcriptomic platform for grapevine. *Proceedings of the National Academy of Sciences*. [doi:10.1073/pnas.2403750121](https://doi.org/10.1073/pnas.2403750121)
- Guo et al. 2025. Super pangenome of Vitis empowers identification of downy mildew resistance genes for grapevine improvement. *Nature Genetics*. [doi:10.1038/s41588-025-02111-7](https://doi.org/10.1038/s41588-025-02111-7)
- Martínez-García et al. 2022. Bioinformatic approach for the discovery of cis-eQTL signals during fruit ripening of a woody species as grape (Vitis vinifera L.). *Scientific Reports*. [doi:10.1038/s41598-022-11689-5](https://doi.org/10.1038/s41598-022-11689-5)
- Huang et al. 2013. Expression QTL mapping in grapevine—Revisiting the genetic determinism of grape skin colour. *Plant Science*. [doi:10.1016/j.plantsci.2013.02.011](https://doi.org/10.1016/j.plantsci.2013.02.011)
- Cochetel et al. 2025. Phased epigenomics and methylation inheritance in a historical Vitis vinifera hybrid. *Genome Biology*. [doi:10.1186/s13059-025-03858-2](https://doi.org/10.1186/s13059-025-03858-2)
