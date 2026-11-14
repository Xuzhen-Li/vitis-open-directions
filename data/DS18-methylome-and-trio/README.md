# DS18 · Public grape methylomes and a phased Cabernet Sauvignon trio

Bisulfite data from wild and cultivated grapes and a phased trio with WGS, RNA-seq and methylation. Used as a check set for allele-specific expression; too small for population epigenetics.

## Sources

| Part | Where |
|---|---|
| Cabernet Sauvignon trio | [PRJNA1244791](https://www.ebi.ac.uk/ena/browser/view/PRJNA1244791) (182 runs, 690.0 GB; 159 RNA-seq, 14 WGS, 9 Bisulfite-Seq); umbrella [PRJEB101820](https://www.ebi.ac.uk/ena/browser/view/PRJEB101820) (no runs) |
| Wild vs cultivated RRBS | [PRJEB55284](https://www.ebi.ac.uk/ena/browser/view/PRJEB55284) (18 runs, 2.4 GB, Bisulfite-Seq) |
| fruitENCODE | [PRJNA381300](https://www.ebi.ac.uk/ena/browser/view/PRJNA381300) (659 runs across 13 species; 30 *V. vinifera* runs) |

Sizes are sums of `fastq_bytes` from the ENA portal API or file sizes from the Zenodo API, read on 2026-11-14 (UTC+8). They are download sizes, not disk needs after processing.

## Licence and reuse

INSDC no restrictions; cite the source studies.

## Download (sketch)

```bash
curl -s 'https://www.ebi.ac.uk/ena/portal/api/filereport?accession=PRJNA1244791&result=read_run&fields=run_accession,library_strategy,sample_title,fastq_ftp,fastq_md5&format=tsv' -o trio_runs.tsv
```

## Preparation

Split runs by strategy and tissue; keep the trio relationship table. The trio's known heterozygous sites (from the WGS runs) serve as the check set for reference bias in allele-specific expression, and its parent–offspring structure separates inherited from new variants.

## QC

AM02; AM04 confirms the parent-offspring relationships.

Shared conventions (layout, manifests, naming, coordinates) are in [`docs/DATA_PREP.md`](../../docs/DATA_PREP.md).

## Cite

- Cochetel et al. 2025. Phased epigenomics and methylation inheritance in a historical Vitis vinifera hybrid. *Genome Biology*. [doi:10.1186/s13059-025-03858-2](https://doi.org/10.1186/s13059-025-03858-2)
- Rodriguez-Izquierdo et al. 2024. Epigenetic differences between wild and cultivated grapevines highlight the contribution of DNA methylation during crop domestication. *BMC Plant Biology*. [doi:10.1186/s12870-024-05197-z](https://doi.org/10.1186/s12870-024-05197-z)

## Used by projects

- [16. Inherited and clonal structural variants on a graph: where hemizygous SVs sit and why](../../projects/16-graph-sv-load/)
- [19. Public RNA-seq on PN_T2T: expression atlas, eQTL/sQTL and allele-specific expression](../../projects/19-public-rnaseq-on-t2t/)
