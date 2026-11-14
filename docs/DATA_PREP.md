# Shared data-preparation conventions

These rules apply to every module in [`data/`](../data/).

## Folder layout on the cluster

```
<project_root>/
  raw/<DSxx>/<date>/        downloaded files, never edited
  ref/                      PN_T2T and liftover chains (DS01)
  work/<step>/<run_id>/     one new folder per run; never write into an old run
  results/<step>/<run_id>/  final tables and figures
  logs/                     SLURM logs
  MANIFEST.tsv              file, bytes, md5, sha256, source URL, date
```

## Download

- Get file lists from the archive API (ENA portal `filereport`, NCBI Datasets, Zenodo API), save the list, then download from the list. The list is the record of what was used.
- Check the archive md5 after download and add a sha256 for every file to `MANIFEST.tsv`.
- Download only the runs a project needs. Several BioProjects here are larger than 1 TB.
- Never download into an existing path; use a new dated folder.

## Sample identity

- Build one sample sheet per dataset: run, BioSample, sample name in the paper, accession or cultivar name, VIVC number when known, and tissue.
- Run [AM04](../analyses/AM04-sample-identity/) before any population statistic. Public panels share material and contain clones.

## Sequence names and coordinates

- Chromosomes are `chr01`..`chr19` on PN_T2T ([DS01](../data/DS01-pn40024-references/)). Keep a map from archive names.
- Haplotypes use PanSN names: `sample#hap#chrNN`.
- Older public coordinates (12X, PN40024.v4) are lifted once with the chain kept in DS01.
- *Muscadinia* chr7 and chr20 both correspond to *Vitis* chr7.

## Licences

- INSDC (NCBI, ENA, DDBJ) and GEO records have no use restrictions; cite the source study.
- Zenodo and figshare records carry their own licence; each data module states it or marks it [待确认].
- Figures reused from papers need a licence that allows it (for example CC BY) and a credit line.

## Before analysis

- Fill in [`PREREGISTRATION.md`](PREREGISTRATION.md) before looking at results.
- Record tool versions in one environment file per project.
