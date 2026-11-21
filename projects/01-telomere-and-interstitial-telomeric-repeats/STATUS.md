# Status: Telomeres and interstitial telomeric repeats across near-complete grape haplotypes

**Status: Partly run** (as of 2026-11-20, UTC+8). Plan: [README.md](README.md). Entry file: [START_HERE.md](../../START_HERE.md).

## Where it stands

An earlier scan of near-complete angiosperm and Vitaceae assemblies used a fixed motif definition. Its decoy-motif negative control did not pass, and some thresholds were changed after results had been seen. That run was therefore closed as descriptive and exploratory, and nothing from it counts as confirmatory. This project restarts from public assemblies as a new study (new question, new preregistration), not as a continuation.

## Design settled earlier (reference only; write a new preregistration before running)

- Main plant telomere motif TTTAGGG, scanned on both strands: the seven rotations of TTTAGGG and the seven rotations of the reverse complement CCCTAAA.
- Two layers. Clean layer: a 7-bp window equals a rotation exactly. Degraded layer: at most one mismatch per 7-bp window. Arrays of the vertebrate-type TTAGGG repeat only enter the degraded layer; report TTAGGG as a separate control motif instead of adding it to the main motif, and subtract it only from clean-layer positions.
- Segment rule: take runs of at least 7 consecutive window start positions that all match (one full cycle of the 7 phases); merge runs on the same layer and strand when the gap is 7 bp or less; keep a segment only if it is at least 50 bp long and at least 80% of its bases are covered by matching windows.
- Scan in 10 Mb chunks that overlap by 14 bp and merge across chunk edges. Read FASTA files in byte blocks, because some assemblies store each chromosome on one line.
- The strand column of the degraded layer leans to the positive strand; do not use it for strand analysis. The cause was not found; scan both strands separately [to confirm the cause].
- Gates before any main result is read: a grid test on known sequence, a decoy-motif negative control, a positive control on an Arabidopsis T2T assembly, and a comparison on a few near-complete assemblies with known chromosome ends. Fix pass levels in the preregistration, and do not change them after seeing results.
- Motif checks: the main motif was not confirmed from the sources opened for grasses (maize, rice, sorghum), Brassica and Capsella, so these were left out of the denominator for the share of chromosome ends with a telomere [to confirm]. Tomato carries a TTAGGG-type variant.

## Where it stopped and why

- The negative control failed, so the decision rule sent the run to a descriptive report.
- Later threshold changes were made after results were visible, which makes them post-hoc.
- No confirmatory result exists.

## Next steps

1. AM01 and AM05 on the assembly list from DS16, with DS17 as comparison set; keep a manifest with checksums.
2. Write a new preregistration (docs/PREREGISTRATION.md) that states the decoy design and pass levels before any scan.
3. Pilot on at most 15 assemblies that include same-species haplotype pairs; run tidk and TRF (AM10).
4. Full run only after the controls pass; test ITS enrichment at known breakpoints, including the *Vitis* chr7 fusion point shared with project 18.

## Open items

- Whether TeloBase and T2T-Hub report interstitial repeats [to confirm].
- The number of accessions in the preprint on Arabidopsis repeat domains [to confirm].
- Repeat the novelty search before writing [to confirm].

## Sources read

- TeloBase: [doi:10.1093/nar/gkad672](https://doi.org/10.1093/nar/gkad672)
- T2T-Hub: [doi:10.1093/nar/gkag423](https://doi.org/10.1093/nar/gkag423)
- Brassicaceae chromosome fusions: [doi:10.1038/s41467-025-59640-2](https://doi.org/10.1038/s41467-025-59640-2)
- Arabidopsis interstitial repeat domains (preprint, not yet in a journal): [doi:10.64898/2026.05.10.723265](https://doi.org/10.64898/2026.05.10.723265)
- Telomere repeat mapping in tomato: [doi:10.1016/s0888-7543(05)80239-3](https://doi.org/10.1016/s0888-7543(05)80239-3)
- Tandem Repeats Finder: [doi:10.1093/nar/27.2.573](https://doi.org/10.1093/nar/27.2.573)
- Maize telomere repeat: [doi:10.1105/tpc.4.8.953](https://doi.org/10.1105/tpc.4.8.953) (abstract only: a seven-base repeat, sequence not stated there)

## Public inputs

| Module | Dataset | Headline accessions (from the module) |
|---|---|---|
| [DS01](../../data/DS01-pn40024-references/) | PN40024 references: PN_T2T (v5), PN40024.v4 and 12X | GCF_030704535.1, GCA_030704535.1, PRJNA882193, PRJCA012093, PRJEB45423, GCF_000003745.3, PRJEA18785 |
| [DS02](../../data/DS02-grapepan-v1/) | Grapepan v1.0: T2T haplotypes, graphs and a 466-accession resequencing panel | Zenodo 10851547, Zenodo 10846425, PRJNA1018808, PRJNA1018809, PRJNA1029477, PRJNA1029480, PRJNA1130629, PRJNA1130651 (see the exact list in data/DOWNLOADS.md) |
| [DS03](../../data/DS03-vitis-super-pangenome-72/) | Vitis super-pangenome: 72 haplotype-resolved accessions | Zenodo 13982444, PRJNA1021789 |
| [DS05](../../data/DS05-vitaceae-family-genomes/) | Vitaceae family chromosome-level genomes | PRJEB88780, PRJNA1219332, PRJNA1021789, figshare 33329247, Zenodo 18590277 |
| [DS07](../../data/DS07-cultivated-16-pangenome/) | Cultivated grapevine pangenome (16 cultivars, Plastivigne) | PRJEB100755, PRJEB95058, PRJEB107006 |
| [DS08](../../data/DS08-muscadinia-genomes/) | Muscadinia rotundifolia assemblies and reads | Zenodo 3866087, PRJNA593045, Zenodo 7944874, PRJNA935741, PRJNA780568 |
| [DS16](../../data/DS16-vitaceae-assembly-index/) | Index of all Vitaceae assemblies in NCBI | see the module |
| [DS17](../../data/DS17-angiosperm-near-complete-assemblies/) | Near-complete angiosperm assemblies (comparison set) | see the module |

## Shared steps, in order

| Order | Step | Main tools |
|---|---|---|
| 1 | [AM01](../../analyses/AM01-download-and-verify/) Download and verify | ncbi-datasets-cli, sra-tools, ENA FTP / Aspera |
| 2 | [AM05](../../analyses/AM05-assembly-qc/) Assembly QC | compleasm, BUSCO, Merqury |
| 3 | [AM10](../../analyses/AM10-repeat-arrays/) Telomeres, centromeric satellites and rDNA arrays | tidk, TRF, TRASH |

## Before any run

- Fill in [docs/PREREGISTRATION.md](../../docs/PREREGISTRATION.md) and commit it with a date before looking at results. Every restart gets a new one; criteria from earlier attempts are reference only.
- Keep an evidence log (template: [docs/EVIDENCE_LOG_TEMPLATE.md](../../docs/EVIDENCE_LOG_TEMPLATE.md)). Add entries only; never edit an old entry.
- Cite only DOIs and URLs you opened yourself. Mark anything else [to confirm].
- Never overwrite outputs: one new run folder per run, ending in .DONE or .FAILED ([docs/HPC_JOBS.md](../../docs/HPC_JOBS.md)).
- Do not commit private data, sample details, results, host names or local paths.

## Update 2026-11-21 (UTC+8)

Added as appended lines; the text above is unchanged.

- The DS02 row in Public inputs abbreviates the accession list. Use the exact list in [data/DOWNLOADS.md](../../data/DOWNLOADS.md) and do not expand it as a range; PRJNA1130635 was not found there.
- The positive-strand lean of the degraded layer is not explained in the records. Until a cause is found, scan both strands separately and report them separately. A strand preference in the earlier scan script is one possible cause; it was not shown [to confirm].
