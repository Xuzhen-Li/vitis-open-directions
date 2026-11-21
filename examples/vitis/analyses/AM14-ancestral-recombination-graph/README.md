# AM14 · Ancestral recombination graphs and allele age

## Tools

| Tool | Version | Role |
|---|---|---|
| tsinfer | 0.5.1 (conda-forge) | inference (with tsdate) |
| tsdate | 0.2.7 (PyPI) | dating |
| Relate | [待确认] | alternative inference |
| SINGER | 0.1.8-beta (GitHub release) | alternative inference with posterior sampling |
| msprime | 1.4.5 (conda-forge) | coalescent simulation and recapitation |
| stdpopsim | 0.3.0 (conda-forge) | simulation framework; no grape model assumed [待确认] |
| SLiM | 5.2 (conda-forge) | forward simulation of clonal generations |
| pyslim | 1.1.1 (conda-forge) | links SLiM output to msprime |

Each tool is listed once, at its latest release on 2026-11-14 (UTC+8): Bioconda or conda-forge unless the version says GitHub, PyPI or CRAN. Pin versions in one environment file per project. The Role column says which tool is the default, which is an alternative to it, and which is a later step. Older tools are listed in the catalogues linked below, not here.

## Steps

Inputs come from AM26: phased haplotypes, ancestral states, and a recombination map. Simulate first: clonal generations are forward-simulated in SLiM and recapitated with msprime via pyslim, because msprime alone simulates backwards and does not model clonal propagation; stdpopsim is used for the framework only, with custom grape parameters and their sources written down [待确认: whether a grape model exists]. Check bias, interval coverage, and RMSE of each ARG method on the simulations, then choose the method for the real data before seeing it. Infer tree sequences (tsinfer with tsdate, Relate, or SINGER) and date alleles. By default, all samples are treated as contemporaneous; only the sensitivity run assigns documented old cultivars an earlier sampling time [待确认: how tsdate and Relate take non-contemporaneous samples]. Convert generations to years with μ and g drawn from preregistered intervals by Monte Carlo.

## Command sketch

```bash
slim -d SEED=1 clonal_model.slim            # forward clonal phase
python recapitate.py --in sim.trees --out sim_recap.trees   # pyslim + msprime
tsinfer infer samples.samples -O x.trees && tsdate date x.trees x.dated.trees --mutation-rate MU
```

## Outputs

calibration tables (bias, coverage, RMSE), tree sequences, allele ages with intervals

## HPC resources (rough)

SLiM 1 CPU, 8–32 GB per replicate (array over replicates); inference 16 CPU, 64 GB per chromosome; long walltime

## Catalogue entries

- [vitis-pangenome §11](https://github.com/Xuzhen-Li/vitis-pangenome#section-11)

## Used by projects

- [10. Ancestral recombination graphs for hundreds of grape genomes and domestication timing](../../projects/10-arg-domestication-timing/)
