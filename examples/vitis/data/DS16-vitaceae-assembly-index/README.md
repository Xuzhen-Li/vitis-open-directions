# DS16 · Index of all Vitaceae assemblies in NCBI

A snapshot table of every Vitaceae genome assembly in NCBI, used to pick inputs for assembly-only projects.

## Sources

| Part | Where |
|---|---|
| Snapshot | [`assemblies_vitaceae_ncbi_20261114.tsv`](../assemblies_vitaceae_ncbi_20261114.tsv): 360 assemblies (taxon 3602), of which 95 are labelled Vitis vinifera; the genus Vitis query returned 350 |

Sizes are sums of `fastq_bytes` from the ENA portal API or file sizes from the Zenodo API, read on 2026-11-14 (UTC+8). They are download sizes, not disk needs after processing.

## Licence and reuse

NCBI metadata, public domain in the US [待确认 wording].

## Download (sketch)

```bash
curl -s 'https://api.ncbi.nlm.nih.gov/datasets/v2/genome/taxon/3602/dataset_report?page_size=1000' -o vitaceae.json
```

## Preparation

De-duplicate GCA/GCF pairs; keep the highest assembly level per haplotype; flag hybrids by organism name.

## QC

Lengths within an expected range for the genus; AM05 on chosen inputs.

Shared conventions (layout, manifests, naming, coordinates) are in [`docs/DATA_PREP.md`](../../../../templates/DATA_PREP.md).

## Used by projects

- [01. Telomeres and interstitial telomeric repeats across near-complete grape haplotypes](../../projects/01-telomere-and-interstitial-telomeric-repeats/)
- [02. 45S and 5S rDNA arrays in near-complete grape assemblies](../../projects/02-rdna-arrays/)
