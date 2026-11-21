# DS11 · Resequencing of 3,525 grapevine accessions (Dong et al. 2023)

The largest public grape resequencing panel, with wild ecotypes and cultivated groups.

## Sources

| Part | Where |
|---|---|
| Reads | NGDC GSA [CRA006917](https://ngdc.cncb.ac.cn/gsa/browse/CRA006917) (HTTP 200; page is rendered by JavaScript so size and run count were not read [待确认]) |
| BioProject | NGDC PRJCA009314. The NGDC description lists 1,014 wild and 2,256 cultivated accessions; the paper reports 3,525 accessions in total, so some samples come from other projects [待确认] |
| VS-1 assembly | NGDC CRA006898 and GWHBQCW00000000 [待确认] |

Sizes are sums of `fastq_bytes` from the ENA portal API or file sizes from the Zenodo API, read on 2026-11-14 (UTC+8). They are download sizes, not disk needs after processing.

## Licence and reuse

NGDC GSA open-access data; reuse terms per NGDC data policy [待确认].

## Download (sketch)

```bash
# GSA provides FTP and HTTP per-run links; list them from the CRA page export [待确认: scriptable endpoint]
```

## Preparation

Harmonise sample names with VIVC and with DS10/DS12 through AM04; many accessions are likely shared between panels [待确认].

## QC

AM02, AM04.

Shared conventions (layout, manifests, naming, coordinates) are in [`docs/DATA_PREP.md`](../../../../templates/DATA_PREP.md).

## Cite

- Dong et al. 2023. Dual domestications and origin of traits in grapevine evolution. *Science*. [doi:10.1126/science.add8655](https://doi.org/10.1126/science.add8655)

## Used by projects

- [08. A harmonised identity table for public grape resequencing panels](../../projects/08-harmonised-sample-panel/)
- [10. Ancestral recombination graphs for hundreds of grape genomes and domestication timing](../../projects/10-arg-domestication-timing/)
