# Moving the framework to another species

Written 2026-11-21 (UTC+8). [中文](SPECIES_TRANSFER_GUIDE.zh.md)

These steps take a new species from nothing to a ranked list of directions, each ready for preregistration. The grapevine example in [examples/vitis/](../examples/vitis/) shows what the finished pages look like.

## Steps

1. Read [README.md](../README.md) and [START_HERE.md](../START_HERE.md) for the working rules: preregistration first, evidence logs are only appended to, a DOI that was not opened is marked [to confirm], no private data and no invented numbers.
2. Fill in [templates/SPECIES_INTAKE_CHECKLIST.md](../templates/SPECIES_INTAKE_CHECKLIST.md): references, panels, transcriptomes, organelle genomes, phenotypes, reproductive system and access limits.
3. Check every listed input through the archive APIs and give it one status: `available`, `portal`, `blocked` or `not found` (see [GAP_FRAMEWORK.md](GAP_FRAMEWORK.md)). Record accession, API, date and file sizes.
4. Go through the six dimensions of [GAP_FRAMEWORK.md](GAP_FRAMEWORK.md). For each candidate gap, fill in one [templates/GAP_AUDIT_TEMPLATE.md](../templates/GAP_AUDIT_TEMPLATE.md).
5. Check the literature through Crossref or DataCite records and full texts. Write down the query strings and the date.
6. Write the not-kept list of the species (directions already covered or not supported by public data, each with its covering papers) and the list of candidate directions.
7. Score the candidates with [EVALUATION_RUBRIC.md](EVALUATION_RUBRIC.md), including the independent second scoring, and freeze the scores with a date.
8. For each kept direction write a project page (gap, existing work, question, hypotheses and criteria, data, steps, paper split, risks, cluster plan) and a status page.
9. Before any main result is looked at, fill in [templates/PREREGISTRATION.md](../templates/PREREGISTRATION.md). Use [templates/DATA_PREP.md](../templates/DATA_PREP.md) and [templates/HPC_JOBS.md](../templates/HPC_JOBS.md) for downloads, checksums and pilot jobs, and append every step to the evidence log of the project ([templates/EVIDENCE_LOG_TEMPLATE.md](../templates/EVIDENCE_LOG_TEMPLATE.md)).

A suggested layout for a new species is `examples/<species>/` with the same parts as the grapevine example: `data/`, `analyses/`, `projects/`, an index, a ranking page, a defaults page and a not-kept list.

## Without internet access

Many model sessions and cluster compute nodes cannot reach the archives. In that case:

- Mark every accession and DOI that was not tested live as [to confirm].
- Write out the queries so that someone can run them on a login node with internet access, for example:

```bash
# read runs and FASTQ sizes of a project (ENA portal API)
curl -s "https://www.ebi.ac.uk/ena/portal/api/filereport?accession=PRJNAxxxxxx&result=read_run&fields=run_accession,instrument_platform,fastq_bytes,fastq_md5&format=tsv"
# assembly summary (NCBI Datasets command-line tool)
datasets summary genome accession GCF_xxxxxxxxx.x
# file list of a Zenodo record
curl -s "https://zenodo.org/api/records/RECORD_ID"
# DOI record
curl -s "https://api.crossref.org/works/DOI_HERE"
```

- Wait for the results to come back before scoring and before preregistration.
