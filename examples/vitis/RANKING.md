# Ranking

Scores were frozen on 2026-11-14 (UTC+8). Each project is scored 1–3 on three axes and ranked by the **sum** F + N + E (not the product). Any later change is recorded in the adjustment register at the end of this page with the date, the old and new values, the reason, and whether any results had been seen.

- **Feasibility (F)**: can it be done with public data now? 3 = all inputs are public and their accessions were checked in the archive APIs; 2 = inputs are public, but some require manual curation, are only partly suitable (for example gapped assemblies, or calibration data from one cultivar), or carry unverified accessions; 1 = depends on data that may not be public (phenotypes, recorded sex, documented dates). F is scored on the project's main paper; data needed only by a follow-up paper are stated in that project's paper split (for example, the rate paper of project 13 requires documented clone dates).
- **Novelty (N)**: after the literature checks. 3 = not found in grape; 2 = partly done, with a clear narrower gap remaining; 1 = mostly done, with only a small or technical gap remaining. Novelty is judged within grape only: a precedent in another species does not lower the score.
- **Effort (E), higher = less effort**: each project's effort range is given in its README under Rough estimates, and a project is assigned by the upper end of that range. 3 = upper end at most 6 weeks for one person; 2 = upper end more than 6 weeks and at most 4 months; 1 = upper end more than 4 months, or a step with a stated high risk of having to start again (calibration, GPU training).

| Upper end of the estimated effort | E | Tier |
|---|---|---|
| 6 weeks or less | 3 | Quick |
| more than 6 weeks, up to 4 months | 2 | Medium |
| more than 4 months, or a high-risk step | 1 | Large |

Projects are sorted by total score, highest first. Equal totals are broken in this order: (a) lower E first, so that the project with higher F + N comes before the faster one; (b) higher N; (c) the project's number in the previous draft (v0.2), given in the Previous # column so the order can be checked.

Scores were set by one integrator from the literature checks and then compared with an independent second scoring (see Independent re-scoring below); every score changed as a result is recorded in the adjustment register.

| # | Project | F | N | E | Total | Tier | Previous # | Why this rank |
|---|---|---|---|---|---|---|---|---|
| 01 | [Telomeres and interstitial telomeric repeats across near-complete grape haplotypes](projects/01-telomere-and-interstitial-telomeric-repeats/) | 3 | 2 | 3 | 8 | Quick | 01 | Assemblies are already public and the scan is cheap; single T2T papers report telomeres, but no cross-haplotype comparison was found. |
| 02 | [45S and 5S rDNA arrays in near-complete grape assemblies](projects/02-rdna-arrays/) | 3 | 2 | 3 | 8 | Quick | 02 | Uses assemblies only; arrays are often truncated, so the product is a careful catalogue with completeness flags. |
| 03 | [Endogenous florendovirus insertions across grape haplotypes](projects/03-endogenous-florendoviruses/) | 3 | 2 | 2 | 7 | Medium | 03 | Requires assemblies only and small compute, but the estimated effort is 1–2 months, so E = 2; insertion presence/absence across haplotypes was not found. |
| 04 | [Virus discovery across public grape RNA-seq and unmapped reads](projects/04-virus-discovery-in-public-data/) | 3 | 2 | 2 | 7 | Medium | 04 | Data are public but large (all public grape RNA-seq runs), and the estimated effort is 1–2 months, so E = 2 and the tier is Medium, not Quick. |
| 05 | [Gene presence/absence across grape pangenomes under one pipeline](projects/05-gene-pav-across-pangenomes/) | 3 | 2 | 2 | 7 | Medium | 06 | All inputs are public; pangenomes report PAV with different pipelines, and a unified comparison was not found. |
| 06 | [A genus-wide NLR catalogue with integrated domains and collapse checks](projects/06-vitis-pan-nlrome/) | 3 | 2 | 2 | 7 | Medium | 07 | Public haplotypes span cultivated, North American, Asian and *Muscadinia* lineages; a genus-wide catalogue with integrated domains was not found. |
| 07 | [Copy number and birth–death of stilbene and aroma gene families (STS, TPS, CCD, LOX)](projects/07-metabolic-gene-families/) | 3 | 2 | 2 | 7 | Medium | 08 | Family studies exist for single references; birth–death rates across many near-complete haplotypes were not found. Splits into two papers. |
| 08 | [A harmonised identity table for public grape resequencing panels](projects/08-harmonised-sample-panel/) | 3 | 2 | 2 | 7 | Medium | 09 | A shared base for most population projects here; clone identification and cultivar-origin studies exist, but no cross-panel identity resource was found. |
| 09 | [Graph genotyping of the berry colour locus](projects/09-berry-colour-locus-graph/) | 3 | 1 | 3 | 7 | Quick | 10 | Quick, uses public graphs and panels; novelty is limited because the locus and its sports are well studied. |
| 10 | [Ancestral recombination graphs for hundreds of grape genomes and domestication timing](projects/10-arg-domestication-timing/) | 2 | 3 | 1 | 6 | Large | 11 | The only direction confirmed as not done, but calibration under clonal propagation is a real risk, so it ranks below the quicker projects. |
| 11 | [Sequence-to-expression models and plant foundation models evaluated on grape](projects/11-sequence-to-function-models/) | 2 | 3 | 1 | 6 | Large | 12 | Only a conference abstract exists for grape; T2T and many RNA-seq runs are public. E = 1 because the estimated effort reaches 5 months and GPU access and leakage control are high-risk steps. |
| 12 | [Convergent domestication: grape compared with other crops in one pipeline](projects/12-convergent-domestication-cross-crop/) | 2 | 3 | 1 | 6 | Large | 13 | Public data are ample and the comparison was not found; the hard parts are the null model and orthology. |
| 13 | [Somatic mutation spectra across grape cultivars, with rates where clone dates are known](projects/13-somatic-mutation-spectra-across-cultivars/) | 2 | 2 | 2 | 6 | Medium | 05 | Clone data for several cultivars are public; single-cultivar studies exist, including a 23-clone Pinot noir study, so N = 2; a cross-cultivar spectrum with one pipeline and a time-calibrated somatic rate were not found. |
| 14 | [TE insertion polymorphisms in cultivated grape from graph genotyping](projects/14-te-insertion-polymorphisms-cultivated/) | 2 | 2 | 2 | 6 | Medium | 14 | Narrowed: wild *V. amurensis* already has a population TE study; cultivated *V. vinifera* on a graph does not. |
| 15 | [Introgression on a graph pangenome: wild-to-cultivated and hybrid cultivars](projects/15-graph-introgression/) | 2 | 2 | 2 | 6 | Medium | 15 | Introgression is well studied on linear references; the SV level and multi-species painting of hybrids on T2T or graph references were not found. |
| 16 | [Inherited and clonal structural variants on a graph: where hemizygous SVs sit and why](projects/16-graph-sv-load/) | 2 | 2 | 2 | 6 | Medium | 16 | Load on linear references has already been studied; the contribution is a method improvement (less reference bias, one genotyping pipeline) and a test that separates inherited from clonal SVs. |
| 17 | [Large inversions: discovery in assemblies, population genotyping and suppressed recombination](projects/17-large-inversions-in-populations/) | 2 | 2 | 2 | 6 | Medium | 17 | Inversions appear in SV studies and single T2T assemblies; a population-scale inversion atlas was not found. F = 2 because breakpoint validation requires long reads, which exist for only part of the panel [待确认: long-read coverage per accession]. |
| 18 | [Centromeres of Vitis and Muscadinia, and a check of the chr7 fusion point](projects/18-vitis-muscadinia-centromeres/) | 2 | 2 | 2 | 6 | Medium | 18 | A cross-genus comparison was not found; CENH3 data exist only for Chardonnay and no *Muscadinia* assembly is gap-free, so feasibility is partial. |
| 19 | [Public RNA-seq on PN_T2T: expression atlas, eQTL/sQTL and allele-specific expression](projects/19-public-rnaseq-on-t2t/) | 2 | 2 | 2 | 6 | Medium | 19 | The atlas is quick; sQTL was not found for grape; pan-eQTL is limited by genotype–expression pairing, so the work splits into three papers of different risk. |
| 20 | [Archaeological grape seeds: graph mapping and low-coverage imputation](projects/20-ancient-seeds-on-graph/) | 2 | 2 | 2 | 6 | Medium | 20 | Several ancient datasets are public; graph-based mapping and imputation for grape seeds were not found. |
| 21 | [Meta-analysis of public GWAS, cross-ancestry genomic prediction and SV markers](projects/21-gwas-meta-and-cross-ancestry-prediction/) | 1 | 2 | 2 | 5 | Medium | 21 | The gaps hold in the literature checks, but whether phenotypes and summary statistics are public is unknown, so an inventory comes first. |
| 22 | [Population-level evolution of the sex-determining region (demoted)](projects/22-sex-region-population-level/) | 1 | 1 | 2 | 4 | Medium | 22 | Demoted: the cross-genus comparison is done; what remains needs reliable sex records in wild panels, or new experiments. |

The order follows the total score rather than the tier. Two Quick projects lead; the third Quick project (09) ranks after the Medium projects with the same total because its novelty is low. The one direction confirmed as not done in grape at all (project 10, ARGs for hundreds of samples) has E = 1 because calibration under clonal propagation may fail; it carries a methods-paper fallback.

## Independent re-scoring

A second scorer scored all 22 projects on the same three axes before seeing the scores on this page, reading only each project's gap, data, and analysis steps (excluding the effort estimates). Agreement with the frozen scores of 2026-11-14:

| Axis | Exact agreement | Quadratic-weighted κ |
|---|---|---|
| F | 16/22 | 0.595 |
| N | 17/22 | 0.455 |
| E | 18/22 | 0.750 |

No project differed by 2 points on any axis. Most scores are 2, so κ is sensitive to a few projects and is given for reference only.

One difference was adopted: project 13 (somatic mutation spectra) had N lowered from 3 to 2, because a published study of 23 Pinot noir clones ([Callipo et al. 2026](https://doi.org/10.1186/s13059-026-04184-x)) already covers part of the gap. The other differences keep the scores above: some arise from a different novelty definition (the second scorer also counted precedents in other species, which this page does not), and the effort differences arise from the second scorer not reading the effort estimates. Open points raised by the second scorer are marked [待确认] on the project pages.

## Adjustment register

| Date | Project | Axis | Old | New | Reason | Results seen? |
|---|---|---|---|---|---|---|
| 2026-11-14 | [03](projects/03-endogenous-florendoviruses/) | E | 3 | 2 | Effort estimate is 1–2 months (statistics review ①-1) | no results exist |
| 2026-11-14 | [04](projects/04-virus-discovery-in-public-data/) | E | 3 | 2 | Effort estimate is 1–2 months and the download is all public grape RNA-seq, not small (statistics review ①-1, methods review ②-15) | no results exist |
| 2026-11-14 | [13](projects/13-somatic-mutation-spectra-across-cultivars/) | N | 3 | 2 | Independent re-scoring: a published 23-clone Pinot noir study (Callipo et al. 2026, doi:10.1186/s13059-026-04184-x, checked in Crossref) already covers part of the gap; the narrower cross-cultivar gap remains | no results exist |
