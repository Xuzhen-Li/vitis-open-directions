# DS01 · PN40024 references: PN_T2T (v5), PN40024.v4 and 12X

The coordinate backbone. Most public grape VCFs, gene IDs and QTL positions use 12X or PN40024.v4; new work should use PN_T2T and keep a liftover table.

## Sources

| Part | Where |
|---|---|
| PN_T2T assembly | [GCF_030704535.1](https://www.ncbi.nlm.nih.gov/datasets/genome/GCF_030704535.1/) / GCA_030704535.1, 494,873,210 bp, Complete Genome; reads [PRJNA882193](https://www.ebi.ac.uk/ena/browser/view/PRJNA882193) (1 PacBio run, 28.5 GB FASTQ); also NGDC PRJCA012093 [待确认: NGDC page not checked] |
| PN_T2T annotation (default) | NCBI RefSeq annotation GCF_030704535.1-RS_2023_09 (EGAP 10.2, released 2023-09-14; 25,187 protein-coding genes in the NCBI report), downloaded with the assembly. The PN_T2T annotation distributed through Grapedia is the alternative [待确认: file URL and version]. |
| PN40024.v4 | [PRJEB45423](https://www.ebi.ac.uk/ena/browser/view/PRJEB45423) (264 runs, 92.5 GB FASTQ; Illumina, PacBio, RAD-seq). Annotation releases are distributed through Grapedia [待确认: exact file URL] |
| 12X (historic) | [GCF_000003745.3](https://www.ncbi.nlm.nih.gov/datasets/genome/GCF_000003745.3/), BioProject PRJEA18785 |

Sizes are sums of `fastq_bytes` from the ENA portal API or file sizes from the Zenodo API, read on 2026-11-14 (UTC+8). They are download sizes, not disk needs after processing.

## Licence and reuse

INSDC records (NCBI/ENA/DDBJ) carry no use restrictions under the INSDC policy; cite the papers. Grapedia annotation licence [待确认].

## Download (sketch)

```bash
datasets download genome accession GCF_030704535.1 --include genome,gff3,gtf,rna,protein,cds --filename pn_t2t.zip
unzip pn_t2t.zip -d pn_t2t && md5sum -c pn_t2t/md5sum.txt   # file name inside the zip [待确认]
seqkit stats -a pn_t2t/ncbi_dataset/data/GCF_030704535.1/*.fna
sha256sum pn_t2t/ncbi_dataset/data/GCF_030704535.1/*   # record in MANIFEST.tsv
```

## Preparation

Rename sequences to chr01..chr19 and keep a two-column map from RefSeq names; apply the same map to the GFF, GTF, transcripts.fa, the salmon decoy list, and every VCF so all files share one naming scheme. Fix one annotation for every module: RefSeq GCF_030704535.1-RS_2023_09 by default; record its file sha256 here, and switch only through a logged deviation. From it, build transcripts.fa (gffread), a tx2gene table (from the GFF transcript-to-gene Parent links; all transcript types kept, with non-coding and pseudogene transcripts flagged), a decoy-aware salmon index, the STAR index, the SnpEff database, and a gene ID map to PN40024.v4 and 12X through the liftover chain. Build a v4-to-T2T liftover chain once (minimap2 + transanno or liftOver) and store it here; every project that reuses old coordinates calls this chain.

## QC

19 chromosome-scale sequences; total length matches NCBI; telomere motif TTTAGGG at both ends of each chromosome (module AM10); no duplicated names.

Shared conventions (layout, manifests, naming, coordinates) are in [`docs/DATA_PREP.md`](../../../../templates/DATA_PREP.md).

## Cite

- Shi et al. 2023. The complete reference genome for grapevine ( Vitis vinifera L.) genetics and breeding. *Horticulture Research*. [doi:10.1093/hr/uhad061](https://doi.org/10.1093/hr/uhad061)
- Velt et al. 2023. An improved reference of the grapevine genome reasserts the origin of the PN40024 highly homozygous genotype. *G3: Genes, Genomes, Genetics*. [doi:10.1093/g3journal/jkad067](https://doi.org/10.1093/g3journal/jkad067)
- The French–Italian Public Consortium for Grapevine Genome Characterization 2007. The grapevine genome sequence suggests ancestral hexaploidization in major angiosperm phyla. *Nature*. [doi:10.1038/nature06148](https://doi.org/10.1038/nature06148)

## Used by projects

- [01. Telomeres and interstitial telomeric repeats across near-complete grape haplotypes](../../projects/01-telomere-and-interstitial-telomeric-repeats/)
- [02. 45S and 5S rDNA arrays in near-complete grape assemblies](../../projects/02-rdna-arrays/)
- [03. Endogenous florendovirus insertions across grape haplotypes](../../projects/03-endogenous-florendoviruses/)
- [04. Virus discovery across public grape RNA-seq and unmapped reads](../../projects/04-virus-discovery-in-public-data/)
- [05. Gene presence/absence across grape pangenomes under one pipeline](../../projects/05-gene-pav-across-pangenomes/)
- [06. A genus-wide NLR catalogue with integrated domains and collapse checks](../../projects/06-vitis-pan-nlrome/)
- [07. Copy number and birth–death of stilbene and aroma gene families (STS, TPS, CCD, LOX)](../../projects/07-metabolic-gene-families/)
- [08. A harmonised identity table for public grape resequencing panels](../../projects/08-harmonised-sample-panel/)
- [09. Graph genotyping of the berry colour locus](../../projects/09-berry-colour-locus-graph/)
- [10. Ancestral recombination graphs for hundreds of grape genomes and domestication timing](../../projects/10-arg-domestication-timing/)
- [11. Sequence-to-expression models and plant foundation models evaluated on grape](../../projects/11-sequence-to-function-models/)
- [12. Convergent domestication: grape compared with other crops in one pipeline](../../projects/12-convergent-domestication-cross-crop/)
- [13. Somatic mutation spectra across grape cultivars, with rates where clone dates are known](../../projects/13-somatic-mutation-spectra-across-cultivars/)
- [14. TE insertion polymorphisms in cultivated grape from graph genotyping](../../projects/14-te-insertion-polymorphisms-cultivated/)
- [15. Introgression on a graph pangenome: wild-to-cultivated and hybrid cultivars](../../projects/15-graph-introgression/)
- [16. Inherited and clonal structural variants on a graph: where hemizygous SVs sit and why](../../projects/16-graph-sv-load/)
- [17. Large inversions: discovery in assemblies, population genotyping and suppressed recombination](../../projects/17-large-inversions-in-populations/)
- [18. Centromeres of Vitis and Muscadinia, and a check of the chr7 fusion point](../../projects/18-vitis-muscadinia-centromeres/)
- [19. Public RNA-seq on PN_T2T: expression atlas, eQTL/sQTL and allele-specific expression](../../projects/19-public-rnaseq-on-t2t/)
- [21. Meta-analysis of public GWAS, cross-ancestry genomic prediction and SV markers](../../projects/21-gwas-meta-and-cross-ancestry-prediction/)
- [22. Population-level evolution of the sex-determining region (demoted)](../../projects/22-sex-region-population-level/)
