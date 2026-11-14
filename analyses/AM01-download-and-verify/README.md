# AM01 · Download and verify

## Tools

| Tool | Version | Role |
|---|---|---|
| ncbi-datasets-cli | 18.41.1 (conda-forge) | assemblies and annotations |
| sra-tools | 3.4.1 | alternative to ENA FTP for runs |
| ENA FTP / Aspera | n/a | default for runs |
| zenodo_get | 3.1.0 (conda-forge) | Zenodo records |
| md5sum / sha256sum | coreutils | checks |

Each tool is listed once, at its latest release on 2026-11-14 (UTC+8): Bioconda or conda-forge unless the version says GitHub, PyPI or CRAN. Pin versions in one environment file per project. The Role column says which tool is the default, which is an alternative to it, and which is a later step. Older tools are listed in the catalogues linked below, not here.

## Steps

Get the run or file table from the ENA portal API, download over FTP with md5 check, write a manifest (file, bytes, md5, sha256, source URL, date). Run downloads on a node with internet access (login or transfer node); many clusters lack internet access on compute nodes. Never re-download into the same path; new files get a new date stamp.

## Command sketch

```bash
wget -nc -i urls.txt
md5sum -c expected.md5
sha256sum *.fastq.gz > SHA256SUMS
```

## Outputs

raw files + MANIFEST.tsv

## HPC resources (rough)

1–4 CPU, 4 GB, network; array over files

## Used by projects

- [01. Telomeres and interstitial telomeric repeats across near-complete grape haplotypes](../../projects/01-telomere-and-interstitial-telomeric-repeats/)
- [02. 45S and 5S rDNA arrays in near-complete grape assemblies](../../projects/02-rdna-arrays/)
- [03. Endogenous florendovirus insertions across grape haplotypes](../../projects/03-endogenous-florendoviruses/)
- [04. Virus discovery across public grape RNA-seq and unmapped reads](../../projects/04-virus-discovery-in-public-data/)
- [05. Gene presence/absence across grape pangenomes under one pipeline](../../projects/05-gene-pav-across-pangenomes/)
- [06. A genus-wide NLR catalogue with integrated domains and collapse checks](../../projects/06-vitis-pan-nlrome/)
- [07. Copy number and birth–death of stilbene and aroma gene families (STS, TPS, CCD, LOX)](../../projects/07-metabolic-gene-families/)
- [08. A harmonised identity table for public grape resequencing panels](../../projects/08-harmonised-sample-panel/)
- [09. Graph genotyping of the berry colour locus](../../projects/09-berry-colour-locus-graph/)
- [10. Ancestral recombination graphs for hundreds of grape genomes and domestication timing](../../projects/10-arg-domestication-timing/)
- [11. Sequence-to-expression models and plant foundation models evaluated on grape](../../projects/11-sequence-to-function-models/)
- [12. Convergent domestication: grape compared with other crops in one pipeline](../../projects/12-convergent-domestication-cross-crop/)
- [13. Somatic mutation spectra across grape cultivars, with rates where clone dates are known](../../projects/13-somatic-mutation-spectra-across-cultivars/)
- [14. TE insertion polymorphisms in cultivated grape from graph genotyping](../../projects/14-te-insertion-polymorphisms-cultivated/)
- [15. Introgression on a graph pangenome: wild-to-cultivated and hybrid cultivars](../../projects/15-graph-introgression/)
- [16. Inherited and clonal structural variants on a graph: where hemizygous SVs sit and why](../../projects/16-graph-sv-load/)
- [17. Large inversions: discovery in assemblies, population genotyping and suppressed recombination](../../projects/17-large-inversions-in-populations/)
- [18. Centromeres of Vitis and Muscadinia, and a check of the chr7 fusion point](../../projects/18-vitis-muscadinia-centromeres/)
- [19. Public RNA-seq on PN_T2T: expression atlas, eQTL/sQTL and allele-specific expression](../../projects/19-public-rnaseq-on-t2t/)
- [20. Archaeological grape seeds: graph mapping and low-coverage imputation](../../projects/20-ancient-seeds-on-graph/)
- [22. Population-level evolution of the sex-determining region (demoted)](../../projects/22-sex-region-population-level/)
