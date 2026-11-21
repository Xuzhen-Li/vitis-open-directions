# Status: Large inversions: discovery in assemblies, population genotyping and suppressed recombination

**Status: Partly run** (as of 2026-11-20, UTC+8). Plan: [README.md](README.md). Entry file: [START_HERE.md](../../START_HERE.md).

## Where it stands

An earlier line preregistered a spanning-read test for one large inversion on chromosome 11 (reported in a grape reference) and built a population genotyping table. The test code did not pass its check and the run never finished. Clone removal (project 08) was a prerequisite and was not finished either. Restart as a new study with a general inversion catalogue (the README plan) and keep the chromosome 11 test as one case.

## Design settled earlier (reference only; write a new preregistration before running)

- Spanning-read test: align reads to the whole genome first, then pull reads at the inverted-repeat windows around each breakpoint. Presets: ONT map-ont, HiFi map-hifi, CLR map-pb. Anchors at least 10 kb of unique sequence outside both breakpoint repeats; judge the call from the strand and order of primary and supplementary alignments of the same read [to confirm]. Assign a read to a haplotype only with at least 2 informative SNPs and at least 80% agreement. Use a decision table of five mutually exclusive outcomes; judge hap1, hap2 and the merged set separately; report the two breakpoints separately.
- Population genotyping: classify each deduplicated individual as heterozygous, homozygous inverted, homozygous not inverted, or undetermined,.
- Chromosome 2 (PN T2T against one cultivar): three explanations kept side by side (deletion, copy-neutral LOH, assembly problem); see project 13.
- Check read identity before use: a long-read run whose BioSample differs from the reference accession cannot be assumed to be the reference genotype.

## Where it stopped and why

- The spanning-read code failed its check; a fix was not finished.
- A reads-identity plan for chromosome 11 stayed as a draft.
- Download of long reads from the compute site was slow.

## Next steps

1. Build the sample pool with project 08 (clones removed).
2. Inversion catalogue with SyRI on haplotype alignments (AM06); validate breakpoints with long reads (AM18).
3. Genotype through the graph (AM07); compute differentiation between arrangements and inversion-SNP LD.
4. Re-use the spanning-read design above for the chromosome 11 case, after writing the decision table in the preregistration.

## Open items

- Long-read runs noted earlier: SRR31308326 (PacBio RS II subreads per ENA) and SRR29686478 (PromethION; BioSample differs from the reference); ERR7997743 (a PN40024 CLR run, side evidence only). None was checked against ENA here [to confirm].
- Coordinates of the chromosome 11 inversion against published pangenome papers [to confirm].
- CLR threshold citation [to confirm].

## Sources read

- PN T2T reference: [doi:10.1093/hr/uhad061](https://doi.org/10.1093/hr/uhad061)
- Grapevine pangenome: [doi:10.1038/s41588-024-01967-5](https://doi.org/10.1038/s41588-024-01967-5)
- SyRI: [doi:10.1186/s13059-019-1911-0](https://doi.org/10.1186/s13059-019-1911-0)
- minimap2: [doi:10.1093/bioinformatics/bty191](https://doi.org/10.1093/bioinformatics/bty191)

## Public inputs

| Module | Dataset | Headline accessions (from the module) |
|---|---|---|
| [DS02](../../data/DS02-grapepan-v1/) | Grapepan v1.0: T2T haplotypes, graphs and a 466-accession resequencing panel | Zenodo 10851547, Zenodo 10846425, PRJNA1018808, PRJNA1018809, PRJNA1029477, PRJNA1029480, PRJNA1130629, PRJNA1130651 (see the exact list in data/DOWNLOADS.md) |
| [DS03](../../data/DS03-vitis-super-pangenome-72/) | Vitis super-pangenome: 72 haplotype-resolved accessions | Zenodo 13982444, PRJNA1021789 |
| [DS07](../../data/DS07-cultivated-16-pangenome/) | Cultivated grapevine pangenome (16 cultivars, Plastivigne) | PRJEB100755, PRJEB95058, PRJEB107006 |
| [DS10](../../data/DS10-reseq-472-vitis/) | Resequencing of 472 Vitis accessions (and the 2017 domestication panel) | PRJNA393611, PRJNA388292 |
| [DS01](../../data/DS01-pn40024-references/) | PN40024 references: PN_T2T (v5), PN40024.v4 and 12X | GCF_030704535.1, GCA_030704535.1, PRJNA882193, PRJCA012093, PRJEB45423, GCF_000003745.3, PRJEA18785 |

## Shared steps, in order

| Order | Step | Main tools |
|---|---|---|
| 1 | [AM01](../../analyses/AM01-download-and-verify/) Download and verify | ncbi-datasets-cli, sra-tools, ENA FTP / Aspera |
| 2 | [AM05](../../analyses/AM05-assembly-qc/) Assembly QC | compleasm, BUSCO, Merqury |
| 3 | [AM06](../../analyses/AM06-wga-and-sv/) Whole-genome alignment, synteny and SVs from assemblies | minimap2, SyRI, AnchorWave |
| 4 | [AM07](../../analyses/AM07-graph-build-and-genotype/) Pangenome graph build and genotyping | Minigraph-Cactus, PGGB, vg |
| 5 | [AM18](../../analyses/AM18-long-read-sv/) Long-read SV calling | Sniffles2, cuteSV, pbsv |

## Before any run

- Fill in [docs/PREREGISTRATION.md](../../docs/PREREGISTRATION.md) and commit it with a date before looking at results. Every restart gets a new one; criteria from earlier attempts are reference only.
- Keep an evidence log (template: [docs/EVIDENCE_LOG_TEMPLATE.md](../../docs/EVIDENCE_LOG_TEMPLATE.md)). Add entries only; never edit an old entry.
- Cite only DOIs and URLs you opened yourself. Mark anything else [to confirm].
- Never overwrite outputs: one new run folder per run, ending in .DONE or .FAILED ([docs/HPC_JOBS.md](../../docs/HPC_JOBS.md)).
- Do not commit private data, sample details, results, host names or local paths.

## Update 2026-11-21 (UTC+8)

Added as appended lines; the text above is unchanged.

- The DS02 row in Public inputs abbreviates the accession list. Use the exact list in [data/DOWNLOADS.md](../../data/DOWNLOADS.md) and do not expand it as a range; PRJNA1130635 was not found there.
- Study PRJNA1178252 (which includes SRR31308326) now has its own module, [DS23](../../data/DS23-hemizygous-multiomics-vitis/). It was used here before but was not in the Public inputs table above.
- Run details from ENA on 2026-11-21: SRR31308326 is PacBio RS II subreads (library strategy WGS, Vitis vinifera); SRR29686478 is PromethION (library strategy OTHER, Vitis vinifera) in study PRJNA1048106. The Open items line describes both runs as ONT; for SRR31308326 that does not match ENA. Whether the BioSample of each run matches the reference is still not checked [to confirm].
- Suggested refinement of the spanning-read test, not yet adopted [to confirm]: require each spanning read to cover unique sequence outside both breakpoint repeats, and judge the call from the strand and order of the primary and supplementary alignments of the same read on the two sides of the breakpoint. Reason: when the repeats that mediate an inversion are near or longer than the read length, a single whole-genome alignment can split or down-weight such reads. How often this happens in the Vitis data has not been tested.
