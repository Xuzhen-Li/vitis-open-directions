# 03. Endogenous florendovirus insertions across grape haplotypes

中文：葡萄泛基因组中的内源 florendovirus

Rank 3 of 22 (score F 3 + N 2 + E 2 = 7; see docs/RANKING.md) · Tier: Medium (E = 2, effort range ending after 6 weeks and by 4 months) · Origin: new · Status: draft v0.3.2, 2026-11-14

## Gap

Endogenous florendovirus insertions were described from single references. Presence/absence of each insertion across haplotypes and wild *Vitis* is not catalogued [待确认].

**Existing work**

- [Geering et al. 2014](https://doi.org/10.1038/ncomms6269): florendoviruses in many angiosperm genomes, including grape.
- [Bertsch et al. 2009](https://doi.org/10.1186/1745-6150-4-21): endogenous pararetrovirus sequences in grape.

**How this project differs**

Treats each insertion as a locus and genotypes it across haplotypes by flanking synteny.

## Question

Which florendovirus insertions are shared by all grapes and which are polymorphic, and does sharing follow the species tree?

## Hypotheses, planned figures and criteria

No results are given here. Each row says what would count as support; the exact thresholds go into the preregistration.

| Figure or table | Hypothesis or purpose | Criterion |
|---|---|---|
| Fig 1. Insertion catalogue per haplotype | Not a hypothesis: catalogue. | Insertions defined by protein similarity plus flanking synteny; similarity and synteny thresholds fixed in advance. |
| Fig 2. Polymorphic vs fixed insertions | Polymorphic insertions are less degraded (younger) than fixed ones. | ORF integrity (complete or incomplete) compared between classes with Fisher's exact test or logistic regression, and divergence with a rank test; one-sided direction stated in advance. |
| Fig 3. Sharing pattern vs species tree | Orthologous insertions are shared consistently with the species tree. | Consistency index on the species tree compared with trees whose leaf labels are permuted (permutation scheme fixed in advance). |

## Preregistration

Before any data are analysed, fill in [`docs/PREREGISTRATION.md`](../../docs/PREREGISTRATION.md) for this project: hypotheses, primary outcome, sample inclusion rules, thresholds, stop rules and what will be reported if a hypothesis fails. Commit it with a date. Criteria from any earlier attempt are reference only and are not carried over.

## Data

| Module | Dataset |
|---|---|
| [DS01](../../data/DS01-pn40024-references/) | PN40024 references: PN_T2T (v5), PN40024.v4 and 12X |
| [DS02](../../data/DS02-grapepan-v1/) | Grapepan v1.0: T2T haplotypes, graphs and a 466-accession resequencing panel |
| [DS03](../../data/DS03-vitis-super-pangenome-72/) | Vitis super-pangenome: 72 haplotype-resolved accessions |
| [DS04](../../data/DS04-na-vitis-super-pangenome/) | North American Vitis super-pangenome and wild resequencing |
| [DS05](../../data/DS05-vitaceae-family-genomes/) | Vitaceae family chromosome-level genomes |
| [DS06](../../data/DS06-vitis-amurensis-pangenome/) | Vitis amurensis haplotype assemblies and 330-sample resequencing |

## Analysis steps

Shared modules, in order:

1. [AM01 · Download and verify](../../analyses/AM01-download-and-verify/)
2. [AM05 · Assembly QC](../../analyses/AM05-assembly-qc/)
3. [AM16 · Virus discovery in RNA-seq and endogenous viral elements in assemblies](../../analyses/AM16-virus-and-eve-search/)
4. [AM06 · Whole-genome alignment, synteny and SVs from assemblies](../../analyses/AM06-wga-and-sv/)

Project-specific steps:

- Search assemblies with florendovirus protein seeds (AM16, DIAMOND).
- Cluster hits into loci by flanking sequence (AM06).
- Score each locus present or absent per haplotype; build the matrix.

## Paper design and split

| Paper | Working title | Type | Figures |
|---|---|---|---|
| C1 | Endogenous florendoviruses across the grape pangenome | short paper | Fig 1–3 |

Each paper: introduction from the gap above; one results section per figure; methods with tool versions from the modules; data availability listing every accession used and the derived tables.

## Risks and novelty check

- Risk: Fragmented viral copies may be missed or merged.
- Risk: Flanks inside repeats make orthology uncertain.
- Risk: Novelty: no dedicated literature search on this topic has been done beyond the grape literature base yet [待确认: repeat the search before writing].
- Novelty: checked against the existing work above (Crossref-verified DOIs). Repeat the search before writing; anything marked [待确认] is not yet verified.

## Rough estimates

- Compute: small [draft]
- Effort: 1–2 months for one person [draft]
- Target: virology or genome journal [draft]

## Continue on HPC

Run each step as its own job, in this order. Every job writes `.DONE` or `.FAILED` and a log; the next step starts only after `.DONE`. Template and rules: [`docs/HPC_JOBS.md`](../../docs/HPC_JOBS.md).

| Order | Step | Main tools | Resources (rough) |
|---|---|---|---|
| 1 | [AM01](../../analyses/AM01-download-and-verify/) Download and verify | ncbi-datasets-cli, sra-tools, ENA FTP / Aspera | 1–4 CPU, 4 GB, network; array over files |
| 2 | [AM05](../../analyses/AM05-assembly-qc/) Assembly QC | compleasm, BUSCO, Merqury | 16 CPU, 64 GB, 1–3 h per assembly; array |
| 3 | [AM16](../../analyses/AM16-virus-and-eve-search/) Virus discovery in RNA-seq and endogenous viral elements in assemblies | DIAMOND, MEGAHIT, SPAdes (rnaviralSPAdes) | 16 CPU, 64 GB per run for assembly |
| 4 | [AM06](../../analyses/AM06-wga-and-sv/) Whole-genome alignment, synteny and SVs from assemblies | minimap2, SyRI, AnchorWave | 16 CPU, 64 GB, 1–4 h per haplotype; array |

Public inputs: [DS01](../../data/DS01-pn40024-references/), [DS02](../../data/DS02-grapepan-v1/), [DS03](../../data/DS03-vitis-super-pangenome-72/), [DS04](../../data/DS04-na-vitis-super-pangenome/), [DS05](../../data/DS05-vitaceae-family-genomes/), [DS06](../../data/DS06-vitis-amurensis-pangenome/).

## References

- Geering et al. 2014. Endogenous florendoviruses are major components of plant genomes and hallmarks of virus evolution. *Nature Communications*. [doi:10.1038/ncomms6269](https://doi.org/10.1038/ncomms6269)
- Bertsch et al. 2009. Retention of the virus-derived sequences in the nuclear genome of grapevine as a potential pathway to virus resistance. *Biology Direct*. [doi:10.1186/1745-6150-4-21](https://doi.org/10.1186/1745-6150-4-21)
