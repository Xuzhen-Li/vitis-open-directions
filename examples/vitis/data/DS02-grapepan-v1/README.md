# DS02 · Grapepan v1.0: T2T haplotypes, graphs and a 466-accession resequencing panel

Telomere-to-telomere haplotypes of nine grapes, the Grapepan v1.0 graph, and short-read resequencing used for graph genotyping and GWAS.

## Sources

| Part | Where |
|---|---|
| Graph, assemblies, annotations | [zenodo.10851547](https://doi.org/10.5281/zenodo.10851547) (Grapepan v1.0, 10.71 GB, CC BY 4.0) and [zenodo.10846425](https://doi.org/10.5281/zenodo.10846425) (nine T2T diploid grapes, 4.22 GB, CC BY 4.0) |
| Assemblies in NCBI | BioProjects PRJNA1018808, PRJNA1018809, PRJNA1029477–PRJNA1029480, PRJNA1130629–PRJNA1130651 (as listed in the paper); per-haplotype GCA accessions are in [`../assemblies_vitaceae_ncbi_20261114.tsv`](../assemblies_vitaceae_ncbi_20261114.tsv) |
| Long reads and Hi-C | [PRJNA1048106](https://www.ebi.ac.uk/ena/browser/view/PRJNA1048106) (15 runs, 265.9 GB FASTQ; HiFi, ONT, Hi-C) |
| Resequencing | [PRJNA994294](https://www.ebi.ac.uk/ena/browser/view/PRJNA994294) (324 runs, 1,154.2 GB FASTQ, Illumina WGS). The paper genotyped 466 accessions; the remaining samples come from earlier projects [待确认: sample list in Supplementary Table] |
| NGDC mirror | PRJCA024688, PRJCA024753 [待确认: NGDC pages not checked] |

Sizes are sums of `fastq_bytes` from the ENA portal API or file sizes from the Zenodo API, read on 2026-11-14 (UTC+8). They are download sizes, not disk needs after processing.

## Licence and reuse

Zenodo records: CC BY 4.0 (checked via Zenodo API). INSDC reads: no use restrictions; cite the paper.

## Download (sketch)

```bash
zenodo_get 10851547 -o grapepan_v1     # or wget each file URL from the Zenodo API
zenodo_get 10846425 -o grapepan_t2t9
md5sum -c grapepan_v1/md5sums.txt
```

## Preparation

Convert haplotype FASTA names to PanSN (sample#hap#chrNN). Keep the published graph unchanged; derived graphs go to project folders. Build a sample sheet (run → BioSample → accession name → VIVC number) through module AM04 before any population analysis.

## QC

File md5 against Zenodo; per-haplotype length and N count; compleasm/BUSCO on each haplotype (AM05).

Shared conventions (layout, manifests, naming, coordinates) are in [`docs/DATA_PREP.md`](../../../../templates/DATA_PREP.md).

## Cite

- Liu et al. 2024. Grapevine pangenome facilitates trait genetics and genomic breeding. *Nature Genetics*. [doi:10.1038/s41588-024-01967-5](https://doi.org/10.1038/s41588-024-01967-5)

## Used by projects

- [01. Telomeres and interstitial telomeric repeats across near-complete grape haplotypes](../../projects/01-telomere-and-interstitial-telomeric-repeats/)
- [02. 45S and 5S rDNA arrays in near-complete grape assemblies](../../projects/02-rdna-arrays/)
- [03. Endogenous florendovirus insertions across grape haplotypes](../../projects/03-endogenous-florendoviruses/)
- [05. Gene presence/absence across grape pangenomes under one pipeline](../../projects/05-gene-pav-across-pangenomes/)
- [06. A genus-wide NLR catalogue with integrated domains and collapse checks](../../projects/06-vitis-pan-nlrome/)
- [07. Copy number and birth–death of stilbene and aroma gene families (STS, TPS, CCD, LOX)](../../projects/07-metabolic-gene-families/)
- [08. A harmonised identity table for public grape resequencing panels](../../projects/08-harmonised-sample-panel/)
- [09. Graph genotyping of the berry colour locus](../../projects/09-berry-colour-locus-graph/)
- [11. Sequence-to-expression models and plant foundation models evaluated on grape](../../projects/11-sequence-to-function-models/)
- [13. Somatic mutation spectra across grape cultivars, with rates where clone dates are known](../../projects/13-somatic-mutation-spectra-across-cultivars/)
- [14. TE insertion polymorphisms in cultivated grape from graph genotyping](../../projects/14-te-insertion-polymorphisms-cultivated/)
- [15. Introgression on a graph pangenome: wild-to-cultivated and hybrid cultivars](../../projects/15-graph-introgression/)
- [16. Inherited and clonal structural variants on a graph: where hemizygous SVs sit and why](../../projects/16-graph-sv-load/)
- [17. Large inversions: discovery in assemblies, population genotyping and suppressed recombination](../../projects/17-large-inversions-in-populations/)
- [18. Centromeres of Vitis and Muscadinia, and a check of the chr7 fusion point](../../projects/18-vitis-muscadinia-centromeres/)
- [19. Public RNA-seq on PN_T2T: expression atlas, eQTL/sQTL and allele-specific expression](../../projects/19-public-rnaseq-on-t2t/)
- [20. Archaeological grape seeds: graph mapping and low-coverage imputation](../../projects/20-ancient-seeds-on-graph/)
- [21. Meta-analysis of public GWAS, cross-ancestry genomic prediction and SV markers](../../projects/21-gwas-meta-and-cross-ancestry-prediction/)
