# DS09 · Sex-determination region haplotypes and reads

Male, female and hermaphrodite haplotypes of the grape sex-determining region from wild and cultivated Vitis, with the reads used to build them.

## Sources

| Part | Where |
|---|---|
| Haplotypes and annotations | [zenodo.3827985](https://doi.org/10.5281/zenodo.3827985) (3.01 GB, CC BY 4.0) |
| Reads | [PRJNA593045](https://www.ebi.ac.uk/ena/browser/view/PRJNA593045) (52 runs, 270.1 GB; WGS, RNA-seq) |
| Vitaceae sex-determining regions | [PRJNA1151724](https://www.ebi.ac.uk/ena/browser/view/PRJNA1151724) (43 runs, 621.4 GB; 26 WGS, 17 RNA-seq), phased sex-determining regions of six Vitaceae species and *Leea* |

Sizes are sums of `fastq_bytes` from the ENA portal API or file sizes from the Zenodo API, read on 2026-11-14 (UTC+8). They are download sizes, not disk needs after processing.

## Licence and reuse

Zenodo CC BY 4.0; INSDC no restrictions.

## Download (sketch)

```bash
zenodo_get 3827985 -o sexlocus
```

## Preparation

Extract the chr2 sex-region coordinates on PN_T2T through DS01 liftover.

## QC

AM05 on the region only.

Shared conventions (layout, manifests, naming, coordinates) are in [`docs/DATA_PREP.md`](../../../../templates/DATA_PREP.md).

## Cite

- Massonnet et al. 2020. The genetic basis of sex determination in grapes. *Nature Communications*. [doi:10.1038/s41467-020-16700-z](https://doi.org/10.1038/s41467-020-16700-z)
- Badouin et al. 2020. The wild grape genome sequence provides insights into the transition from dioecy to hermaphroditism during grape domestication. *Genome Biology*. [doi:10.1186/s13059-020-02131-y](https://doi.org/10.1186/s13059-020-02131-y)
- Massonnet et al. 2025. Evolutionary conservation of the grape sex-determining region in angiosperms and emergence of dioecy in Vitaceae. *Nature Communications*. [doi:10.1038/s41467-025-61387-9](https://doi.org/10.1038/s41467-025-61387-9)

## Used by projects

- [22. Population-level evolution of the sex-determining region (demoted)](../../projects/22-sex-region-population-level/)
