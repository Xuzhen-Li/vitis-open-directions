# vitis-open-directions

只用公开数据就能做的葡萄（*Vitis*）基因组学研究方向。每个方向都写成从下载数据到计划图表的可执行方案。[English](README.md)

这个仓库是三个目录仓库的分析导航页：目录仓库列工具和方法，这里写用哪些公开数据、跑哪些步骤、每个项目回答什么问题。工具的介绍在目录仓库里，这里只放链接。

| 仓库 | 内容 |
|---|---|
| [vitis-pangenome](https://github.com/Xuzhen-Li/vitis-pangenome) | 葡萄泛基因组方法：组装、图基因组、结构变异、群体基因组 |
| [gene-structure-annotation](https://github.com/Xuzhen-Li/gene-structure-annotation) | 基因结构注释工具和流程 |
| [gene-function-annotation](https://github.com/Xuzhen-Li/gene-function-annotation) | 基因功能注释工具和流程 |
| vitis-open-directions（本仓库） | 公开数据、共用分析步骤、排好序的项目 |

状态：草稿 v0.3.2（2026-11-14）。打分于 2026-11-14 冻结，后续调整均登记在排序页；新颖性核查和工作量估计仍为草稿。各页面和状态表最近更新于 2026-11-21。

## 怎么找

- **按项目**：[`projects/`](projects/) 每个项目一个文件夹，写缺口、已有工作、问题、假设和判据、数据、步骤、文章拆分、风险，以及在 SLURM 集群上怎么跑。
- **按数据**：[`data/`](data/) 每个公开数据集一个文件夹，写在哪、多大、许可、下载、预处理和质控。
- **按分析步骤**：[`analyses/`](analyses/) 每个可复用步骤一个文件夹，写最新版本的工具、命令、输出和大致资源。
- **按文章**：[`docs/INDEX.md`](docs/INDEX.md) 列出每个项目用哪些模块、拆成哪几篇文章。
- [`docs/RANKING.md`](docs/RANKING.md)：打分和排序理由。
- [`docs/NOT_KEPT.md`](docs/NOT_KEPT.md)：核查后没有收入的方向，以及已经做过它们的论文。
- [`docs/PREREGISTRATION.md`](docs/PREREGISTRATION.md)：开跑前要填的预注册模板。
- [`docs/DATA_PREP.md`](docs/DATA_PREP.md)、[`docs/HPC_JOBS.md`](docs/HPC_JOBS.md)：共用约定和作业模板。
- [`CHECK.md`](CHECK.md)：链接、DOI、登录号和两套视角一致性的核查。

## 项目

按公开数据可行性、新颖性、工作量三项分数之和排序（见 docs/RANKING.md）。规模按工作量估计的上限归档：快 = 不超过 6 周；中 = 超过 6 周、不超过 4 个月；大 = 超过 4 个月或包含高风险步骤。「续做」表示此前已启动、此处改为基于公开数据并按新预注册重新开始。

| # | 项目 | 规模 | 文章数 | 来源 |
|---|---|---|---|---|
| 01 | [近完整葡萄单倍型的端粒与间质端粒重复](projects/01-telomere-and-interstitial-telomeric-repeats/) | 快 | 2 | 续做 |
| 02 | [近完整葡萄组装中的 45S/5S rDNA 阵列](projects/02-rdna-arrays/) | 快 | 1 | 续做 |
| 03 | [葡萄泛基因组中的内源 florendovirus](projects/03-endogenous-florendoviruses/) | 中 | 1 | 新 |
| 04 | [在全部公开葡萄测序数据中找病毒](projects/04-virus-discovery-in-public-data/) | 中 | 1 | 新 |
| 05 | [统一流程下的葡萄基因有/无：哪些是真的](projects/05-gene-pav-across-pangenomes/) | 中 | 2 | 续做 |
| 06 | [带塌缩核查和整合结构域的葡萄属泛 NLR 组](projects/06-vitis-pan-nlrome/) | 中 | 1 | 续做 |
| 07 | [芪合酶与香气基因家族（STS、TPS、CCD、LOX）的拷贝数与生灭](projects/07-metabolic-gene-families/) | 中 | 2 | 续做 |
| 08 | [公开重测序群体的统一样本身份表](projects/08-harmonised-sample-panel/) | 中 | 1 | 续做 |
| 09 | [果皮颜色位点的图基因组分型](projects/09-berry-colour-locus-graph/) | 快 | 1 | 新 |
| 10 | [数百样本级祖先重组图（ARG）与驯化定年](projects/10-arg-domestication-timing/) | 大 | 2 | 续做 |
| 11 | [葡萄序列到表达模型与植物基础模型的跨物种迁移评估](projects/11-sequence-to-function-models/) | 大 | 1 | 新 |
| 12 | [葡萄与其他作物统一流程的趋同驯化比较](projects/12-convergent-domestication-cross-crop/) | 大 | 1 | 新 |
| 13 | [跨品种体细胞突变谱（有日期时估速率）](projects/13-somatic-mutation-spectra-across-cultivars/) | 中 | 2 | 续做 |
| 14 | [栽培葡萄的图泛基因组 TE 插入多态（含 solo-LTR）](projects/14-te-insertion-polymorphisms-cultivated/) | 中 | 2 | 续做 |
| 15 | [图泛基因组上的野生到栽培渗入与杂交品种单倍型着色](projects/15-graph-introgression/) | 中 | 2 | 新 |
| 16 | [图上分型的结构变异：有性起源继承的与克隆期新增的半合子 SV 分布与负担](projects/16-graph-sv-load/) | 中 | 1 | 续做 |
| 17 | [大倒位：组装发现、群体分型与重组抑制](projects/17-large-inversions-in-populations/) | 中 | 1 | 续做 |
| 18 | [Vitis 与 Muscadinia 着丝粒比较及 chr7 融合点核查](projects/18-vitis-muscadinia-centromeres/) | 中 | 2 | 续做 |
| 19 | [公开 RNA-seq 在 T2T 上重算：表达图谱、eQTL/sQTL 与等位特异表达](projects/19-public-rnaseq-on-t2t/) | 中 | 3 | 新 |
| 20 | [古葡萄种子：图参照比对与低覆盖填补](projects/20-ancient-seeds-on-graph/) | 中 | 1 | 新 |
| 21 | [公开 GWAS 荟萃、跨祖先基因组预测与 SV 标记](projects/21-gwas-meta-and-cross-ancestry-prediction/) | 中 | 3 | 新 |
| 22 | [性别决定区的群体层面演化（降级）](projects/22-sex-region-population-level/) | 中 | 1 | 新 |
| 23 | [公开葡萄记录上的亲子与亲缘关系质控](projects/23-family-parentage/STATUS.md) | [待确认] | [待确认] | 续做 |
| 24 | [葡萄的系谱与连锁不平衡重组图谱](projects/24-recombination-maps/STATUS.md) | [待确认] | [待确认] | 续做 |
| 25 | [转座子注释方法、文库整理与自动化](projects/25-te-annotation-methods/STATUS.md) | [待确认] | [待确认] | 续做 |
| 26 | [葡萄线粒体基因组、核内线粒体插入与异质](projects/26-mitochondrial-genomes/STATUS.md) | [待确认] | [待确认] | 新 |

## 范围

仅使用公开数据：INSDC（NCBI、ENA、DDBJ）、NGDC、GEO、Zenodo、figshare 等。不含任何未发表的数据或结果；计划图表仅列出假设和判据。细胞器基因组、TE 库构建和群体重组图谱在项目 23 至 26 中有方法层面的页面（见 docs/METHOD_LINES.md）；10 号项目仅使用已发表的连锁图，或仅将基于 LD 估计的重组率作为输入。

标 [待确认] 的内容还没有核实。项目文件夹目前是英文。

## 许可

文字和表格：[CC BY 4.0](LICENSE)。数据集按各数据模块写明的许可使用。

**第一次来？** 各项目现状、建议的重启顺序和工作规则见 [START_HERE.zh.md](START_HERE.zh.md)。[English](START_HERE.md)

状态补记，2026-11-21（UTC+8）：新增项目 23 至 26（只写到方法层面），已列入上表。它们涉及亲子检验、重组图谱、TE 注释方法和线粒体基因组，即上面范围一节说的在别处处理的内容；见 [docs/METHOD_LINES.md](docs/METHOD_LINES.md)（英文）。待定事项的默认选项见 [docs/DEFAULTS.md](docs/DEFAULTS.md)（英文）。各项目现状见 [START_HERE.zh.md](START_HERE.zh.md)，截至 2026-11-21。排序页的分数没有变，也没有给项目 23 至 26 打分。
