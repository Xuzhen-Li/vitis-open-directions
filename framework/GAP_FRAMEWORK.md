# Gap framework: six dimensions for one species

Written 2026-11-21 (UTC+8). [中文](GAP_FRAMEWORK.zh.md)

This page describes how to find, test and rank open research gaps in one species using public data only. It is written so that it can be used for any species. The grapevine pages in [examples/vitis/](../examples/vitis/) are the worked example; each dimension below names the grapevine projects that show it in practice. Scoring rules are in [EVALUATION_RUBRIC.md](EVALUATION_RUBRIC.md); the steps for a new species are in [SPECIES_TRANSFER_GUIDE.md](SPECIES_TRANSFER_GUIDE.md).

## Four checks for every candidate gap

No analysis starts until a candidate gap has passed all four:

1. **Literature.** The gap is checked against papers whose DOI record (Crossref or DataCite) or full text was opened. That a paper is not mentioned in this repository is not evidence that the work has not been done. A DOI or claim that was not opened is marked [to confirm].
2. **Public data.** Inputs are checked through archive APIs (ENA filereport, NCBI Datasets, Zenodo API), not only from what a paper says. Each input gets one status: `available` (the API lists the files), `portal` (web search only, no closed file list), `blocked` (an access check or an empty list) or `not found`. There must be a first closed subset that runs without private access.
3. **Preregistration.** Hypotheses, controls, pass lines and statistical tests are written in [templates/PREREGISTRATION.md](../templates/PREREGISTRATION.md) before any main result is looked at.
4. **Stop rules.** The condition under which the work stops, or falls back to a smaller paper, is written down in advance.

Each candidate is recorded with [templates/GAP_AUDIT_TEMPLATE.md](../templates/GAP_AUDIT_TEMPLATE.md).

## Why these six dimensions

Data and resources are the base; the other five dimensions are biological: genome structure and organelles; variation and mobile elements; population, domestication and reproductive system; expression, regulation and epigenetics; phenotype, function and cross-species comparison. In plant genomes such as grapevine, repeat arrays (telomeres, rDNA, centromeres), organelle genomes and transposable elements (TEs) are separate bottlenecks for assembly and for methods, and the reproductive system (clonal propagation, the shift from separate sexes to hermaphrodite flowers) decides whether population statistics and dating calibrations work. The same split can be used for any plant or animal species with a reference genome, a resequenced population and public transcriptomes.

For each dimension the four questions are the same: what to search for, whether the gap is real, whether it is worth doing, and whether public data are enough.

## 1. Data and resources (the base)

- **Search.** List the assemblies, resequencing, long-read, RNA-seq, epigenome and phenotype data for the species in INSDC (NCBI, ENA, DDBJ), NGDC, GEO, Zenodo, figshare and the species portals. Look for samples repeated across studies, clonal redundancy, fragmented coordinate systems and missing metadata.
- **Is the gap real?** Do not stop at a paper saying that a panel exists. Test through the APIs whether accessions resolve, whether file lists can be read, and whether access is blocked or links are dead. Check whether one sample identity table and one de-duplicated baseline exist across panels.
- **Is it worth doing?** Infrastructure gaps have high value when several population, graph or QTL projects depend on the same sample pool or reference coordinates; they have low priority when they serve one side question.
- **Public data enough?** Classify every input with the four status words above, and require a first closed subset that runs without private access.
- **Grapevine example:** [data/DOWNLOADS.md](../examples/vitis/data/DOWNLOADS.md), [data/README.md](../examples/vitis/data/README.md), [DEFAULTS.md](../examples/vitis/DEFAULTS.md), project [08](../examples/vitis/projects/08-harmonised-sample-panel/).

## 2. Genome structure and organelles

- **Search.** Scan the genome region by region: telomeres and interstitial telomeric repeats (ITS), 45S and 5S rDNA, centromeric satellites and chromosome fusion points, synteny and gene-family copy number between haplotypes, and the mitochondrial and plastid genomes with nuclear insertions of organelle DNA (NUMT, NUPT) and heteroplasmy.
- **Is the gap real?** Check whether single-genome T2T papers and pangenome papers describe one reference only and lack a uniform comparison across haplotypes or genera. Check also for gaps where a technical artefact may have been read as biology: missed annotations giving false gene presence/absence, or collapsed assemblies giving false copy-number variation in resistance genes.
- **Is it worth doing?** Prefer questions that separate real evolution from assembly or annotation artefacts, or that give the nuclear analyses of the whole species a mask (a NUMT mask, centromere coordinates).
- **Public data enough?** Check whether the number of near-complete haplotypes gives enough power. For example, with 9 genomes of which 2 are outgroups, the smallest exact permutation p-value is 1/36, which is too coarse. Check whether validation data (long reads from the same BioSample, CENH3 ChIP-seq) cover the target taxa.
- **Grapevine example:** projects [01](../examples/vitis/projects/01-telomere-and-interstitial-telomeric-repeats/), [02](../examples/vitis/projects/02-rdna-arrays/), [05](../examples/vitis/projects/05-gene-pav-across-pangenomes/), [06](../examples/vitis/projects/06-vitis-pan-nlrome/), [07](../examples/vitis/projects/07-metabolic-gene-families/), [18](../examples/vitis/projects/18-vitis-muscadinia-centromeres/), [26](../examples/vitis/projects/26-mitochondrial-genomes/STATUS.md).

## 3. Variation and mobile elements

- **Search.** Cover variation beyond SNPs and indels: structural variants (SVs) on graph pangenomes, large inversions, TE insertion polymorphisms and solo-LTRs, endogenous viral elements, and clonal or somatic mutation spectra.
- **Is the gap real?** Check whether existing work is limited to a linear reference (with reference bias) or to one wild or one cultivated group.
- **Is it worth doing?** Ask whether the change of method (from a linear to a graph reference, from single samples to population genotyping) can change the biological conclusion, for example by separating sexually inherited hemizygous SVs from those that arose during clonal propagation. A change of tool alone is not enough.
- **Public data enough?** Check for long reads to validate breakpoints, a suitable outgroup for polarisation, family trios to separate inherited from new variants, and whether the key tools install on the cluster.
- **Grapevine example:** projects [03](../examples/vitis/projects/03-endogenous-florendoviruses/), [13](../examples/vitis/projects/13-somatic-mutation-spectra-across-cultivars/), [14](../examples/vitis/projects/14-te-insertion-polymorphisms-cultivated/), [16](../examples/vitis/projects/16-graph-sv-load/), [17](../examples/vitis/projects/17-large-inversions-in-populations/), [25](../examples/vitis/projects/25-te-annotation-methods/STATUS.md).

## 4. Population, domestication and reproductive system

- **Search.** Parentage and pedigree QC, pedigree and linkage-disequilibrium recombination maps, ancestral recombination graphs (ARGs) and allele dating, introgression on a graph and painting of hybrid cultivars, evolution of the sex-determining region, and graph mapping and imputation of ancient DNA.
- **Is the gap real?** Keep "done on a linear reference" apart from "not done on a graph or at SV level". Keep different statistics apart: a pedigree recombination rate is not a historical LD-based rate.
- **Is it worth doing?** Where a basic methodological barrier exists (for example clonal propagation breaking the calibration of ARG dating), set a methods-paper fallback in advance. Where published work already covers the core question and the remaining gap depends on scarce phenotype or sex records, downgrade the direction.
- **Public data enough?** Check for a de-duplicated sample pool without clones, public families or trios that can be verified, ancient DNA accessions whose raw reads were checked one by one, and complete donor panels.
- **Grapevine example:** projects [08](../examples/vitis/projects/08-harmonised-sample-panel/), [10](../examples/vitis/projects/10-arg-domestication-timing/), [15](../examples/vitis/projects/15-graph-introgression/), [20](../examples/vitis/projects/20-ancient-seeds-on-graph/), [22](../examples/vitis/projects/22-sex-region-population-level/), [23](../examples/vitis/projects/23-family-parentage/STATUS.md), [24](../examples/vitis/projects/24-recombination-maps/STATUS.md).

## 5. Expression, regulation and epigenetics

- **Search.** A uniform re-analysis of public RNA-seq on the newest reference (expression atlas, splicing, eQTL and sQTL, allele-specific expression), small RNA and phasiRNA, DNA methylation, 3D genome (Hi-C, TADs), and sequence-to-expression models.
- **Is the gap real?** Check whether existing expression platforms and single-study eQTL work use an older reference or lack sQTL, and whether recent papers already cover the epigenetic and 3D-genome directions.
- **Is it worth doing?** Prefer resource work that gives models and genetic mapping a common base (for example a T2T expression atlas that feeds sequence-to-expression models), and split it by risk into separate outputs (the atlas apart from the QTL work).
- **Public data enough?** Check whether genotype, tissue and study are so confounded that QTL mapping is not possible; whether public methylome or single-cell sample sizes support population analysis (if not, list the direction as not kept); and whether GPUs and leakage-proof data splits (by chromosome and by gene family) are available.
- **Grapevine example:** projects [11](../examples/vitis/projects/11-sequence-to-function-models/), [19](../examples/vitis/projects/19-public-rnaseq-on-t2t/); directions left out are in [NOT_KEPT.md](../examples/vitis/NOT_KEPT.md).

## 6. Phenotype, function and cross-species comparison

- **Search.** Graph genotyping of single key agronomic loci, meta-analysis of public GWAS and cross-ancestry genomic prediction, SV marker panels, convergent domestication across crops, and discovery of pathogens and viruses in unmapped public reads.
- **Is the gap real?** Check whether a classic locus has already been studied many times (then novelty is low), and whether a functional gap in fact needs wet-lab work.
- **Is it worth doing?** Where phenotypes depend on outside databases, make an inventory of public phenotypes and summary statistics a hard stop gate. For cross-species work, confirm that the null model and the definition of orthologous groups are sound.
- **Public data enough?** Check whether phenotypes and GWAS summary statistics are public in a machine-readable form (not only inside a PDF), and whether the raw FASTQ files of every panel in a cross-crop comparison are in ENA and can be down-sampled to matching sizes.
- **Grapevine example:** projects [04](../examples/vitis/projects/04-virus-discovery-in-public-data/), [09](../examples/vitis/projects/09-berry-colour-locus-graph/), [12](../examples/vitis/projects/12-convergent-domestication-cross-crop/), [21](../examples/vitis/projects/21-gwas-meta-and-cross-ancestry-prediction/).

## Possible gaps outside the current grapevine projects [to confirm]

Two candidates were named on 2026-11-21 and have not had a literature search. Each needs a filled [gap audit](../templates/GAP_AUDIT_TEMPLATE.md) with Crossref searches before it is added:

- Plastid pangenome and cytonuclear interaction, analysed together with the mitochondrial genome [to confirm].
- Evolution of protein structure across haplotypes, using structure prediction to look for structural variants of proteins or new functions [to confirm].

## When this framework changes

After any change to `framework/` or `templates/`, rerun the relative-link check and the public-text screen described in [examples/vitis/CHECK.md](../examples/vitis/CHECK.md).
