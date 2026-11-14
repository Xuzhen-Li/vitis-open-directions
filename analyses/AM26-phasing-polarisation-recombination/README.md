# AM26 · Phasing, ancestral states and recombination rates

## Tools

| Tool | Version | Role |
|---|---|---|
| SHAPEIT5 | 5.1.1 | phasing |
| minimap2 | 2.31 | outgroup alignment to PN_T2T; paftools.js call gives per-site outgroup bases |
| est-sfs | 2.04 | probabilistic ancestral states |
| pyrho | 0.2.1 (Bioconda) | LD-based rates, used only as ARG input |
| LDhelmet | 1.10 | alternative to pyrho |

Each tool is listed once, at its latest release on 2026-11-14 (UTC+8): Bioconda or conda-forge unless the version says GitHub, PyPI or CRAN. Pin versions in one environment file per project. The Role column says which tool is the default, which is an alternative to it, and which is a later step. Older tools are listed in the catalogues linked below, not here.

## Steps

Phase the deduplicated joint SNP VCF from AM03/AM04 with SHAPEIT5 (common variants first, then rare), using the published linkage map interpolated to PN_T2T; where no adequate published map exists, phase without a map. A pyrho map is never used for phasing. Ancestral states: align two or more outgroups to PN_T2T using the settings stated here (which differ from AM06, which targets SV calling): *Muscadinia rotundifolia* (DS08) plus a North American or East Asian *Vitis* haplotype (DS04 or DS06), with minimap2 asm20 for *Vitis* and asm20 or AnchorWave for the more diverged *Muscadinia* [待确认: which gives better one-to-one coverage]. Keep one-to-one alignment blocks only, mask multi-mapping and low-mapping-quality blocks, and convert the alignments to per-site outgroup bases (paftools.js call on the cs-tagged PAF); sites without one-to-one coverage are treated as missing. Choose *Vitis* outgroup haplotypes with no reported introgression with *V. vinifera*, order outgroups from nearest to most distant in the est-sfs configuration, and report missing and discordant site fractions per outgroup; estimate the probability that each allele is ancestral with est-sfs and report the polarisation error estimated separately for each outgroup, from nearest to most distant, because incomplete lineage sorting between North American or East Asian *Vitis* and *V. vinifera* leaves shared ancestral polymorphisms that can mislead even a close outgroup. A single *Muscadinia* outgroup is deeply diverged and its errors would inflate allele ages, so it is never used alone. Recombination: by default, interpolate published grape linkage maps onto PN_T2T [待确认: which map has enough markers]; where none is adequate, estimate LD-based rates with pyrho (or LDhelmet) on deduplicated samples, used only as an input to ARG inference and not released as a map. Run pyrho per population, taking the population-size history from the project's simulation scenarios or a published model with its source, and recording the sample size per population in the preregistration; Clonal propagation itself does not change LD between genotypes: cultivars arose from sexual crosses, cuttings involve no meiosis, and with few sexual generations since domestication, most LD in cultivated grape is inherited from the wild ancestor. It affects LD-based estimates in two ways only: repeated samples of one genotype, removed by AM04, and the dense parent–offspring and sibling relationships among cultivars, which elevate LD. Beyond deduplication, one sample from each first-degree pair is removed (default: KING kinship above 0.177), or a kinship sensitivity run is reported. Under inbreeding, the effective recombination rate is about r(1 − F) ([Nordborg 2000](https://doi.org/10.1093/genetics/154.2.923)), so ρ is biased downward: highly homozygous lines such as PN40024 are excluded from the LD sample, and F (or heterozygosity) is reported per population. Populations are defined in advance from ancestry components; mixing cultivated grapes with *V. sylvestris*, different cultivar groups, or introgressed cultivars creates long-range admixture LD that lowers rates and creates false hot or cold spots at introgression edges, so highly admixed individuals are excluded or analysed separately. pyrho rates are compared with the published map where both exist. A constant-rate run is always kept as a sensitivity check.

## Command sketch

```bash
phase_common --input x.bcf --region chr01 --map chr01.gmap.gz --output chr01.common.bcf --thread 8  # drop --map if no published map
minimap2 -x asm20 -c --cs pn_t2t.fa outgroup.fa | sort -k6,6 -k8,8n | paftools.js call -f pn_t2t.fa - | gzip -c > outgroup.var.gz
est-sfs config.txt input.txt seed.txt sfs.txt p_anc.txt
```

## Outputs

phased BCF per chromosome, ancestral-state probabilities with polarisation error, recombination map used

## HPC resources (rough)

8–16 CPU, 32–64 GB per chromosome; est-sfs single-threaded, hours per chromosome

## Catalogue entries

- [vitis-pangenome §11](https://github.com/Xuzhen-Li/vitis-pangenome#section-11)

## Used by projects

- [10. Ancestral recombination graphs for hundreds of grape genomes and domestication timing](../../projects/10-arg-domestication-timing/)
- [16. Inherited and clonal structural variants on a graph: where hemizygous SVs sit and why](../../projects/16-graph-sv-load/)
- [19. Public RNA-seq on PN_T2T: expression atlas, eQTL/sQTL and allele-specific expression](../../projects/19-public-rnaseq-on-t2t/)
