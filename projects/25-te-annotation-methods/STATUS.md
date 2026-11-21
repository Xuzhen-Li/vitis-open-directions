# Status: Transposable-element annotation methods, library curation and automation

**Status: Plan fixed** (as of 2026-11-21, UTC+8). Entry file: [START_HERE.md](../../START_HERE.md). Related public catalogue: [vitis-te](https://github.com/Xuzhen-Li/vitis-te). Related analysis project: [project 14](../14-te-insertion-polymorphisms-cultivated/STATUS.md).

## Where it stands

A writing plan for a methods-centred survey of transposable-element (TE) annotation was set earlier: detection (several generations of methods), manual curation as a methods topic in its own right, automation (pipelines and machine learning), and the evidence used to judge whether an annotation is good. Plants are the main thread; published grape assemblies and pangenomes are case studies only. An earlier, grape-and-clonal-perennial angle was set aside and kept as a historical plan; it is not the current angle.

The literature list and chapter plan exist outside this repository. No manuscript has been added here, and no unpublished annotation or insertion-polymorphism results are included. This page records the method-level plan so the line is visible next to the analysis projects.

## Design settled earlier (reference only; lock the outline before drafting text)

- Scope: homology search and reference libraries; de novo discovery; structure-based detectors; combined pipelines; manual curation and its automation; machine-learning classification; classification systems; benchmarks; long-read, T2T and pangenome annotation. Years 1990s-2026, with emphasis after 2019.
- Out of scope for the main text: TE biology, traits and expression (at most a short opening); prokaryotic insertion sequences; preprint-only tools, if used, stay in a short recent-work note.
- Population insertion polymorphisms, if included, stay a short section, not the centre of the article.
- Do not use unpublished datasets or unpublished haplotype catalogues as evidence.
- Classification: the Wicker system and the 80-80-80 family rule are the coordinate system; they are a convention, not a biological boundary (Wicker et al. 2007).
- Example method families to cover (from the plan, with published tool papers): RepeatMasker and Dfam or Repbase; RepeatModeler and related de novo tools; LTR and TIR structure detectors; combined pipelines such as EDTA (Ou et al. 2019) and later pangenome-aware workflows; curation protocols.

## Where it stopped and why

The angle and outline were written. Drafting of the public article in this repository has not started. Project 14 remains the place for a public-data insertion-polymorphism analysis; this project is the methods survey.

## Next steps

1. Lock the outline, journal choice and inclusion rules in a new preregistration for the article, then draft only from published sources.
2. Keep the split with project 14 and with the vitis-te catalogue explicit (see docs/DEFAULTS.md for the default split).
3. Add a table of published grape TE annotations and libraries as the case-study section: the PN40024 TE annotation file in Zenodo 7751391 (listed in data/DOWNLOADS.md), any TE annotations released with the published pangenomes (DS02, DS03) [to confirm which deposits include them], and the grape retrotransposon insertion that changes berry colour (Kobayashi et al. 2004). Record only DOIs and accessions that were opened.
4. When citing tools, open the tool paper or official page and quote only what was read.

## Open items

- Journal choice [to confirm].
- Whether project 14 and the vitis-te catalogue should be merged or split, and how this survey sits beside them [to confirm].
- Official word and figure limits for the chosen journal [to confirm].
- Cut-off date for preprints [to confirm].

## Sources read

All entries below were opened as Crossref records on 2026-11-21 (abstract level; full text not read).

- Wicker et al. 2007, a unified classification system for eukaryotic transposable elements: [doi:10.1038/nrg2165](https://doi.org/10.1038/nrg2165)
- Ou et al. 2019, benchmarking TE annotation methods and the EDTA pipeline: [doi:10.1186/s13059-019-1905-y](https://doi.org/10.1186/s13059-019-1905-y)
- Sierra et al. 2024, identification of transposable element families from pangenome polymorphisms: [doi:10.1186/s13100-024-00323-y](https://doi.org/10.1186/s13100-024-00323-y)
- Shi et al. 2023, complete PN40024 reference genome: [doi:10.1093/hr/uhad061](https://doi.org/10.1093/hr/uhad061)
- Liu et al. 2024, grapevine pangenome: [doi:10.1038/s41588-024-01967-5](https://doi.org/10.1038/s41588-024-01967-5)
- Guo et al. 2025, super pangenome of Vitis: [doi:10.1038/s41588-025-02111-7](https://doi.org/10.1038/s41588-025-02111-7)
- Kobayashi et al. 2004, retrotransposon-induced mutations in grape skin colour: [doi:10.1126/science.1095011](https://doi.org/10.1126/science.1095011)
- [Project 14 STATUS](../14-te-insertion-polymorphisms-cultivated/STATUS.md) in this repository

## Public inputs

| Module or source | What it provides | Headline accessions or URL |
|---|---|---|
| [DS01](../../data/DS01-pn40024-references/) | Public T2T and v4 references used as published cases; the PN_T2T deposit includes a TE annotation file | GCF_030704535.1, PRJEB45423, Zenodo 7751391, doi:10.57745/F9N2FZ |
| [DS02](../../data/DS02-grapepan-v1/) | Published pangenome haplotypes and graph | Zenodo 10851547, Zenodo 10846425, PRJNA1048106 |
| [DS03](../../data/DS03-vitis-super-pangenome-72/) | Super-pangenome haplotypes (published case) | Zenodo 13982444, PRJNA1021789 |
| [DS05](../../data/DS05-vitaceae-family-genomes/) | Vitaceae family chromosome-level genomes (comparison) | PRJEB88780, PRJNA1021789 |
| [DS16](../../data/DS16-vitaceae-assembly-index/) | Index of all Vitaceae assemblies in NCBI | assemblies_vitaceae_ncbi_20261114.tsv |
| [vitis-te](https://github.com/Xuzhen-Li/vitis-te) | Public methods catalogue for TE classes and tools | repository on GitHub |
| Project 14 | Public-data insertion-polymorphism analysis plan | see that STATUS page |

## Shared steps, in order

| Order | Step | Main tools |
|---|---|---|
| 1 | Lock the outline and the source list from published papers | Crossref or DataCite for each DOI |
| 2 | Optional: rerun published pipelines on public assemblies only, if a methods figure needs a worked example, and only after a preregistration | EDTA and related tools, versions to pin [to confirm] |
| 3 | Draft the text from opened sources only | none |

## Before any run

- Fill in [docs/PREREGISTRATION.md](../../docs/PREREGISTRATION.md) and commit it with a date before looking at results or writing claims from a new comparison. Every restart gets a new one; criteria from earlier attempts are reference only.
- Keep an evidence log (template: [docs/EVIDENCE_LOG_TEMPLATE.md](../../docs/EVIDENCE_LOG_TEMPLATE.md)). Add entries only; never edit an old entry.
- Cite only DOIs and URLs you opened yourself. Mark anything else [to confirm].
- Never overwrite outputs: one new run folder per run, ending in .DONE or .FAILED ([docs/HPC_JOBS.md](../../docs/HPC_JOBS.md)).
- Do not commit private data, sample details, results, host names or local paths.
