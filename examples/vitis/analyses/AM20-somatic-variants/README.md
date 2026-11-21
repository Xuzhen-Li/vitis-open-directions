# AM20 · Somatic variants among clones and mutation spectra

## Tools

| Tool | Version | Role |
|---|---|---|
| DeepSomatic | 1.10.0 (GitHub release) | default caller; suitability for plant clones [待确认] |
| GATK Mutect2 | 4.7.0.0 | alternative caller |
| GenMap | 1.3.0 | mappability mask |
| SigProfilerExtractor | 1.6.1 (PyPI) | spectra |
| mosdepth | 0.3.14 | depth and callable bp |

Each tool is listed once, at its latest release on 2026-11-14 (UTC+8): Bioconda or conda-forge unless the version says GitHub, PyPI or CRAN. Pin versions in one environment file per project. The Role column says which tool is the default, which is an alternative to it, and which is a later step. Older tools are listed in the catalogues linked below, not here.

## Steps

Use at least three clones per cultivar so that the direction of change can be set by parsimony. Call candidate somatic SNVs and indels for each clone against the other clones of the same cultivar on PN_T2T (the same reference for all cultivars). A public phased assembly comes from one clone, so that clone is treated as one tip of the clone tree: re-call it from its reads together with the other clones where the reads are public. The starting genotype is the state shared by all clones, including the assembled clone (or the consensus of all clones where no phased assembly exists). At variable sites, distinguishing LOH in one clone from a new mutation shared by several clones requires a rooted clone tree: root it with parental genotypes where they are public (for example Gouais blanc, a parent of Chardonnay), and call LOH as runs of consecutive germline heterozygous sites that become homozygous, by segment rather than site by site, since new mutations occur at isolated sites. Count as mutations only new alleles that are absent from the starting genotype and present in some clones; list states seen only in the assembly as unpolarised rather than as LOH; report loss of heterozygosity as a separate class, not in the spectrum or the rate. Variants confined to one cell layer appear in mixed-layer tissue at a VAF of about 0.5 × the layer's share of cells, so the VAF window is set by tissue before calling; published layer-specific variants (Merlot roots vs leaves) serve as positive controls. Mask low-mappability, repeat and centromere regions before any spectrum is computed, because clone-specific SV calls concentrate there. Re-genotype candidates in all clones; estimate callable bp (mosdepth) and sensitivity with in-silico spike-ins. Normalise 6-class and 96-class spectra to the trinucleotide composition of each cultivar's callable region.

## Command sketch

```bash
genmap index -F ref.fa -I idx && genmap map -K 100 -E 2 -I idx -O map -bg
run_deepsomatic --model_type=WGS --ref ref.fa --reads_tumor cloneA.bam --reads_normal pool_others.bam --output_vcf A.vcf.gz  # pairing design [待确认]
```

## Outputs

per-clone somatic call sets, LOH table, masked-region and callable-bp tables, sensitivity estimates, normalised spectra per cultivar

## HPC resources (rough)

16 CPU, 64 GB per clone (DeepSomatic); GPU optional

## Catalogue entries

- [vitis-pangenome §5 cohort genotyping](https://github.com/Xuzhen-Li/vitis-pangenome#section-5)

## Used by projects

- [13. Somatic mutation spectra across grape cultivars, with rates where clone dates are known](../../projects/13-somatic-mutation-spectra-across-cultivars/)
