# Analysis modules

Each reusable analysis step is written once here.

| Module | Step | Used by projects |
|---|---|---|
| [AM01](AM01-download-and-verify/) | Download and verify | 01, 02, 03, 04, 05, 06, 07, 08, 09, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 22 |
| [AM02](AM02-read-qc/) | Read QC and trimming | 04, 08, 11, 13, 19 |
| [AM03](AM03-short-read-variants/) | Short-read mapping and small-variant calling | 08, 09, 10, 12, 13, 15, 16, 19, 21, 22 |
| [AM04](AM04-sample-identity/) | Sample identity, clones and relatedness | 08, 10, 13, 16, 19, 21 |
| [AM05](AM05-assembly-qc/) | Assembly QC | 01, 02, 03, 05, 06, 07, 14, 17, 18 |
| [AM06](AM06-wga-and-sv/) | Whole-genome alignment, synteny and SVs from assemblies | 03, 14, 17, 18 |
| [AM07](AM07-graph-build-and-genotype/) | Pangenome graph build and genotyping | 09, 14, 15, 16, 17, 20, 21 |
| [AM08](AM08-gene-family-annotation/) | Gene-family search across haplotypes | 05, 06, 07 |
| [AM09](AM09-gene-pav-and-cnv/) | Gene presence/absence and copy number | 05, 06, 07 |
| [AM10](AM10-repeat-arrays/) | Telomeres, centromeric satellites and rDNA arrays | 01, 02, 18 |
| [AM11](AM11-diversity-and-selection/) | Diversity and selection scans | 12 |
| [AM12](AM12-roh-and-load/) | Runs of homozygosity and deleterious load | 16 |
| [AM13](AM13-ancestry-and-introgression/) | Ancestry and introgression | 15, 20 |
| [AM14](AM14-ancestral-recombination-graph/) | Ancestral recombination graphs and allele age | 10 |
| [AM15](AM15-rnaseq-quant-and-ase/) | RNA-seq quantification and allele-specific expression | 11, 19 |
| [AM16](AM16-virus-and-eve-search/) | Virus discovery in RNA-seq and endogenous viral elements in assemblies | 03, 04 |
| [AM17](AM17-ancient-dna/) | Ancient DNA processing | 20 |
| [AM18](AM18-long-read-sv/) | Long-read SV calling | 06, 15, 16, 17 |
| [AM19](AM19-te-insertion-polymorphism/) | TE insertion polymorphisms among haplotypes | 14 |
| [AM20](AM20-somatic-variants/) | Somatic variants among clones and mutation spectra | 13 |
| [AM21](AM21-eqtl-and-sqtl/) | eQTL and splicing QTL | 19 |
| [AM22](AM22-sequence-to-function-models/) | Sequence-to-expression models and plant foundation models | 11 |
| [AM23](AM23-cross-crop-convergence/) | Cross-crop orthology and convergence tests | 12 |
| [AM24](AM24-gwas-meta-and-prediction/) | GWAS meta-analysis and genomic prediction | 21 |
| [AM25](AM25-small-rna-phasirna/) | Small-RNA and phasiRNA loci | 22 |
| [AM26](AM26-phasing-polarisation-recombination/) | Phasing, ancestral states and recombination rates | 10, 16, 19 |
