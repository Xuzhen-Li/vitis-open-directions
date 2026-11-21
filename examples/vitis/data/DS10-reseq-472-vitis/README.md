# DS10 · Resequencing of 472 Vitis accessions (and the 2017 domestication panel)

Short-read WGS of wild and cultivated Vitis and Vitaceae outgroups.

## Sources

| Part | Where |
|---|---|
| 472 accessions | [PRJNA393611](https://www.ebi.ac.uk/ena/browser/view/PRJNA393611) (476 runs, 2,101.7 GB) |
| Domestication panel | [PRJNA388292](https://www.ebi.ac.uk/ena/browser/view/PRJNA388292) (23 runs, 173.8 GB; V. vinifera, sylvestris, rotundifolia) |

Sizes are sums of `fastq_bytes` from the ENA portal API or file sizes from the Zenodo API, read on 2026-11-14 (UTC+8). They are download sizes, not disk needs after processing.

## Licence and reuse

INSDC no restrictions; cite the papers.

## Download (sketch)

```bash
curl -s 'https://www.ebi.ac.uk/ena/portal/api/filereport?accession=PRJNA393611&result=read_run&fields=run_accession,sample_accession,sample_title,scientific_name,fastq_ftp,fastq_md5,fastq_bytes&format=tsv' -o PRJNA393611_runs.tsv
```

## Preparation

Sample sheet via AM04; mark outgroup genera; remove duplicates and clones before population statistics.

## QC

AM02, AM04.

Shared conventions (layout, manifests, naming, coordinates) are in [`docs/DATA_PREP.md`](../../../../templates/DATA_PREP.md).

## Cite

- Liang et al. 2019. Whole-genome resequencing of 472 Vitis accessions for grapevine diversity and demographic history analyses. *Nature Communications*. [doi:10.1038/s41467-019-09135-8](https://doi.org/10.1038/s41467-019-09135-8)
- Zhou et al. 2017. Evolutionary genomics of grape ( Vitis vinifera ssp. vinifera ) domestication. *Proceedings of the National Academy of Sciences*. [doi:10.1073/pnas.1709257114](https://doi.org/10.1073/pnas.1709257114)

## Used by projects

- [04. Virus discovery across public grape RNA-seq and unmapped reads](../../projects/04-virus-discovery-in-public-data/)
- [07. Copy number and birth–death of stilbene and aroma gene families (STS, TPS, CCD, LOX)](../../projects/07-metabolic-gene-families/)
- [08. A harmonised identity table for public grape resequencing panels](../../projects/08-harmonised-sample-panel/)
- [09. Graph genotyping of the berry colour locus](../../projects/09-berry-colour-locus-graph/)
- [10. Ancestral recombination graphs for hundreds of grape genomes and domestication timing](../../projects/10-arg-domestication-timing/)
- [12. Convergent domestication: grape compared with other crops in one pipeline](../../projects/12-convergent-domestication-cross-crop/)
- [14. TE insertion polymorphisms in cultivated grape from graph genotyping](../../projects/14-te-insertion-polymorphisms-cultivated/)
- [15. Introgression on a graph pangenome: wild-to-cultivated and hybrid cultivars](../../projects/15-graph-introgression/)
- [16. Inherited and clonal structural variants on a graph: where hemizygous SVs sit and why](../../projects/16-graph-sv-load/)
- [17. Large inversions: discovery in assemblies, population genotyping and suppressed recombination](../../projects/17-large-inversions-in-populations/)
- [19. Public RNA-seq on PN_T2T: expression atlas, eQTL/sQTL and allele-specific expression](../../projects/19-public-rnaseq-on-t2t/)
- [20. Archaeological grape seeds: graph mapping and low-coverage imputation](../../projects/20-ancient-seeds-on-graph/)
- [21. Meta-analysis of public GWAS, cross-ancestry genomic prediction and SV markers](../../projects/21-gwas-meta-and-cross-ancestry-prediction/)
- [22. Population-level evolution of the sex-determining region (demoted)](../../projects/22-sex-region-population-level/)
