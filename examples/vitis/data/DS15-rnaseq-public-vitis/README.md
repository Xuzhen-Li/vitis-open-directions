# DS15 · Public Vitis RNA-seq and the expression atlas

Bulk RNA-seq for expression re-quantification, allele-specific expression and virus discovery.

## Sources

| Part | Where |
|---|---|
| Germplasm transcriptomes | [PRJNA565689](https://www.ebi.ac.uk/ena/browser/view/PRJNA565689) (475 runs, 608.7 GB; many Vitis species) |
| Tissue series | [PRJNA434655](https://www.ebi.ac.uk/ena/browser/view/PRJNA434655) (43 runs, 53.2 GB) |
| Plastivigne RNA-seq | [PRJEB107006](https://www.ebi.ac.uk/ena/browser/view/PRJEB107006) (72 runs) |
| Seven-cultivar series | [PRJNA260535](https://www.ebi.ac.uk/ena/browser/view/PRJNA260535) (84 runs, 149.2 GB) |
| Rootstock series | [PRJNA674915](https://www.ebi.ac.uk/ena/browser/view/PRJNA674915) (216 runs, 42.6 GB) and [PRJNA915033](https://www.ebi.ac.uk/ena/browser/view/PRJNA915033) (996 runs, 179.5 GB) [待确认: linked papers] |
| Expression atlas (microarray, not RNA-seq) | GEO [GSE36128](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE36128) |
| Everything else | ENA query `tax_tree(3603) AND library_strategy="RNA-Seq"` returned 17,172 runs on 2026-11-14 |

Sizes are sums of `fastq_bytes` from the ENA portal API or file sizes from the Zenodo API, read on 2026-11-14 (UTC+8). They are download sizes, not disk needs after processing.

## Licence and reuse

INSDC and GEO: no use restrictions; cite the source studies.

## Download (sketch)

```bash
curl -s 'https://www.ebi.ac.uk/ena/portal/api/search?result=read_run&query=tax_tree(3603)%20AND%20library_strategy=%22RNA-Seq%22&fields=run_accession,study_accession,sample_accession,scientific_name,instrument_platform,library_layout,read_count,base_count,fastq_bytes,first_public&format=tsv&limit=0' -o vitis_rnaseq_runs.tsv
```

## Preparation

Build one metadata table (tissue, stage, cultivar, treatment) with manual curation of BioSample fields; flag single-end and short reads.

## QC

AM02; strandedness check with salmon libtype.

Shared conventions (layout, manifests, naming, coordinates) are in [`docs/DATA_PREP.md`](../../../../templates/DATA_PREP.md).

## Cite

- Fasoli et al. 2012. The Grapevine Expression Atlas Reveals a Deep Transcriptome Shift Driving the Entire Plant into a Maturation Program. *The Plant Cell*. [doi:10.1105/tpc.112.100230](https://doi.org/10.1105/tpc.112.100230)

## Used by projects

- [04. Virus discovery across public grape RNA-seq and unmapped reads](../../projects/04-virus-discovery-in-public-data/)
- [11. Sequence-to-expression models and plant foundation models evaluated on grape](../../projects/11-sequence-to-function-models/)
- [19. Public RNA-seq on PN_T2T: expression atlas, eQTL/sQTL and allele-specific expression](../../projects/19-public-rnaseq-on-t2t/)
