# AM15 · RNA-seq quantification and allele-specific expression

## Tools

| Tool | Version | Role |
|---|---|---|
| salmon | 2.11.0 | atlas: gene-level quantification |
| STAR | 2.7.11b | BAMs for splicing and ASE (WASP filter on) |
| gffread | 0.12.9 | transcripts.fa from the DS01 annotation |
| tximport | 1.38.2 (Bioconductor) | transcript-to-gene aggregation |
| GATK | 4.7.0.0 (GitHub release) | ASEReadCounter on WASP-filtered BAMs |
| phASER | bioconda 0.1.1ad5f89 | haplotype-level ASE from the same BAM and phased VCF |
| bcftools | 1.25 | per-sample heterozygous VCF for the WASP filter |

Each tool is listed once, at its latest release on 2026-11-14 (UTC+8): Bioconda or conda-forge unless the version says GitHub, PyPI or CRAN. Pin versions in one environment file per project. The Role column says which tool is the default, which is an alternative to it, and which is a later step. Older tools are listed in the catalogues linked below, not here.

## Steps

Use the single annotation fixed in DS01 (RefSeq GCF_030704535.1-RS_2023_09 by default). Atlas: quantify every run with a decoy-aware salmon index and aggregate transcripts to genes with tximport and the DS01 tx2gene table. Splicing and ASE: map to PN_T2T with STAR with the WASP filter enabled (`--waspOutputMode SAMtag` with the phased VCF) and XS strand tags for unstranded libraries (`--outSAMstrandField intronMotif`). STAR's WASP filter takes one VCF per sample: extract each genotype's phased heterozygous sites from the multi-sample AM26 BCF (bcftools view -s, then keep heterozygous sites), using chromosome names from the DS01 rename map so they match the STAR index. ASE uses one route only: same-coordinate BAM + phased heterozygous sites called from DNA of the same genotype (AM03, phased in AM26) + WASP-passed reads, counted with GATK ASEReadCounter and phASER; minimum depth per site fixed in advance. Residual reference bias is estimated on the trio's known heterozygous sites (DS18).

## Command sketch

```bash
gffread -w transcripts.fa -g pn_t2t.fna pn_t2t.gff
salmon index -t gentrome.fa -d decoys.txt -i idx && salmon quant -i idx -l A -1 r1.fq.gz -2 r2.fq.gz -o q
bcftools view -s S1 -g het -Oz -o S1.het.vcf.gz phased.bcf
STAR --genomeDir star --readFilesIn r1.fq.gz r2.fq.gz --readFilesCommand zcat --waspOutputMode SAMtag --varVCFfile het.vcf --outSAMattributes NH HI AS nM vA vG vW --outSAMstrandField intronMotif --outSAMtype BAM SortedByCoordinate
```

## Outputs

gene-level TPM and counts (tximport), STAR BAMs with WASP tags, ASE tables per genotype × tissue

## HPC resources (rough)

16 CPU, 48 GB per run (STAR); salmon 8 CPU, 16 GB

## Catalogue entries

- [gene-function-annotation §11 expression-supported function](https://github.com/Xuzhen-Li/gene-function-annotation#section-11)
- [vitis-pangenome §10 expression](https://github.com/Xuzhen-Li/vitis-pangenome#section-10)

## Used by projects

- [11. Sequence-to-expression models and plant foundation models evaluated on grape](../../projects/11-sequence-to-function-models/)
- [19. Public RNA-seq on PN_T2T: expression atlas, eQTL/sQTL and allele-specific expression](../../projects/19-public-rnaseq-on-t2t/)
