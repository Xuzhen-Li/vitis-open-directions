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

**Background survey (literature read for this plan)**

Deep learning can predict expression from sequence. Across seven model organisms, models trained on more than 20,000 mRNA datasets explained up to 82% of transcript-level variation from the gene regulatory structure ([Zrimec et al. 2020](https://doi.org/10.1038/s41467-020-19921-4)); Enformer improved expression prediction by using long-range interactions in human and mouse ([Avsec et al. 2021](https://doi.org/10.1038/s41592-021-01252-x)). In plants, evolutionarily informed models predicted relative transcript abundance in grasses ([Washburn et al. 2019](https://doi.org/10.1073/pnas.1814551116)), and cis-regulatory models were trained for selected model plants ([Peleke et al. 2024](https://doi.org/10.1038/s41467-024-47744-0)).

DNA language models are trained without labels and used zero-shot or fine-tuned. GPN showed that such models predict genome-wide variant effects in *Arabidopsis* ([Benegas et al. 2023](https://doi.org/10.1073/pnas.2311219120)); AgroNT is a foundation model for edible plant genomes ([Mendoza-Revilla et al. 2024](https://doi.org/10.1038/s42003-024-06465-2)); PlantCaduceus models plant genomes at single-nucleotide resolution across species ([Zhai et al. 2025](https://doi.org/10.1073/pnas.2421738122)). Whether grape was part of the training corpora decides whether a grape test is transfer or within-genus [待确认 per model].

For grape, an expression atlas exists ([Fasoli et al. 2012](https://doi.org/10.1105/tpc.112.100230)) and a transcriptomic platform on a haplotype-resolved genome ([Djari et al. 2024](https://doi.org/10.1073/pnas.2403750121)).

**Specific gap.** No journal paper was found that tests sequence-to-expression models or plant DNA language models on grape with chromosome and gene-family hold-outs and a simple baseline [待确认: only a conference abstract found].

## Question

Do models trained on other plants predict grape expression from sequence better than a grape-only model and a simple baseline?

## Scope update (2026-11-26)

Added 2026-11-26. This section narrows or reframes the plan above; where the two differ, this section applies. Earlier text is kept unchanged.

**New scope: a methods benchmark only.** The project no longer aims to build a new grape model. It asks how well existing models ([Peleke et al. 2024](https://doi.org/10.1038/s41467-024-47744-0); [Mendoza-Revilla et al. 2024](https://doi.org/10.1038/s42003-024-06465-2); [Zhai et al. 2025](https://doi.org/10.1073/pnas.2421738122)) and a simple baseline predict grape expression and allelic differences, and how much leakage changes the answer.

Target: a first-quartile (Q1) journal in plant science, genetics or evolution. Quartile lists change each year, so the journal is chosen from the current list at submission [to confirm]. The points below are what the paper needs to compete at that level.

- Task sets released with fixed splits by chromosome and by gene family, with homology filtering between splits.
- At least two task types: expression class per gene and tissue, and allele-specific expression differences from project 19.
- Every model scored on the same splits, with and without leakage control, against a k-mer or promoter-feature baseline.
- Code and data released so others can add models.

**Fallback.** If no model beats the baseline after leakage control, that is the main result and is preregistered as publishable.

## Hypotheses, planned figures and criteria

No results are given here. Each row says what would count as support; the exact thresholds go into the preregistration.

| Figure or table | Hypothesis or purpose | Criterion |
|---|---|---|
| Fig 1. Held-out performance | Pre-trained models beat the k-mer baseline on held-out chromosomes. | Spearman correlation (expression) or AUC (on/off) with 95% bootstrap intervals; held-out chromosomes and gene families fixed in advance; paralogues kept in the same split. |
| Fig 2. Fine-tuned vs zero-shot, and against a model trained on other plants | Fine-tuning on grape improves over zero-shot use; a sequence-to-expression model trained on other plants serves as the comparison. | Zero-shot means frozen embeddings with a linear probe trained on grape targets; fine-tuning protocol fixed in advance; paired bootstrap on the same test genes with effect sizes. If the pre-training corpus includes *Vitis* [待确认], the result is reported as within-genus rather than transfer. |
| Fig 3. Variant effects | Predicted effects agree in sign with allele-specific expression from project 19. | Sign agreement tested against 50% with one ASE site per gene as the unit; performed only if project 19 yields ASE sites. |

**Expected results and how they will be read**

- Fig 1: if pre-trained models beat the k-mer baseline on held-out chromosomes (paired bootstrap), they carry useful information for grape; if not, the paper reports that current plant models do not transfer to grape expression.
- Fig 2: the gain from fine-tuning over a frozen probe is the practical result for users; it is reported with effect sizes, not only p-values.
- Fig 3 is run only if project 19 yields ASE sites; sign agreement above 50% would support variant-level use, near 50% would not.

## Preregistration

Before any data are analysed, fill in [`docs/PREREGISTRATION.md`](../../../../templates/PREREGISTRATION.md) for this project: hypotheses, primary outcome, sample inclusion rules, thresholds, stop rules and what will be reported if a hypothesis fails. Commit it with a date. Criteria from any earlier attempt are reference only and are not carried over.

## Data

| Module | Dataset |
|---|---|
| [DS01](../../data/DS01-pn40024-references/) | PN40024 references: PN_T2T (v5), PN40024.v4 and 12X |
| [DS15](../../data/DS15-rnaseq-public-vitis/) | Public Vitis RNA-seq and the expression atlas |
| [DS02](../../data/DS02-grapepan-v1/) | Grapepan v1.0: T2T haplotypes, graphs and a 466-accession resequencing panel |

**How each dataset is used**

| Module | Role in this project |
|---|---|
| DS01 | PN_T2T sequence and RefSeq gene models (input windows, splits by chromosome) |
| DS15 | Public RNA-seq for expression targets (through project 19 tables) |
| DS02 | Haplotypes for allele-level tests with project 19 |

New public data: none needed. Model weights come from the published model releases [待确认: licences].

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

**Stepwise work plan with tools**

| Step | Work | Tools (paper) | Output |
|---|---|---|---|
| 1 | Take gene-level expression from project 19 (or rebuild with AM15) | salmon, tximport | Target table |
| 2 | Fix splits by chromosome and gene family; paralogues in the same split | OrthoFinder families | Split file |
| 3 | Baselines: k-mer ridge regression and a grape-only CNN | scikit-learn, PyTorch | Baseline scores |
| 4 | Zero-shot embeddings with a linear probe | AgroNT, PlantCaduceus, GPN (AM22) | Probe scores |
| 5 | Fine-tuning with a fixed protocol | same models | Fine-tuned scores |
| 6 | Paired bootstrap on test genes; Spearman and AUC | R or Python | Fig 1, Fig 2 |
| 7 | Variant-effect sign test against ASE sites | project 19 output | Fig 3 |

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

## Risks and how to handle them

Added 2026-11-26. Each row names a risk, the evidence behind it, and a concrete check or fallback. Sources cited here were read for this section and their DOIs were checked on Crossref; preprints are marked.

| Area | Risk | Check or mitigation |
|---|---|---|
| Data access and licence | The broad RNA-seq set (DS15) is an open query ([data/DOWNLOADS.md](../../data/DOWNLOADS.md)). A grape expression platform exists (VitExpress, [Djari et al. 2024](https://doi.org/10.1073/pnas.2403750121)), but its bulk-download terms were not checked. | Build labels from INSDC runs; use platform data only after its terms are confirmed. |
| Homology leakage | Performance on test sequences rises with their similarity to training sequences, so homology between splits inflates scores ([Rafi et al. 2025](https://doi.org/10.1101/2025.01.22.634321), preprint). | Split train and test by gene family across all species; report scores by similarity bins. |
| Pretraining leakage | Plant DNA language models are pretrained on many angiosperm genomes (16 for PlantCaduceus, [Zhai et al. 2025](https://doi.org/10.1073/pnas.2421738122); 65 for PlantCAD2, [Zhai et al. 2026](https://doi.org/10.1016/j.xgen.2026.101329)). If grape is among them, grape tests are not out-of-species. | Check each model training list for *Vitis* before testing; report grape results separately for models that saw grape. |
| Allelic variation | A model built on PlantCaduceus embeddings predicted between-gene differences well but showed a persistent gap for allelic variation ([Vahedi Torghabeh et al. 2026](https://doi.org/10.64898/2026.02.27.708524), preprint). | Keep variant-level claims to a separate test on allele-specific expression from project 19; do not extend gene-level accuracy to alleles. |
| Pooling across studies | Tissue and study effects in public RNA-seq add label noise (see above). | Fit labels within tissue; compare a model trained on one tissue with one trained on pooled data. |
| Sample size and power | Each gene gives one label per tissue, but genes in one family are not independent; the effective sample is closer to the number of gene families. | Report confidence intervals by bootstrapping families. |
| Computing cost | PlantCAD2 has 676 million parameters ([Zhai et al. 2026](https://doi.org/10.1016/j.xgen.2026.101329)); full fine-tuning needs GPUs. | Use parameter-efficient fine-tuning, as PlantCAD2 did, or frozen embeddings with a small head. |
| Alternative methods and sensitivity | Deep models may not beat simple features. | Always report a baseline on k-mer and UTR-length features. |

**Recent and competing work (search of 2024 to 2026 literature on 2026-11-26)**

- Cross-species expression prediction is now well covered: models for four plants with strong cross-species performance ([Peleke et al. 2024](https://doi.org/10.1038/s41467-024-47744-0)), PlantCAD2 with cross-species expression tasks ([Zhai et al. 2026](https://doi.org/10.1016/j.xgen.2026.101329)), and a 17-species model tested on unseen gene families ([Vahedi Torghabeh et al. 2026](https://doi.org/10.64898/2026.02.27.708524), preprint). A grape transfer test is a case study, not a new method.

**What would end the idea, and the fallback.** If no model beats the simple baseline on held-out grape families, the transfer question has a negative answer. That is still publishable as a benchmark note with the leakage controls above.

**Journal-level realism.** Given how much is now published, a grape benchmark fits a specialty computational or plant genomics journal; mid-field needs a positive allele-level result.

## Reference study in another species

Added 2026-11-26. Published studies that already did this kind of work in another species, to plan the grape version against. Every DOI was checked on Crossref. Figures are described, not copied; a figure redrawn for a grape paper would be marked "Redrawn after" its source. The last bullet for each study lists what a grape results section would need; it is a planning suggestion, not a finding of that study.

### Washburn et al. 2019

- **Paper:** [Washburn et al. 2019](https://doi.org/10.1073/pnas.1814551116), *PNAS*.
- **Note:** Full text not read; figures not checked.
- **Species:** Not checked: the full text was not read.
- **What was done:** From the title: evolutionarily informed deep learning to predict relative transcript abundance from DNA sequence; details not checked.
- **Figures:** Figures not checked.
- **What a grape results section would need:** to confirm after reading the full text [to confirm].

### Mendoza-Revilla et al. 2024

- **Paper:** [Mendoza-Revilla et al. 2024](https://doi.org/10.1038/s42003-024-06465-2), *Communications Biology* (PMC11233511). Licence CC BY 4.0: figures may be reused with credit; none are copied here.
- **Species:** genomes of 48 plant species for pretraining, with tasks in several crops; cassava for in-silico mutagenesis.
- **What was done:** a DNA language model (AgroNT) was evaluated on regulatory annotation, promoter and terminator strength, tissue-specific expression and variant prioritisation; over 10 million cassava mutations were scored in silico; the task datasets were released as the Plants Genomic Benchmark.
- **Figures:** Fig. 1 overview and pretraining genomes; Fig. 2 polyadenylation, splicing and long non-coding RNA tasks; Fig. 3 promoter and terminator strength from STARR-seq; Fig. 4 chromatin accessibility; Fig. 5 expression prediction across species; Fig. 6 promoter input choices in maize; Fig. 7 zero-shot variant effects; Fig. 8 in-silico mutagenesis in cassava.
- **What its results section needed:** several task types with held-out data, comparison against other models, and a released benchmark.
- **Grape version (benchmark only):** grape tasks built like the Plants Genomic Benchmark, with splits by chromosome and gene family, scored for several models and a simple baseline; the released task set is the main output (see Scope update above).
- **Further results a grape version would need:** benchmark tasks on grape (expression prediction R squared, chromatin accessibility, variant effects); comparison with baseline models; performance split by tissue and gene class.

### Q1-level bar

Target: a first-quartile (Q1) journal in plant science, genetics or evolution. Quartile lists change each year, so the journal is chosen from the current list at submission [to confirm]. To compete at that level, the grape paper needs the points listed in the Scope update section above, which applies to this project.

## Rough estimates

- Compute: large (GPU) [draft]
- Effort: 3–5 months for one person [draft]
- Target: computational biology journal [draft]

## Suggested journal level (suggestion only)

**Mid-field journal (computational biology or plant genomics).** The plant model papers read here appeared in *PNAS*, *Nature Communications* and *Communications Biology*; the general models in *Nature Methods*. A transfer benchmark on one crop is a mid-field contribution; a positive variant-level result would strengthen it. This is a suggestion, not a decision; impact factors are not used.

## Continue on HPC

Run each step as its own job, in this order. Every job writes `.DONE` or `.FAILED` and a log; the next step starts only after `.DONE`. Template and rules: [`docs/HPC_JOBS.md`](../../../../templates/HPC_JOBS.md).

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
- Avsec et al. 2021. Effective gene expression prediction from sequence by integrating long-range interactions. *Nature Methods*. [doi:10.1038/s41592-021-01252-x](https://doi.org/10.1038/s41592-021-01252-x)
- Benegas et al. 2023. DNA language models are powerful predictors of genome-wide variant effects. *Proceedings of the National Academy of Sciences*. [doi:10.1073/pnas.2311219120](https://doi.org/10.1073/pnas.2311219120)
- Djari et al. 2024. Haplotype-resolved genome assembly and implementation of VitExpress, an open interactive transcriptomic platform for grapevine. *Proceedings of the National Academy of Sciences*. [doi:10.1073/pnas.2403750121](https://doi.org/10.1073/pnas.2403750121)
- Fasoli et al. 2012. The Grapevine Expression Atlas Reveals a Deep Transcriptome Shift Driving the Entire Plant into a Maturation Program. *The Plant Cell*. [doi:10.1105/tpc.112.100230](https://doi.org/10.1105/tpc.112.100230)
- Zrimec et al. 2020. Deep learning suggests that gene expression is encoded in all parts of a co-evolving interacting gene regulatory structure. *Nature Communications*. [doi:10.1038/s41467-020-19921-4](https://doi.org/10.1038/s41467-020-19921-4)
- Rafi et al. 2025. Characterizing homology-induced data leakage and memorization in genome-trained sequence models. *bioRxiv* (preprint). [doi:10.1101/2025.01.22.634321](https://doi.org/10.1101/2025.01.22.634321)
- Zhai et al. 2026. PlantCAD2: A DNA foundation model for interpreting genomes across flowering plants. *Cell Genomics*. [doi:10.1016/j.xgen.2026.101329](https://doi.org/10.1016/j.xgen.2026.101329)
- Vahedi Torghabeh et al. 2026. Genomic language models improve cross-species gene expression prediction and accurately capture regulatory variant effects in Brachypodium mutant lines. *bioRxiv* (preprint). [doi:10.64898/2026.02.27.708524](https://doi.org/10.64898/2026.02.27.708524)
