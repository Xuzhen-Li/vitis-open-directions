# DS13 · Clone resequencing across cultivars (Zinfandel, Chardonnay, Pinot noir, Malbec, Merlot and others)

Short and long reads from several clones of the same cultivar, for somatic-variant work. Each cultivar comes from a different study, so cultivar and study cannot be separated except inside the four-cultivar panel; a single pipeline is needed before any comparison.

## Sources

| Part | Where |
|---|---|
| Zinfandel / Primitivo / Tribidrag clones | [PRJNA527006](https://www.ebi.ac.uk/ena/browser/view/PRJNA527006) (66 runs, 379.7 GB; includes a Cabernet Franc sample) |
| Chardonnay clones | [PRJNA399599](https://www.ebi.ac.uk/ena/browser/view/PRJNA399599) (95 runs, 1,829.8 GB, WGS; Chardonnay clones and Gouais blanc) |
| Pinot noir clones (2026) | [PRJEB106155](https://www.ebi.ac.uk/ena/browser/view/PRJEB106155) (25 runs, 277.8 GB, WGS) |
| Pinot clones (earlier) | [PRJNA321480](https://www.ebi.ac.uk/ena/browser/view/PRJNA321480) (12 runs, 109.3 GB, WGS) [待确认: linked paper] |
| Malbec clones | [PRJNA663442](https://www.ebi.ac.uk/ena/browser/view/PRJNA663442) (4 runs, 68.9 GB, WGS) |
| Merlot root and leaf | [PRJEB59893](https://www.ebi.ac.uk/ena/browser/view/PRJEB59893) (4 runs, WGS) |
| Clone identification panel | [PRJNA847341](https://www.ebi.ac.uk/ena/browser/view/PRJNA847341) (45 runs, 342.5 GB; four cultivars) |
| Tribidrag clones (2026) | eight clones; accession as given in the paper [待确认] |
| Chardonnay long reads (SV reference) | [PRJNA550461](https://www.ebi.ac.uk/ena/browser/view/PRJNA550461) (41 PacBio runs, 20.4 GB); assembly [zenodo.org/records/3337377](https://zenodo.org/records/3337377) (no Zenodo DOI is registered for this record) (0.64 GB, CC BY 4.0) |
| Cabernet Sauvignon reference reads | [PRJNA316730](https://www.ebi.ac.uk/ena/browser/view/PRJNA316730) (76 runs, 136.1 GB; one FPS 08 plant used for the reference assembly, not a clone panel) |

Sizes are sums of `fastq_bytes` from the ENA portal API or file sizes from the Zenodo API, read on 2026-11-14 (UTC+8). They are download sizes, not disk needs after processing.

## Licence and reuse

INSDC no restrictions; Zenodo CC BY 4.0.

## Download (sketch)

```bash
per BioProject filereport as DS10
```

## Preparation

Group runs by cultivar and clone from `sample_title`. Record for each clone the sampled tissue and any documented selection or registration date and nursery history [待确认 per study]; a documented date is a lower bound on the divergence time of two clones, not the date of their common ancestor. Record which clone any public assembly of the cultivar was built from and whether that clone's reads are public [待确认 per study], so the assembled clone can be re-called as one tip of the clone tree. Keep the original study's sample names next to new IDs. The four-cultivar panel (PRJNA847341) is the only within-study multi-cultivar set and is used for within-study comparisons.

## QC

AM02; depth per clone with mosdepth; AM04 to confirm that clones of one cultivar are genetically identical apart from somatic changes and that no sample is mislabelled.

Shared conventions (layout, manifests, naming, coordinates) are in [`docs/DATA_PREP.md`](../../../../templates/DATA_PREP.md).

## Cite

- Vondras et al. 2019. The genomic diversification of grapevine clones. *BMC Genomics*. [doi:10.1186/s12864-019-6211-2](https://doi.org/10.1186/s12864-019-6211-2)
- Roach et al. 2018. Population sequencing reveals clonal diversity and ancestral inbreeding in the grapevine cultivar Chardonnay. *PLOS Genetics*. [doi:10.1371/journal.pgen.1007807](https://doi.org/10.1371/journal.pgen.1007807)
- Callipo et al. 2026. A dual genome-methylome map of clonal evolution in grapevine. *Genome Biology*. [doi:10.1186/s13059-026-04184-x](https://doi.org/10.1186/s13059-026-04184-x)
- Calderón et al. 2021. Whole genome resequencing and custom genotyping unveil clonal lineages in ‘Malbec’ grapevines (Vitis vinifera L.). *Scientific Reports*. [doi:10.1038/s41598-021-87445-y](https://doi.org/10.1038/s41598-021-87445-y)
- Sichel et al. 2023. Chimeras in Merlot grapevine revealed by phased assembly. *BMC Genomics*. [doi:10.1186/s12864-023-09453-8](https://doi.org/10.1186/s12864-023-09453-8)
- Urra et al. 2023. Identification of grapevine clones via high-throughput amplicon sequencing: a proof-of-concept study. *G3: Genes, Genomes, Genetics*. [doi:10.1093/g3journal/jkad145](https://doi.org/10.1093/g3journal/jkad145)
- Zdunić et al. 2026. Whole-genome sequencing of eight grapevine clones of cv. Tribidrag (Vitis vinifera L.) reveals measurable differentiation not linked directly to phenotypic divergence. *BMC Plant Biology*. [doi:10.1186/s12870-026-10110-x](https://doi.org/10.1186/s12870-026-10110-x)
- Zhou et al. 2019. The population genetics of structural variants in grapevine domestication. *Nature Plants*. [doi:10.1038/s41477-019-0507-8](https://doi.org/10.1038/s41477-019-0507-8)

## Used by projects

- [13. Somatic mutation spectra across grape cultivars, with rates where clone dates are known](../../projects/13-somatic-mutation-spectra-across-cultivars/)
- [16. Inherited and clonal structural variants on a graph: where hemizygous SVs sit and why](../../projects/16-graph-sv-load/)
