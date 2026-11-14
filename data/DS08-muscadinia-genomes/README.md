# DS08 · Muscadinia rotundifolia assemblies and reads

Outgroup genomes with a different karyotype (2n=40); chr7 and chr20 of Muscadinia map to Vitis chr7.

## Sources

| Part | Where |
|---|---|
| Trayshed | [zenodo.3866087](https://doi.org/10.5281/zenodo.3866087) (1.93 GB, CC BY 4.0); reads in [PRJNA593045](https://www.ebi.ac.uk/ena/browser/view/PRJNA593045) |
| Carlos | [zenodo.7944874](https://doi.org/10.5281/zenodo.7944874) (0.18 GB, CC BY 4.0); reads [PRJNA935741](https://www.ebi.ac.uk/ena/browser/view/PRJNA935741) (9 runs, 55.6 GB). The published version reports 112 contigs and 76 scaffolds, so the assembly still has gaps. |
| Powdery-mildew resistance loci | [PRJNA780568](https://www.ebi.ac.uk/ena/browser/view/PRJNA780568) (26 runs, 37.4 GB; 2 WGS, 24 RNA-seq), haplotype-resolved resistance loci |
| Other assemblies | NCBI lists 14 *Muscadinia* assemblies, all with gaps; none is telomere-to-telomere (NCBI Datasets, 2026-11-14). Whether GWH or CNGB hold a gap-free assembly [待确认]. |

Sizes are sums of `fastq_bytes` from the ENA portal API or file sizes from the Zenodo API, read on 2026-11-14 (UTC+8). They are download sizes, not disk needs after processing.

## Licence and reuse

Zenodo CC BY 4.0; INSDC no restrictions.

## Download (sketch)

```bash
zenodo_get 3866087 -o trayshed
zenodo_get 7944874 -o carlos
```

## Preparation

Keep a chromosome correspondence table (Muscadinia chr7 + chr20 → Vitis chr7).

## QC

AM05.

Shared conventions (layout, manifests, naming, coordinates) are in [`docs/DATA_PREP.md`](../../docs/DATA_PREP.md).

## Cite

- Cochetel et al. 2021. Diploid chromosome-scale assembly of the Muscadinia rotundifolia genome supports chromosome fusion and disease resistance gene expansion during Vitis and Muscadinia divergence. *G3 Genes|Genomes|Genetics*. [doi:10.1093/g3journal/jkab033](https://doi.org/10.1093/g3journal/jkab033)
- Huff et al. 2023. Long-read, chromosome-scale assembly of Vitis rotundifolia cv. Carlos and its unique resistance to Xylella fastidiosa subsp. fastidiosa. *BMC Genomics*. [doi:10.1186/s12864-023-09514-y](https://doi.org/10.1186/s12864-023-09514-y)
- Massonnet et al. 2022. Haplotype-resolved powdery mildew resistance loci reveal the impact of heterozygous structural variation on NLR genes in Muscadinia rotundifolia. *G3 Genes|Genomes|Genetics*. [doi:10.1093/g3journal/jkac148](https://doi.org/10.1093/g3journal/jkac148)

## Used by projects

- [01. Telomeres and interstitial telomeric repeats across near-complete grape haplotypes](../../projects/01-telomere-and-interstitial-telomeric-repeats/)
- [02. 45S and 5S rDNA arrays in near-complete grape assemblies](../../projects/02-rdna-arrays/)
- [06. A genus-wide NLR catalogue with integrated domains and collapse checks](../../projects/06-vitis-pan-nlrome/)
- [07. Copy number and birth–death of stilbene and aroma gene families (STS, TPS, CCD, LOX)](../../projects/07-metabolic-gene-families/)
- [10. Ancestral recombination graphs for hundreds of grape genomes and domestication timing](../../projects/10-arg-domestication-timing/)
- [18. Centromeres of Vitis and Muscadinia, and a check of the chr7 fusion point](../../projects/18-vitis-muscadinia-centromeres/)
