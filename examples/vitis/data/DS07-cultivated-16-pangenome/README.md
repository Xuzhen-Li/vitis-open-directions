# DS07 · Cultivated grapevine pangenome (16 cultivars, Plastivigne)

Haplotyped assemblies of 15 cultivars plus PN40024, with HiFi, short reads and RNA-seq.

## Sources

| Part | Where |
|---|---|
| Assemblies, annotations, graph | [doi:10.57745/ckd4h5](https://doi.org/10.57745/ckd4h5) (Recherche Data Gouv) |
| HiFi | [PRJEB100755](https://www.ebi.ac.uk/ena/browser/view/PRJEB100755) (15 runs, 142.9 GB) |
| Short reads | [PRJEB95058](https://www.ebi.ac.uk/ena/browser/view/PRJEB95058) (205 runs, 1,225.9 GB) |
| RNA-seq | [PRJEB107006](https://www.ebi.ac.uk/ena/browser/view/PRJEB107006) (72 runs, 388.0 GB) |

Sizes are sums of `fastq_bytes` from the ENA portal API or file sizes from the Zenodo API, read on 2026-11-14 (UTC+8). They are download sizes, not disk needs after processing.

## Licence and reuse

Recherche Data Gouv record licence [待确认]; INSDC no restrictions.

## Download (sketch)

```bash
# Dataverse API: list files then fetch by id [待确认: exact API path]
curl -s 'https://entrepot.recherche.data.gouv.fr/api/datasets/:persistentId/?persistentId=doi:10.57745/CKD4H5' -o ckd4h5.json
```

## Preparation

As DS02.

## QC

As DS02.

Shared conventions (layout, manifests, naming, coordinates) are in [`docs/DATA_PREP.md`](../../../../templates/DATA_PREP.md).

## Cite

- Pierre et al. 2026. Pangenomic analyses in the cultivated grapevine confirm high genomic collinearity and extensive dispensable gene content likely involved in adaptation. *G3: Genes, Genomes, Genetics*. [doi:10.1093/g3journal/jkag168](https://doi.org/10.1093/g3journal/jkag168)

## Used by projects

- [01. Telomeres and interstitial telomeric repeats across near-complete grape haplotypes](../../projects/01-telomere-and-interstitial-telomeric-repeats/)
- [05. Gene presence/absence across grape pangenomes under one pipeline](../../projects/05-gene-pav-across-pangenomes/)
- [07. Copy number and birth–death of stilbene and aroma gene families (STS, TPS, CCD, LOX)](../../projects/07-metabolic-gene-families/)
- [14. TE insertion polymorphisms in cultivated grape from graph genotyping](../../projects/14-te-insertion-polymorphisms-cultivated/)
- [17. Large inversions: discovery in assemblies, population genotyping and suppressed recombination](../../projects/17-large-inversions-in-populations/)
