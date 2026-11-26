# Risks across the project pages

Added 2026-11-26. Each project page now has a section "Risks and how to handle them". This page lists the risks that recur across projects and the single largest risk for each project. Sources cited here were read for this page and their DOIs were checked on Crossref; preprints are marked.

## Risks shared by many projects

| Area | Risk | Check or mitigation |
|---|---|---|
| Data access and licence | INSDC data are free and open ([INSDC 2024](https://doi.org/10.1093/nar/gkae1058)), but some grape resources are not: runs of the 3,525-accession panel (DS11) were blocked on the public listing check, and several licences are still to confirm ([data/DOWNLOADS.md](data/DOWNLOADS.md)). | Plan each project on data marked open in DOWNLOADS.md; treat blocked sets as optional. |
| Clones, synonyms and pedigree | Identical genotypes of grape cultivars persist for centuries ([Noraz et al. 2026](https://doi.org/10.1038/s41467-026-70166-z)); cloning, crossing and selfing all shape grape pedigrees and change heterozygosity and the site frequency spectrum ([Xiao et al. 2025](https://doi.org/10.1038/s41467-025-56817-7)). | Collapse samples to unique genotypes before any population statistic (project 08) and report results with and without the collapse. |
| Reference bias and genome choice | Short and low-coverage reads map better to the reference allele, and the bias is stronger in ancient data ([Günther et al. 2019](https://doi.org/10.1371/journal.pgen.1008302)); graph alignment reduces it ([Koptekin et al. 2025](https://doi.org/10.1186/s13059-024-03462-w)). | Repeat key results on a second reference or on the graph; report allele balance at heterozygous sites. |
| Annotation differences | Gene presence-absence can be inflated by differences in annotation rather than in genomes ([Brůna et al. 2026](https://doi.org/10.1093/nargab/lqag011)). | Re-annotate with one pipeline, or confirm absence at the sequence level. |
| Pooling public data | Studies differ in platform, depth, tissue and sampling design. | Record source, platform and depth per sample and include them as covariates; show that results hold within the largest single source. |
| Computing cost | Graph construction, ARG inference and whole-panel alignment are the expensive steps. | Time one chromosome first, as each project page suggests. |

## Largest risk for each project

| Project | Largest risk | Where to read more |
|---|---|---|
| 01 Telomeres | Long-read technology confounds telomere length; a method from long-read assemblies already exists (preprint). | [01](projects/01-telomere-and-interstitial-telomeric-repeats/README.md#risks-and-how-to-handle-them) |
| 02 rDNA arrays | Few assemblies close the NORs, and copy number is not activity. | [02](projects/02-rdna-arrays/README.md#risks-and-how-to-handle-them) |
| 03 Florendoviruses | A comparative study in *Prunus* is a direct template, so novelty is lower. | [03](projects/03-endogenous-florendoviruses/README.md#risks-and-how-to-handle-them) |
| 04 Virus discovery | Contamination, index hopping and attribution of viruses to the wrong host. | [04](projects/04-virus-discovery-in-public-data/README.md#risks-and-how-to-handle-them) |
| 05 Gene PAV | Annotation-driven inflation of PAV is already shown in general. | [05](projects/05-gene-pav-across-pangenomes/README.md#risks-and-how-to-handle-them) |
| 06 Pan-NLRome | A preprint on 29 Vitaceae assemblies overlaps with the NLR expansion question. | [06](projects/06-vitis-pan-nlrome/README.md#risks-and-how-to-handle-them) |
| 07 Metabolic families | Assemblies can collapse tandem arrays and bias copy number. | [07](projects/07-metabolic-gene-families/README.md#risks-and-how-to-handle-them) |
| 08 Sample panel | The largest panel (DS11) is blocked; synonyms are hard to separate from clones. | [08](projects/08-harmonised-sample-panel/README.md#risks-and-how-to-handle-them) |
| 09 Berry colour locus | Some haplotypes may be missing from the graph; the locus is largely explained. | [09](projects/09-berry-colour-locus-graph/README.md#risks-and-how-to-handle-them) |
| 10 ARG timing | Clonal propagation breaks generation-time calibration. | [10](projects/10-arg-domestication-timing/README.md#risks-and-how-to-handle-them) |
| 11 Sequence-to-function | Leakage through gene families and pretraining; a crowded field. | [11](projects/11-sequence-to-function-models/README.md#risks-and-how-to-handle-them) |
| 12 Convergent domestication | A null result is likely, and ancient duplications confound gene matching. | [12](projects/12-convergent-domestication-cross-crop/README.md#risks-and-how-to-handle-them) |
| 13 Somatic spectra | A long-read clone map of Pinot exists; short reads miss large SVs. | [13](projects/13-somatic-mutation-spectra-across-cultivars/README.md#risks-and-how-to-handle-them) |
| 14 TE insertions | Genotyping accuracy for TE insertions from short reads. | [14](projects/14-te-insertion-polymorphisms-cultivated/README.md#risks-and-how-to-handle-them) |
| 15 Graph introgression | Local ancestry fails with closely related donors; SNP painting is already done (preprint). | [15](projects/15-graph-introgression/README.md#risks-and-how-to-handle-them) |
| 16 SV load | The clonal versus sexual hemizygosity question is partly answered. | [16](projects/16-graph-sv-load/README.md#risks-and-how-to-handle-them) |
| 17 Inversions | Many inversions may be neutral; short-read genotyping of inversions is weak. | [17](projects/17-large-inversions-in-populations/README.md#risks-and-how-to-handle-them) |
| 18 Centromeres | Satellite arrays are not proof of centromere position without CENH3 data. | [18](projects/18-vitis-muscadinia-centromeres/README.md#risks-and-how-to-handle-them) |
| 19 RNA-seq on T2T | A drought atlas on the T2T assembly exists (preprint); allelic mapping bias. | [19](projects/19-public-rnaseq-on-t2t/README.md#risks-and-how-to-handle-them) |
| 20 Ancient seeds | Graph gains need raw reads, which may not be public. | [20](projects/20-ancient-seeds-on-graph/README.md#risks-and-how-to-handle-them) |
| 21 GWAS meta-analysis | Summary statistics may be missing; prediction across populations is weak. | [21](projects/21-gwas-meta-and-cross-ancestry-prediction/README.md#risks-and-how-to-handle-them) |
| 22 Sex region | The cross-genus question is answered; few sexed wild samples. | [22](projects/22-sex-region-population-level/README.md#risks-and-how-to-handle-them) |
| 23 Parentage | Without known-cross controls, error rates are unknown. | [23](projects/23-family-parentage/README.md#risks-and-how-to-handle-them) |
| 24 Recombination maps | Demography produces false hotspots in LD-based maps. | [24](projects/24-recombination-maps/README.md#risks-and-how-to-handle-them) |
| 25 TE annotation methods | General surveys and benchmarks exist; keep to a grape case study. | [25](projects/25-te-annotation-methods/README.md#risks-and-how-to-handle-them) |
| 26 Mitochondria | NUMT reads bias heteroplasmy calls; the maternal phylogeny option is largely covered. | [26](projects/26-mitochondrial-genomes/README.md#risks-and-how-to-handle-them) |

## Projects to narrow or keep demoted

- 22: keep demoted; the population-level question remains, the cross-genus one is answered.
- 16: narrow to the split between inherited and clonal hemizygosity within grape.
- 11: frame as a benchmark with leakage controls, not as a new model.
- 12: preregister the null result as publishable, or fold into a smaller comparison.
- 03, 06, 19 and 05: novelty depends on what the grape case adds to published templates; state this in the Gap section before starting.

## References

- INSDC 2024. The international nucleotide sequence database collaboration (INSDC): enhancing global participation. *Nucleic Acids Research*. [doi:10.1093/nar/gkae1058](https://doi.org/10.1093/nar/gkae1058)
- Noraz et al. 2026. Ancient DNA reveals 4000 years of grapevine diversity, viticulture and clonal propagation in France. *Nature Communications*. [doi:10.1038/s41467-026-70166-z](https://doi.org/10.1038/s41467-026-70166-z)
- Xiao et al. 2025. Impacts of reproductive systems on grapevine genome and breeding. *Nature Communications*. [doi:10.1038/s41467-025-56817-7](https://doi.org/10.1038/s41467-025-56817-7)
- Günther et al. 2019. The presence and impact of reference bias on population genomic studies of prehistoric human populations. *PLOS Genetics*. [doi:10.1371/journal.pgen.1008302](https://doi.org/10.1371/journal.pgen.1008302)
- Koptekin et al. 2025. Pre-processing of paleogenomes: mitigating reference bias and postmortem damage in ancient genome data. *Genome Biology*. [doi:10.1186/s13059-024-03462-w](https://doi.org/10.1186/s13059-024-03462-w)
- Brůna et al. 2026. Evolutionary and methodological considerations when interpreting gene presence–absence variation in pangenomes. *NAR Genomics and Bioinformatics*. [doi:10.1093/nargab/lqag011](https://doi.org/10.1093/nargab/lqag011)
