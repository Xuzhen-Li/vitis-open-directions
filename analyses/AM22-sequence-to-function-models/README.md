# AM22 · Sequence-to-expression models and plant foundation models

## Tools

| Tool | Version | Role |
|---|---|---|
| PyTorch | 2.14.1 (conda-forge) |  |
| PlantCaduceus | [GitHub](https://github.com/plantcad/plantcad), version [待确认] |  |
| AgroNT | model release [待确认] |  |

Each tool is listed once, at its latest release on 2026-11-14 (UTC+8): Bioconda or conda-forge unless the version says GitHub, PyPI or CRAN. Pin versions in one environment file per project. The Role column says which tool is the default, which is an alternative to it, and which is a later step. Older tools are listed in the catalogues linked below, not here.

## Steps

Build gene-level targets from AM15. Split train and test by chromosome and by gene family so that paralogues do not leak. Compare a simple k-mer baseline, a model trained on grape only, and models pre-trained on other plants (with and without fine-tuning).

## Command sketch

```bash
# training scripts per model; fix seeds and splits in a config file before training
```

## Outputs

Held-out performance tables; per-variant predicted effects

## HPC resources (rough)

1–4 GPU, 64–256 GB RAM per training run

## Catalogue entries

- [vitis-pangenome §14 ideas (variant-effect models)](https://github.com/Xuzhen-Li/vitis-pangenome#section-14)

## Used by projects

- [11. Sequence-to-expression models and plant foundation models evaluated on grape](../../projects/11-sequence-to-function-models/)
