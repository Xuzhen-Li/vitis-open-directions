# AM03 · Short-read mapping and small-variant calling

## Tools

| Tool | Version | Role |
|---|---|---|
| bwa-mem2 | 2.3 | mapping |
| samtools | 1.25 | sorting, duplicates |
| DeepVariant | 1.10.0 | default caller |
| GATK | 4.7.0.0 (GitHub release) | alternative caller (HaplotypeCaller, GenotypeGVCFs) |
| bcftools | 1.25 | filters |
| GLnexus | 1.4.1 | joint genotyping of DeepVariant gVCFs (alternative to GenotypeGVCFs) |

Each tool is listed once, at its latest release on 2026-11-14 (UTC+8): Bioconda or conda-forge unless the version says GitHub, PyPI or CRAN. Pin versions in one environment file per project. The Role column says which tool is the default, which is an alternative to it, and which is a later step. Older tools are listed in the catalogues linked below, not here.

## Steps

Select samples first by a preregistered rule (AM04 on existing public genotypes; one sample per clone group, highest depth), and estimate CPU hours and storage before mapping: DeepVariant on thousands of samples requires hundreds of thousands of CPU hours. Map to PN_T2T (DS01); mark duplicates; call per sample with DeepVariant (default) or GATK HaplotypeCaller in GVCF mode (alternative); joint-genotype; apply hard filters; keep a filtered biallelic SNP set and an all-sites VCF for diversity statistics. Record each sample's panel of origin as a covariate; compare panels only within a panel or with panel included in the model.

## Command sketch

```bash
bwa-mem2 mem -t 16 -R '@RG\tID:x\tSM:x' ref.fa t1.fq.gz t2.fq.gz | samtools sort -o x.bam
samtools markdup ...
run_deepvariant --model_type=WGS --ref ref.fa --reads x.bam --output_gvcf x.g.vcf.gz
```

## Outputs

BAM/CRAM, gVCF, joint VCF

## HPC resources (rough)

16 CPU, 64 GB, 6–24 h per sample (DeepVariant); joint step 32 CPU, 128 GB

## Catalogue entries

- [vitis-pangenome §5 cohort genotyping](https://github.com/Xuzhen-Li/vitis-pangenome#section-5)

## Used by projects

- [08. A harmonised identity table for public grape resequencing panels](../../projects/08-harmonised-sample-panel/)
- [09. Graph genotyping of the berry colour locus](../../projects/09-berry-colour-locus-graph/)
- [10. Ancestral recombination graphs for hundreds of grape genomes and domestication timing](../../projects/10-arg-domestication-timing/)
- [12. Convergent domestication: grape compared with other crops in one pipeline](../../projects/12-convergent-domestication-cross-crop/)
- [13. Somatic mutation spectra across grape cultivars, with rates where clone dates are known](../../projects/13-somatic-mutation-spectra-across-cultivars/)
- [15. Introgression on a graph pangenome: wild-to-cultivated and hybrid cultivars](../../projects/15-graph-introgression/)
- [16. Inherited and clonal structural variants on a graph: where hemizygous SVs sit and why](../../projects/16-graph-sv-load/)
- [19. Public RNA-seq on PN_T2T: expression atlas, eQTL/sQTL and allele-specific expression](../../projects/19-public-rnaseq-on-t2t/)
- [21. Meta-analysis of public GWAS, cross-ancestry genomic prediction and SV markers](../../projects/21-gwas-meta-and-cross-ancestry-prediction/)
- [22. Population-level evolution of the sex-determining region (demoted)](../../projects/22-sex-region-population-level/)
