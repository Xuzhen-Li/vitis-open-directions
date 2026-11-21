# DS23 · Long-read and multi-omic Vitis study (hemizygous genes)

One ENA study with PacBio and PromethION whole-genome reads, Hi-C, RNA-seq and bisulfite data from Vitis vinifera and two wild Vitis species. It was already used by projects 16 to 19 and listed in data/DOWNLOADS.md, but had no module of its own.

## Sources

| Part | Where |
|---|---|
| Study | [PRJNA1178252](https://www.ebi.ac.uk/ena/browser/view/PRJNA1178252): 16 runs with FASTQ; ENA study title: The genomic and epigenomic landscapes of hemizygous genes across crops with contrasting reproductive systems |
| Long reads, V. vinifera | PacBio RS II WGS, 2 runs (21.1 GB), including [SRR31308326](https://www.ebi.ac.uk/ena/browser/view/SRR31308326) (subreads FASTQ); PromethION WGS, 1 run (38.1 GB) |
| Long reads, V. piasezkii | PacBio RS II WGS, 1 run (10.1 GB) |
| Hi-C, V. vinifera | 2 runs (55.3 GB) |
| RNA-seq | V. piasezkii 3 runs (6.8 GB); V. retordii 3 runs (7.4 GB) |
| Bisulfite-seq | V. vinifera 1 run (14.0 GB); V. piasezkii 1 run (7.7 GB); V. retordii 2 runs (12.4 GB) |

Sizes are sums of `fastq_bytes` from the ENA portal API, read on 2026-11-21 (UTC+8); the total is 172.9 GB. They are download sizes, not disk needs after processing. All sixteen runs were listed with these library strategies and instruments; which individual each run comes from was not read [to confirm].

## Licence and reuse

INSDC no restrictions; cite the source study.

## Download (sketch)

```bash
curl -s "https://www.ebi.ac.uk/ena/portal/api/filereport?accession=PRJNA1178252&result=read_run&fields=run_accession,library_strategy,instrument_model,scientific_name,fastq_ftp,fastq_md5,fastq_bytes&format=tsv" -o runs.tsv
```

## Preparation

Split runs by library strategy and species. Before using a read set as evidence for a given genotype, check its BioSample and name against the genotype you think it is (see project 17, which notes that one long-read run has a BioSample that differs from the reference). Keep a manifest with sha256 for every file.

## QC

AM02 for reads. Project-specific checks are in the project pages.

Shared conventions (layout, manifests, naming, coordinates) are in [`docs/DATA_PREP.md`](../../docs/DATA_PREP.md).

## Cite

- Peng et al. 2025. The genomic and epigenomic landscapes of hemizygous genes across crops with contrasting reproductive systems. *PNAS*. [doi:10.1073/pnas.2422487122](https://doi.org/10.1073/pnas.2422487122) (Crossref record checked 2026-11-21; an earlier preprint is [doi:10.1101/2024.05.24.595664](https://doi.org/10.1101/2024.05.24.595664)). That the ENA study is the data deposit of this paper rests on the identical title and was not checked against the paper data statement [to confirm].

## Used by projects

- [16. Inherited and clonal structural variants on a graph: where hemizygous SVs sit and why](../../projects/16-graph-sv-load/)
- [17. Large inversions: discovery in assemblies, population genotyping and suppressed recombination](../../projects/17-large-inversions-in-populations/)
- [18. Centromeres of Vitis and Muscadinia, and a check of the chr7 fusion point](../../projects/18-vitis-muscadinia-centromeres/)
- [19. Public RNA-seq on PN_T2T: expression atlas, eQTL/sQTL and allele-specific expression](../../projects/19-public-rnaseq-on-t2t/)
