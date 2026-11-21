# Status: Pedigree and linkage-disequilibrium recombination maps in grape

**Status: Plan fixed** (as of 2026-11-21, UTC+8). Entry file: [START_HERE.md](../../../../START_HERE.md). Depends on the public relationship work in [project 23](../23-family-parentage/STATUS.md). Feeds [project 10](../10-arg-domestication-timing/STATUS.md), which uses published linkage maps and treats LD-based rates only as an input.

## Where it stands

A detailed, conditional design for estimating recombination was written earlier and has not been run. It distinguishes several quantities that must not be treated as the same thing: (i) candidate crossover intervals in a single transmission; (ii) a recent pedigree recombination quantity (r_ped), with the exact estimand still to be locked; (iii) map distance in centimorgans; (iv) a historical quantity estimated from linkage disequilibrium and related information (rho_LD), which depends on demography, phasing and the callable region, and is not the same as linkage disequilibrium itself; (v) mosaic ancestry after many generations of breeding. A unit conversion does not calibrate rho_LD and r_ped. Subtracting one ranking from the other is not evidence of selection, structural variation or introgression.

The earlier design allowed a pedigree-first route when local transmissions are measurable, and a separate historical linkage-disequilibrium route with its own checks. Failure of one route does not make the other valid. A private genotype panel and a private reference from that design are not in this repository (panel size, accession and hash [to confirm]). This page states the method only. Public work can compare against published grape maps and, if wanted, estimate linkage-disequilibrium rates on public panels, with the limits already noted in AM26.

## Design settled earlier (reference only; write a new preregistration before running)

- A crossover is an interval. The midpoint is not base-pair precision. A published average map spacing is not the resolution of this project.
- Lack of signal in a structural-variant region may be a detection gap; it is not automatically recombination suppression. Missing local information is NA, not zero and not a cold spot.
- Short haplotype-origin switches are a mixed observation (true close crossovers, genotype or phase error, gene conversion, or a double crossover) and are not labelled as crossovers by default.
- If a published map was used to phase, call, filter or tune, it cannot also be the independent truth for the same result.
- Software-to-software agreement, or agreement after linkage-disequilibrium-aided phasing, is a sensitivity check, not independent validation.
- Preset report terms when a claim cannot be made: not estimable, not identified, untested, hypothesis not supported, not independently validated, comparison not performed, disagreement.
- Do not present the work as the first such map; a limited literature search is not proof that none exists.

## Where it stopped and why

The design is complete as a conditional plan. No estimation, simulation or pilot was run. All analysis gates in that plan were left closed.

## Next steps

1. Finish the public relationship inventory in project 23 before any pedigree-based map.
2. For a public linkage-disequilibrium estimate: build clone-free, unrelated sample sets per group (for example wild V. vinifera subsp. sylvestris, wine and table cultivars) from project 08 outputs (DS10, DS12, DS02; DS11 only after its run list can be exported). Estimate each group on its own, because bottlenecks, structure and clonal propagation distort rho_LD.
3. Phase with SHAPEIT5 (AM26) on PN_T2T, mask centromeres and low-mappability repeats, and fix window sizes and the minimum sample count per group in the preregistration.
4. Estimate rho_LD with pyrho or LDhelmet as listed in AM26. The population-size history input and its tool are not fixed (project 10 and AM14 list Relate; SMC++ is another option) [to confirm].
5. Compare the window-level rates with published maps (cM per Mb) as a descriptive check only; do not use the maps to calibrate rho_LD, and do not release a map as a product without its own preregistration.
6. Pedigree interval calling only if public families exist and a preregistration locks the estimand.

## Open items

- Which published map has enough markers to interpolate onto PN_T2T [to confirm] (also open in AM26).
- Whether a public-only pedigree map is feasible once project 23 is done [to confirm].
- Window sizes, group definitions and minimum sample count per group [to confirm].
- Population-size history tool [to confirm].
- Accession of the private reference from the earlier design [to confirm].

## Sources read

All entries below were opened as Crossref records on 2026-11-21 (abstract level; full text not read).

- Vervalle et al. 2022, high-density integrated grapevine map, three mapping populations, Vitis18K SNP chip: [doi:10.1007/s00122-022-04225-6](https://doi.org/10.1007/s00122-022-04225-6)
- Zou et al. 2020, haplotyping the Vitis collinear core genome with rhAmpSeq: [doi:10.1038/s41467-019-14280-1](https://doi.org/10.1038/s41467-019-14280-1)
- Xiao et al. 2025, reproductive systems, grapevine genome and breeding: [doi:10.1038/s41467-025-56817-7](https://doi.org/10.1038/s41467-025-56817-7)
- Morales-Cruz et al. 2021, introgression among North American wild grapes: [doi:10.1186/s13059-021-02467-z](https://doi.org/10.1186/s13059-021-02467-z)
- Delame et al. 2019, introgression and recombination distribution in interspecific grapevine hybrids: [doi:10.1007/s00122-018-3260-x](https://doi.org/10.1007/s00122-018-3260-x)
- Broman et al. 2003, R/qtl: [doi:10.1093/bioinformatics/btg112](https://doi.org/10.1093/bioinformatics/btg112)
- Spence and Song 2019, population-specific fine-scale recombination maps (the pyrho paper): [doi:10.1126/sciadv.aaw9206](https://doi.org/10.1126/sciadv.aaw9206)
- Hofmeister et al. 2023, SHAPEIT5 phasing: [doi:10.1038/s41588-023-01415-w](https://doi.org/10.1038/s41588-023-01415-w)
- Shi et al. 2023, complete PN40024 reference genome: [doi:10.1093/hr/uhad061](https://doi.org/10.1093/hr/uhad061)
- [AM26](../../analyses/AM26-phasing-polarisation-recombination/) in this repository (SHAPEIT5, pyrho, LDhelmet; published maps as the default)

## Public inputs

| Module | Dataset | Headline accessions (from the module) |
|---|---|---|
| [DS01](../../data/DS01-pn40024-references/) | PN40024 references: PN_T2T (v5) as the coordinate system | GCF_030704535.1, PRJEB45423, GCF_000003745.3 |
| [DS10](../../data/DS10-reseq-472-vitis/) | Resequencing of 472 Vitis accessions | PRJNA393611, PRJNA388292 |
| [DS12](../../data/DS12-reseq-204-magris2021/) | Resequencing of 204 V. vinifera accessions | PRJNA373967, PRJNA390884, PRJNA385116, PRJNA321480 |
| [DS02](../../data/DS02-grapepan-v1/) | Grapepan v1.0 resequencing panel | PRJNA994294 (see the exact list in data/DOWNLOADS.md) |
| [DS11](../../data/DS11-reseq-3525-dong2023/) | Resequencing of 3,525 grapevine accessions; reads cannot be listed without an NGDC login, see data/DOWNLOADS.md | PRJCA009314, CRA006917 |
| [DS08](../../data/DS08-muscadinia-genomes/) | Muscadinia assemblies (outgroup, if polarisation is needed) | PRJNA593045, PRJNA935741, PRJNA780568 |

## Shared steps, in order

| Order | Step | Main tools |
|---|---|---|
| 1 | [Project 23](../23-family-parentage/STATUS.md) and [AM04](../../analyses/AM04-sample-identity/) | plink2, KING |
| 2 | [AM26](../../analyses/AM26-phasing-polarisation-recombination/) Phasing and, if locked, linkage-disequilibrium rates | SHAPEIT5, pyrho or LDhelmet |
| 3 | Pedigree interval calling, only if public families exist and a preregistration locks the estimand | R/qtl, duoHMM (methods from the papers cited above; versions to pin [to confirm]) |

## Before any run

- Fill in [docs/PREREGISTRATION.md](../../../../templates/PREREGISTRATION.md) and commit it with a date before looking at results. Every restart gets a new one; criteria from earlier attempts are reference only.
- Keep an evidence log (template: [docs/EVIDENCE_LOG_TEMPLATE.md](../../../../templates/EVIDENCE_LOG_TEMPLATE.md)). Add entries only; never edit an old entry.
- Cite only DOIs and URLs you opened yourself. Mark anything else [to confirm].
- Never overwrite outputs: one new run folder per run, ending in .DONE or .FAILED ([docs/HPC_JOBS.md](../../../../templates/HPC_JOBS.md)).
- Do not commit private data, sample details, results, host names or local paths.

## Note, 2026-11-21 (UTC+8): place in the six-dimension map

Dimension 4 (population, domestication and reproductive system). Proposed on 2026-11-21: method line linked to projects 23 and 10. LD-based and pedigree recombination rates are kept apart. This project has a STATUS page only, with no README and no F/N/E score; whether to add them is [to confirm]. Read it together with [METHOD_LINES.md](../../METHOD_LINES.md). This is a proposal, not a decision: nothing in RANKING.md changes and the folder stays as it is. The full direction map is in [examples/vitis/README.md](../../README.md).
