# DS21 · Population genomes of other domesticated plants (comparison set)

Published population resequencing of other fruit and field crops, for convergent-domestication comparisons with one pipeline. Accessions are taken from each paper's data statement at download time.

## Sources

| Part | Where |
|---|---|
| Peach | resequencing panel of the cited peach study [待确认: accession list] |
| Apple | resequencing panel of the cited apple study [待确认] |
| Citrus | genomes of the cited citrus study [待确认] |
| Potato | genomes of the cited potato study [待确认] |
| Rice | population genomes of the cited rice study [待确认] |

Sizes are sums of `fastq_bytes` from the ENA portal API or file sizes from the Zenodo API, read on 2026-11-14 (UTC+8). They are download sizes, not disk needs after processing.

## Licence and reuse

INSDC no restrictions; check each non-INSDC source.

## Download (sketch)

```bash
per BioProject filereport as DS10, after the accession list is confirmed
```

## Preparation

One reference per crop; record the wild and domesticated group labels from each paper.

## QC

AM02, AM04 per crop.

Shared conventions (layout, manifests, naming, coordinates) are in [`docs/DATA_PREP.md`](../../docs/DATA_PREP.md).

## Cite

- Yu et al. 2018. Genome re-sequencing reveals the evolutionary history of peach fruit edibility. *Nature Communications*. [doi:10.1038/s41467-018-07744-3](https://doi.org/10.1038/s41467-018-07744-3)
- Duan et al. 2017. Genome re-sequencing reveals the history of apple and supports a two-stage model for fruit enlargement. *Nature Communications*. [doi:10.1038/s41467-017-00336-7](https://doi.org/10.1038/s41467-017-00336-7)
- Wu et al. 2018. Genomics of the origin and evolution of Citrus. *Nature*. [doi:10.1038/nature25447](https://doi.org/10.1038/nature25447)
- Tang et al. 2022. Genome evolution and diversity of wild and cultivated potatoes. *Nature*. [doi:10.1038/s41586-022-04822-x](https://doi.org/10.1038/s41586-022-04822-x)
- Gutaker et al. 2020. Genomic history and ecology of the geographic spread of rice. *Nature Plants*. [doi:10.1038/s41477-020-0659-6](https://doi.org/10.1038/s41477-020-0659-6)

## Used by projects

- [12. Convergent domestication: grape compared with other crops in one pipeline](../../projects/12-convergent-domestication-cross-crop/)
