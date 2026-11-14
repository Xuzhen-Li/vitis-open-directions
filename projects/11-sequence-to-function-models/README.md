# 11. Sequence-to-expression models and plant foundation models evaluated on grape

中文：葡萄序列到表达模型与植物基础模型的跨物种迁移评估

Rank 11 of 22 (score F 2 + N 3 + E 1 = 6; see docs/RANKING.md) · Tier: Large (E = 1, more than 4 months or a high-risk step) · Origin: new · Status: draft v0.3.2, 2026-11-14

## Gap

Sequence-to-expression models and plant foundation models have not been evaluated on grape in a journal paper [待确认: only a conference abstract found].

**Existing work**

- [Washburn et al. 2019](https://doi.org/10.1073/pnas.1814551116): deep learning of transcript abundance from sequence in grasses.
- [Peleke et al. 2024](https://doi.org/10.1038/s41467-024-47744-0): cis-regulatory models in selected model plants.
- [Mendoza-Revilla et al. 2024](https://doi.org/10.1038/s42003-024-06465-2): a foundation language model for edible plant genomes.
- [Zhai et al. 2025](https://doi.org/10.1073/pnas.2421738122): a cross-species plant genome model at single-nucleotide resolution.

**How this project differs**

A transfer evaluation with chromosome and gene-family hold-outs, a k-mer baseline, and checks against grape expression data.

## Question

Do models trained on other plants predict grape expression from sequence better than a grape-only model and a simple baseline?

## Hypotheses, planned figures and criteria

No results are given here. Each row says what would count as support; the exact thresholds go into the preregistration.

| Figure or table | Hypothesis or purpose | Criterion |
|---|---|---|
| Fig 1. Held-out performance | Pre-trained models beat the k-mer baseline on held-out chromosomes. | Spearman correlation (expression) or AUC (on/off) with 95% bootstrap intervals; held-out chromosomes and gene families fixed in advance; paralogues kept in the same split. |
| Fig 2. Fine-tuned vs zero-shot, and against a model trained on other plants | Fine-tuning on grape improves over zero-shot use; a sequence-to-expression model trained on other plants serves as the comparison. | Zero-shot means frozen embeddings with a linear probe trained on grape targets; fine-tuning protocol fixed in advance; paired bootstrap on the same test genes with effect sizes. If the pre-training corpus includes *Vitis* [待确认], the result is reported as within-genus rather than transfer. |
| Fig 3. Variant effects | Predicted effects agree in sign with allele-specific expression from project 19. | Sign agreement tested against 50% with one ASE site per gene as the unit; performed only if project 19 yields ASE sites. |

## Preregistration

Before any data are analysed, fill in [`docs/PREREGISTRATION.md`](../../docs/PREREGISTRATION.md) for this project: hypotheses, primary outcome, sample inclusion rules, thresholds, stop rules and what will be reported if a hypothesis fails. Commit it with a date. Criteria from any earlier attempt are reference only and are not carried over.

## Data

| Module | Dataset |
|---|---|
| [DS01](../../data/DS01-pn40024-references/) | PN40024 references: PN_T2T (v5), PN40024.v4 and 12X |
| [DS15](../../data/DS15-rnaseq-public-vitis/) | Public Vitis RNA-seq and the expression atlas |
| [DS02](../../data/DS02-grapepan-v1/) | Grapepan v1.0: T2T haplotypes, graphs and a 466-accession resequencing panel |

## Analysis steps

Shared modules, in order:

1. [AM01 · Download and verify](../../analyses/AM01-download-and-verify/)
2. [AM02 · Read QC and trimming](../../analyses/AM02-read-qc/)
3. [AM15 · RNA-seq quantification and allele-specific expression](../../analyses/AM15-rnaseq-quant-and-ase/)
4. [AM22 · Sequence-to-expression models and plant foundation models](../../analyses/AM22-sequence-to-function-models/)

Project-specific steps:

- Reuse the gene-level expression tables from project 19 (AM15) with their run IDs and sha256, or rebuild them with AM01, AM02, and AM15 in the same way; never mix the two.
- Fix splits by chromosome and gene family.
- Train the k-mer baseline, a grape-only model, and an expression model trained on other plants; evaluate the language models both zero-shot (frozen embeddings + linear probe) and fine-tuned.
- Fig 3 depends on project 19's ASE output.

## Paper design and split

| Paper | Working title | Type | Figures |
|---|---|---|---|
| L1 | How well do plant sequence models transfer to grape | methods paper | Fig 1–3 |

Each paper: introduction from the gap above; one results section per figure; methods with tool versions from the modules; data availability listing every accession used and the derived tables.

## Risks and novelty check

- Risk: Leakage between paralogues inflates scores.
- Risk: GPU access is needed.
- Risk: Tissue mixing in public RNA-seq adds noise.
- Novelty: checked against the existing work above (Crossref-verified DOIs). Repeat the search before writing; anything marked [待确认] is not yet verified.

## Rough estimates

- Compute: large (GPU) [draft]
- Effort: 3–5 months for one person [draft]
- Target: computational biology journal [draft]

## Continue on HPC

Run each step as its own job, in this order. Every job writes `.DONE` or `.FAILED` and a log; the next step starts only after `.DONE`. Template and rules: [`docs/HPC_JOBS.md`](../../docs/HPC_JOBS.md).

| Order | Step | Main tools | Resources (rough) |
|---|---|---|---|
| 1 | [AM01](../../analyses/AM01-download-and-verify/) Download and verify | ncbi-datasets-cli, sra-tools, ENA FTP / Aspera | 1–4 CPU, 4 GB, network; array over files |
| 2 | [AM02](../../analyses/AM02-read-qc/) Read QC and trimming | fastp, MultiQC, seqkit | 8 CPU, 16 GB, 1–2 h per run; array over runs |
| 3 | [AM15](../../analyses/AM15-rnaseq-quant-and-ase/) RNA-seq quantification and allele-specific expression | salmon, STAR, gffread | 16 CPU, 48 GB per run (STAR); salmon 8 CPU, 16 GB |
| 4 | [AM22](../../analyses/AM22-sequence-to-function-models/) Sequence-to-expression models and plant foundation models | PyTorch, PlantCaduceus, AgroNT | 1–4 GPU, 64–256 GB RAM per training run |

Public inputs: [DS01](../../data/DS01-pn40024-references/), [DS15](../../data/DS15-rnaseq-public-vitis/), [DS02](../../data/DS02-grapepan-v1/).

## References

- Washburn et al. 2019. Evolutionarily informed deep learning methods for predicting relative transcript abundance from DNA sequence. *Proceedings of the National Academy of Sciences*. [doi:10.1073/pnas.1814551116](https://doi.org/10.1073/pnas.1814551116)
- Peleke et al. 2024. Deep learning the cis-regulatory code for gene expression in selected model plants. *Nature Communications*. [doi:10.1038/s41467-024-47744-0](https://doi.org/10.1038/s41467-024-47744-0)
- Mendoza-Revilla et al. 2024. A foundational large language model for edible plant genomes. *Communications Biology*. [doi:10.1038/s42003-024-06465-2](https://doi.org/10.1038/s42003-024-06465-2)
- Zhai et al. 2025. Cross-species modeling of plant genomes at single-nucleotide resolution using a pretrained DNA language model. *Proceedings of the National Academy of Sciences*. [doi:10.1073/pnas.2421738122](https://doi.org/10.1073/pnas.2421738122)
