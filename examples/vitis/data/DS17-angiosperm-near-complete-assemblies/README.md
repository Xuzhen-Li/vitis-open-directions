# DS17 · Near-complete angiosperm assemblies (comparison set)

Complete-genome and chromosome-level flowering-plant assemblies in NCBI, used when a repeat-array question (telomeres, interstitial telomeric repeats, rDNA) is extended beyond Vitaceae.

## Sources

| Part | Where |
|---|---|
| NCBI query | taxon 3398 (Magnoliopsida), GenBank: 278 assemblies at Complete Genome level and 4,748 at Chromosome level on 2026-11-14 |

Sizes are sums of `fastq_bytes` from the ENA portal API or file sizes from the Zenodo API, read on 2026-11-14 (UTC+8). They are download sizes, not disk needs after processing.

## Licence and reuse

INSDC records: no use restrictions; cite each assembly's source paper when used.

## Download (sketch)

```bash
datasets summary genome taxon 3398 --assembly-level complete --assembly-source genbank --as-json-lines > angio_complete.jsonl
datasets download genome accession --inputfile picked_accessions.txt --include genome --dehydrated --filename angio.zip
unzip angio.zip -d angio && datasets rehydrate --directory angio
```

## Preparation

One assembly per species (highest level, latest release); record family and order from NCBI taxonomy; drop assemblies without telomere-to-telomere chromosomes for array-length work.

## QC

AM05 summary; check that chromosome counts match the karyotype where known [待确认 per species].

Shared conventions (layout, manifests, naming, coordinates) are in [`docs/DATA_PREP.md`](../../../../templates/DATA_PREP.md).

## Used by projects

- [01. Telomeres and interstitial telomeric repeats across near-complete grape haplotypes](../../projects/01-telomere-and-interstitial-telomeric-repeats/)
- [02. 45S and 5S rDNA arrays in near-complete grape assemblies](../../projects/02-rdna-arrays/)
