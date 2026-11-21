# DS04 · North American Vitis super-pangenome and wild resequencing

Nine North American Vitis species assemblies, graph and browser, plus wild-species resequencing used for introgression and Pierce's disease GWAS.

## Sources

| Part | Where |
|---|---|
| Assemblies and graph | [zenodo.8065808](https://doi.org/10.5281/zenodo.8065808) (24.35 GB; licence field empty in the Zenodo record [待确认]); code [zenodo.10206475](https://doi.org/10.5281/zenodo.10206475) (CC BY 4.0); browser [grapegenomics.com](https://grapegenomics.com/pages/NA_Vitis_pangenome/index.php) |
| Reads (this study) | [PRJNA984685](https://www.ebi.ac.uk/ena/browser/view/PRJNA984685) (95 runs, 428.5 GB FASTQ; WGS, RNA-seq, Iso-Seq) |
| Reads (earlier) | [PRJNA731597](https://www.ebi.ac.uk/ena/browser/view/PRJNA731597) (130 runs, 683.2 GB; introgression among wild grapes) and [PRJNA842753](https://www.ebi.ac.uk/ena/browser/view/PRJNA842753) (152 runs, 488.5 GB; V. arizonica Pierce's disease GWAS) |

Sizes are sums of `fastq_bytes` from the ENA portal API or file sizes from the Zenodo API, read on 2026-11-14 (UTC+8). They are download sizes, not disk needs after processing.

## Licence and reuse

Code record CC BY 4.0; data record licence not stated [待确认 before redistribution of derived files]. INSDC reads: no use restrictions.

## Download (sketch)

```bash
zenodo_get 8065808 -o na_vitis
for p in PRJNA984685 PRJNA731597 PRJNA842753; do curl -s "https://www.ebi.ac.uk/ena/portal/api/filereport?accession=$p&result=read_run&fields=run_accession,scientific_name,library_strategy,fastq_ftp,fastq_md5,fastq_bytes&format=tsv" -o ${p}_runs.tsv; done
```

## Preparation

Keep species labels from ENA scientific_name and check them against the paper tables; several runs are hybrids.

## QC

Species identity by k-mer distance (mash) against the nine assemblies before use.

Shared conventions (layout, manifests, naming, coordinates) are in [`docs/DATA_PREP.md`](../../../../templates/DATA_PREP.md).

## Cite

- Cochetel et al. 2023. A super-pangenome of the North American wild grape species. *Genome Biology*. [doi:10.1186/s13059-023-03133-2](https://doi.org/10.1186/s13059-023-03133-2)

## Used by projects

- [03. Endogenous florendovirus insertions across grape haplotypes](../../projects/03-endogenous-florendoviruses/)
- [05. Gene presence/absence across grape pangenomes under one pipeline](../../projects/05-gene-pav-across-pangenomes/)
- [06. A genus-wide NLR catalogue with integrated domains and collapse checks](../../projects/06-vitis-pan-nlrome/)
- [10. Ancestral recombination graphs for hundreds of grape genomes and domestication timing](../../projects/10-arg-domestication-timing/)
- [15. Introgression on a graph pangenome: wild-to-cultivated and hybrid cultivars](../../projects/15-graph-introgression/)
