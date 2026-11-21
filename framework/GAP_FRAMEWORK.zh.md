# 缺口框架：单物种的六个维度

写于 2026-11-21（UTC+8）。[English](GAP_FRAMEWORK.md)

本页说明怎样只用公开数据，在一个物种里发现、检验和排序尚未做过的研究方向。写法不绑定物种，可以用于任何物种。[examples/vitis/](../examples/vitis/) 里的葡萄页面是完整范例，下面每个维度都列出对应的葡萄项目。打分规则见 [EVALUATION_RUBRIC.zh.md](EVALUATION_RUBRIC.zh.md)，迁移到新物种的步骤见 [SPECIES_TRANSFER_GUIDE.zh.md](SPECIES_TRANSFER_GUIDE.zh.md)。

## 每个候选缺口都要过的四道核查

四道都通过之前，不开始任何分析：

1. **文献。** 只用已经打开过 DOI 记录（Crossref 或 DataCite）或原文的论文来判断缺口。本仓库没提到某篇论文，不能当作这项工作没人做过的证据。没有打开过的 DOI 或说法标 [待确认]。
2. **公开数据。** 通过数据库 API（ENA filereport、NCBI Datasets、Zenodo API）实测输入，而不是只看论文怎么说。每个输入标一个状态：`available`（API 能直接列出文件）、`portal`（只能网页检索，没有闭合的文件列表）、`blocked`（有访问校验或返回空列表）、`not found`。必须存在一个不需要私有权限就能跑通的第一个闭合子集。
3. **预注册。** 在看任何主结果之前，把假设、对照、通过线和统计检验写进 [templates/PREREGISTRATION.md](../templates/PREREGISTRATION.md)。
4. **止损规则。** 事先写明在什么条件下停止，或退回到一篇更小的论文。

每个候选方向用 [templates/GAP_AUDIT_TEMPLATE.md](../templates/GAP_AUDIT_TEMPLATE.md) 记录。

## 为什么是这六个维度

数据与资源是底座，其余五个是生物学维度：基因组结构与细胞器；多尺度变异与可移动元件；群体演化、驯化与繁殖系统；表达、调控与表观遗传；表型、功能与跨物种比较。在葡萄这样的植物基因组里，重复序列阵列（端粒、rDNA、着丝粒）、细胞器基因组和转座子（TE）各自构成独立的组装与方法学瓶颈；繁殖系统（克隆繁殖、雌雄异株到两性花的转变）直接决定群体统计量和定年校准能不能成立。这套划分可以直接用到任何有参考基因组、重测序群体和公开转录组的动植物物种。

每个维度都问同样四个问题：查什么；缺口是不是真的；值不值得做；公开数据够不够。

## 1. 数据与资源（底座）

- **查什么。** 盘点该物种在 INSDC（NCBI、ENA、DDBJ）、NGDC、GEO、Zenodo、figshare 和物种专属门户里的组装、重测序、长读长、RNA-seq、表观组和表型数据；核查跨研究的样本重复、克隆冗余、坐标系碎片化和元数据缺失。
- **缺口是不是真的。** 不只看文献声称「已有面板」，而是通过 API 实测登录号能否解析、文件列表能否读取、是否有访问拦截或断链；核查各面板之间是否已有统一的样本身份表和去重基线。
- **值不值得做。** 如果多个群体、图基因组或 QTL 项目都依赖同一个样本池或参考坐标，基础设施类缺口杠杆很高；如果只服务一个边缘问题，优先级低。
- **公开数据够不够。** 用上面四个状态词给每个输入分类，并要求有一个不需要私有权限就能跑通的第一个闭合子集。
- **葡萄范例：** [data/DOWNLOADS.md](../examples/vitis/data/DOWNLOADS.md)、[data/README.md](../examples/vitis/data/README.md)、[DEFAULTS.md](../examples/vitis/DEFAULTS.md)、项目 [08](../examples/vitis/projects/08-harmonised-sample-panel/)。

## 2. 基因组结构与细胞器

- **查什么。** 按区域逐层扫描：端粒与间质端粒重复（ITS）、45S 与 5S rDNA、着丝粒卫星与染色体融合点、单倍型之间的共线性与基因家族拷贝数，以及线粒体、叶绿体基因组、核内细胞器 DNA 插入（NUMT、NUPT）与异质性。
- **缺口是不是真的。** 核查单基因组 T2T 论文和泛基因组论文是否只做了单参考描述，缺少跨单倍型或跨属的统一比较；同时核查是否存在「技术假象被当成生物学结论」的缺口，比如注释漏检造成的假基因有无变异、组装塌缩造成的假抗病基因拷贝数变异。
- **值不值得做。** 优先选能区分真实演化与组装、注释假象的问题，或者能为全物种核基因组分析提供掩蔽区（NUMT 掩蔽、着丝粒坐标）的问题。
- **公开数据够不够。** 检查近完整单倍型的数量是否有足够统计功效。例如 9 个基因组里有 2 个外群时，精确置换检验最小 p 值为 1/36，太粗。检查验证数据（同一 BioSample 的长读长、CENH3 ChIP-seq）是否覆盖目标类群。
- **葡萄范例：** 项目 [01](../examples/vitis/projects/01-telomere-and-interstitial-telomeric-repeats/)、[02](../examples/vitis/projects/02-rdna-arrays/)、[05](../examples/vitis/projects/05-gene-pav-across-pangenomes/)、[06](../examples/vitis/projects/06-vitis-pan-nlrome/)、[07](../examples/vitis/projects/07-metabolic-gene-families/)、[18](../examples/vitis/projects/18-vitis-muscadinia-centromeres/)、[26](../examples/vitis/projects/26-mitochondrial-genomes/STATUS.md)。

## 3. 多尺度变异与可移动元件

- **查什么。** SNP 和 Indel 之外的变异：图泛基因组上的结构变异（SV）、大倒位、转座子插入多态与 solo-LTR、内源病毒元件，以及无性系或体细胞突变谱。
- **缺口是不是真的。** 核查已有研究是否局限于线性参考（存在参考偏倚），或只做了一个野生或栽培类群。
- **值不值得做。** 看方法升级（线性参考到图参考、单样本到群体分型）能不能改变生物学结论，例如区分有性遗传的半合子 SV 和克隆繁殖期间新出现的半合子 SV；只换工具不够。
- **公开数据够不够。** 检查有没有用于断点验证的长读长、用于极化的合适外群、能区分遗传与新发变异的家系三联体，以及关键工具能否在集群上安装。
- **葡萄范例：** 项目 [03](../examples/vitis/projects/03-endogenous-florendoviruses/)、[13](../examples/vitis/projects/13-somatic-mutation-spectra-across-cultivars/)、[14](../examples/vitis/projects/14-te-insertion-polymorphisms-cultivated/)、[16](../examples/vitis/projects/16-graph-sv-load/)、[17](../examples/vitis/projects/17-large-inversions-in-populations/)、[25](../examples/vitis/projects/25-te-annotation-methods/STATUS.md)。

## 4. 群体演化、驯化与繁殖系统

- **查什么。** 亲子与系谱质控、系谱与连锁不平衡（LD）重组图谱、祖先重组图（ARG）与等位基因定年、图上渐渗与杂交品种着色、性别决定区演化，以及古 DNA 的图比对与填补。
- **缺口是不是真的。** 严格区分「在线性参考上已做过」与「在图参考或 SV 层面没做过」；严格区分不同统计量，系谱重组率不等于基于 LD 的历史重组率。
- **值不值得做。** 如果存在根本性的方法学障碍（例如克隆繁殖导致 ARG 定年校准失败），事先设好方法学论文兜底；如果已发表工作已覆盖核心问题，剩下的缺口又依赖稀缺的表型或性别记录，应当降级。
- **公开数据够不够。** 检查有没有去克隆的去重样本池、可核实的公开家系或三联体、逐个核实过原始读段的古 DNA 登录号，以及完整的供体面板。
- **葡萄范例：** 项目 [08](../examples/vitis/projects/08-harmonised-sample-panel/)、[10](../examples/vitis/projects/10-arg-domestication-timing/)、[15](../examples/vitis/projects/15-graph-introgression/)、[20](../examples/vitis/projects/20-ancient-seeds-on-graph/)、[22](../examples/vitis/projects/22-sex-region-population-level/)、[23](../examples/vitis/projects/23-family-parentage/STATUS.md)、[24](../examples/vitis/projects/24-recombination-maps/STATUS.md)。

## 5. 表达、调控与表观遗传

- **查什么。** 公开 RNA-seq 在最新参考上的统一重算（表达图谱、可变剪接、eQTL 与 sQTL、等位特异表达），小 RNA 与 phasiRNA、DNA 甲基化、三维基因组（Hi-C、TAD），以及序列到表达模型。
- **缺口是不是真的。** 核查现有表达平台和单研究 eQTL 是否基于旧参考、是否缺 sQTL；核查表观遗传与三维基因组方向是否已被近期论文覆盖。
- **值不值得做。** 优先做能为模型和遗传定位提供统一基座的资源型工作（例如 T2T 表达图谱喂给序列到表达模型），并按风险拆成独立产出（图谱与 QTL 分开）。
- **公开数据够不够。** 检查基因型、组织和研究之间的混杂是否严重到无法做 QTL 定位；公开甲基化组或单细胞数据的样本量能否支撑群体分析（不够就列入未收入方向）；GPU 算力和防信息泄露的数据划分（按染色体、按基因家族）是否具备。
- **葡萄范例：** 项目 [11](../examples/vitis/projects/11-sequence-to-function-models/)、[19](../examples/vitis/projects/19-public-rnaseq-on-t2t/)；未收入的方向见 [NOT_KEPT.md](../examples/vitis/NOT_KEPT.md)。

## 6. 表型、功能与跨物种比较

- **查什么。** 单个关键农艺位点的图分型、公开 GWAS 荟萃分析与跨祖先基因组预测、SV 标记面板、跨作物趋同驯化，以及在公开测序的未比对读段里发现病原和病毒。
- **缺口是不是真的。** 核查经典位点是否已被大量研究（那样新颖性低）；核查功能类缺口是否其实需要湿实验。
- **值不值得做。** 表型依赖外部数据库的方向，把「公开表型与汇总统计量清点」设为硬止损门槛；跨物种比较要先确认零模型和同源群定义是否严密。
- **公开数据够不够。** 检查表型和 GWAS 汇总统计量是否以机器可读格式公开（而不只嵌在 PDF 里）；检查跨作物比较里每个面板的原始 FASTQ 是否都在 ENA、能否下采样到相近规模。
- **葡萄范例：** 项目 [04](../examples/vitis/projects/04-virus-discovery-in-public-data/)、[09](../examples/vitis/projects/09-berry-colour-locus-graph/)、[12](../examples/vitis/projects/12-convergent-domestication-cross-crop/)、[21](../examples/vitis/projects/21-gwas-meta-and-cross-ancestry-prediction/)。

## 现有葡萄项目之外可能的缺口 [待确认]

2026-11-21 提出了两个候选，尚未做文献检索。每个都要先按 [缺口审计模板](../templates/GAP_AUDIT_TEMPLATE.md) 完成 Crossref 检索，再决定是否加入：

- 叶绿体泛基因组与核质互作，并与线粒体基因组联合分析 [待确认]。
- 跨单倍型的蛋白质结构演化：用结构预测找蛋白结构变异或新功能化 [待确认]。

## 框架改动之后

每次改动 `framework/` 或 `templates/` 之后，重跑 [examples/vitis/CHECK.md](../examples/vitis/CHECK.md) 里说明的相对链接检查和公开文本筛查。
