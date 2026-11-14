# DS05 · Vitaceae family chromosome-level genomes

Chromosome-level assemblies across Vitaceae genera (Ampelopsis, Parthenocissus, Tetrastigma, Cissus and Vitis), annotations and ancestral karyotypes.

## Sources

| Part | Where |
|---|---|
| Assemblies | [PRJEB88780](https://www.ebi.ac.uk/ena/browser/view/PRJEB88780) (ENA; also 5 Illumina runs, 205.1 GB) |
| Raw reads | [PRJNA1219332](https://www.ebi.ac.uk/ena/browser/view/PRJNA1219332) (80 runs, 2,609.9 GB; WGS, Hi-C, RNA-seq) and PRJNA1021789 (DS03) |
| Annotations | [figshare 10.6084/m9.figshare.33329247](https://doi.org/10.6084/m9.figshare.33329247) |
| Ancestral karyotypes | [zenodo.18590277](https://doi.org/10.5281/zenodo.18590277) (0.06 GB, CC BY 4.0) |

Sizes are sums of `fastq_bytes` from the ENA portal API or file sizes from the Zenodo API, read on 2026-11-14 (UTC+8). They are download sizes, not disk needs after processing.

## Licence and reuse

Zenodo CC BY 4.0; figshare licence [待确认]; INSDC no restrictions.

## Download (sketch)

```bash
curl -s 'https://www.ebi.ac.uk/ena/portal/api/search?result=assembly&query=study_accession=PRJEB88780&fields=accession,assembly_name,scientific_name&format=tsv' -o PRJEB88780_assemblies.tsv  # field names [待确认]
```

## Preparation

Use the Vitaceae assembly table in data/ to pick one assembly per species; record genus, ploidy and assembly level.

## QC

AM05 on every assembly; drop contig-level assemblies for repeat-array work.

Shared conventions (layout, manifests, naming, coordinates) are in [`docs/DATA_PREP.md`](../../docs/DATA_PREP.md).

## Cite

- Wang et al. 2026. Chromosome-level phylogenomics and genome evolution of the grape family. *Nature Plants*. [doi:10.1038/s41477-026-02442-1](https://doi.org/10.1038/s41477-026-02442-1)

## Used by projects

- [01. Telomeres and interstitial telomeric repeats across near-complete grape haplotypes](../../projects/01-telomere-and-interstitial-telomeric-repeats/)
- [02. 45S and 5S rDNA arrays in near-complete grape assemblies](../../projects/02-rdna-arrays/)
- [03. Endogenous florendovirus insertions across grape haplotypes](../../projects/03-endogenous-florendoviruses/)
- [18. Centromeres of Vitis and Muscadinia, and a check of the chr7 fusion point](../../projects/18-vitis-muscadinia-centromeres/)
