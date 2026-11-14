# DS03 · Vitis super-pangenome: 72 haplotype-resolved accessions

Haplotype-resolved assemblies and annotations of 25 wild and 47 cultivated accessions, plus reads, CENH3 ChIP-seq and downy-mildew RNA-seq.

## Sources

| Part | Where |
|---|---|
| Assemblies and annotations | [zenodo.13982444](https://doi.org/10.5281/zenodo.13982444) (22.07 GB, CC BY 4.0) |
| Reads | [PRJNA1021789](https://www.ebi.ac.uk/ena/browser/view/PRJNA1021789) (945 runs, 12,108.6 GB FASTQ; Illumina, ONT, PacBio; WGS and ChIP-seq). Also lists assemblies in NCBI, ENA and NGDC (paper Supplementary Table 16) |
| Code | [NotebookOFXiaoMing/SuperPangenomeofGrapevines](https://github.com/NotebookOFXiaoMing/SuperPangenomeofGrapevines) |

Sizes are sums of `fastq_bytes` from the ENA portal API or file sizes from the Zenodo API, read on 2026-11-14 (UTC+8). They are download sizes, not disk needs after processing.

## Licence and reuse

Zenodo: CC BY 4.0. INSDC reads: no use restrictions; cite the paper.

## Download (sketch)

```bash
zenodo_get 13982444 -o superpan72
# reads: pull only what a project needs, never the whole BioProject
curl -s 'https://www.ebi.ac.uk/ena/portal/api/filereport?accession=PRJNA1021789&result=read_run&fields=run_accession,library_strategy,instrument_platform,sample_title,fastq_ftp,fastq_md5,fastq_bytes&format=tsv' -o PRJNA1021789_runs.tsv
```

## Preparation

Split the run table by library_strategy (WGS / ChIP-Seq / RNA-Seq [待确认: RNA-seq may sit under a different BioProject]). Map each accession code in the assemblies to its sample name and species.

## QC

As DS02. The ChIP-seq subset is small enough to download in full for centromere work.

Shared conventions (layout, manifests, naming, coordinates) are in [`docs/DATA_PREP.md`](../../docs/DATA_PREP.md).

## Cite

- Guo et al. 2025. Super pangenome of Vitis empowers identification of downy mildew resistance genes for grapevine improvement. *Nature Genetics*. [doi:10.1038/s41588-025-02111-7](https://doi.org/10.1038/s41588-025-02111-7)

## Used by projects

- [01. Telomeres and interstitial telomeric repeats across near-complete grape haplotypes](../../projects/01-telomere-and-interstitial-telomeric-repeats/)
- [02. 45S and 5S rDNA arrays in near-complete grape assemblies](../../projects/02-rdna-arrays/)
- [03. Endogenous florendovirus insertions across grape haplotypes](../../projects/03-endogenous-florendoviruses/)
- [05. Gene presence/absence across grape pangenomes under one pipeline](../../projects/05-gene-pav-across-pangenomes/)
- [06. A genus-wide NLR catalogue with integrated domains and collapse checks](../../projects/06-vitis-pan-nlrome/)
- [07. Copy number and birth–death of stilbene and aroma gene families (STS, TPS, CCD, LOX)](../../projects/07-metabolic-gene-families/)
- [08. A harmonised identity table for public grape resequencing panels](../../projects/08-harmonised-sample-panel/)
- [09. Graph genotyping of the berry colour locus](../../projects/09-berry-colour-locus-graph/)
- [14. TE insertion polymorphisms in cultivated grape from graph genotyping](../../projects/14-te-insertion-polymorphisms-cultivated/)
- [15. Introgression on a graph pangenome: wild-to-cultivated and hybrid cultivars](../../projects/15-graph-introgression/)
- [16. Inherited and clonal structural variants on a graph: where hemizygous SVs sit and why](../../projects/16-graph-sv-load/)
- [17. Large inversions: discovery in assemblies, population genotyping and suppressed recombination](../../projects/17-large-inversions-in-populations/)
- [18. Centromeres of Vitis and Muscadinia, and a check of the chr7 fusion point](../../projects/18-vitis-muscadinia-centromeres/)
