# 从这里开始

写给接手这个仓库的新维护者或新模型。[English](START_HERE.md)

本仓库收的是只用公开数据的葡萄（*Vitis*）基因组学项目，每个项目都是可以直接执行的方案。其中一部分项目接续了更早的尝试，那些尝试没有走到有确认结果的一步。本页说明每个项目现在做到哪、先做什么、要守哪些规则。这里不含任何结果。

状态截至 2026-11-20（UTC+8）。标 [待确认] 的内容没有核实；英文文件里的 [to confirm] 是同一个意思。

## 阅读顺序

1. [README.md](README.md)：仓库是什么，项目怎么排序。
2. 本页：状态总表、重启顺序、工作规则、教训。
3. [docs/EARLIER_LINES.md](docs/EARLIER_LINES.md)：早先的工作对应哪个项目文件夹（英文）。
4. 你要做的项目：先读 `projects/NN-.../README.md`（方案），再读 `projects/NN-.../STATUS.md`（现状和第一步）。
5. 它用到的模块：[data/](data/)（公开数据集）、[analyses/](analyses/)（工具、命令、资源）。
6. [docs/PREREGISTRATION.md](docs/PREREGISTRATION.md)、[docs/EVIDENCE_LOG_TEMPLATE.md](docs/EVIDENCE_LOG_TEMPLATE.md)、[docs/HPC_JOBS.md](docs/HPC_JOBS.md)、[docs/DATA_PREP.md](docs/DATA_PREP.md)。
7. [docs/RANKING.md](docs/RANKING.md) 和 [docs/NOT_KEPT.md](docs/NOT_KEPT.md)：为什么这样排序，哪些方向没有收。

## 目录结构

| 文件夹 | 内容 |
|---|---|
| [data/](data/) | DS01 到 DS22：每个文件夹一个公开数据集，写登录号、大小、许可、下载和质控 |
| [analyses/](analyses/) | AM01 到 AM26：可复用的分析步骤，写工具、命令、输出和大致资源 |
| [projects/](projects/) | 22 个项目，每个一个文件夹：README（方案）和 STATUS（现状） |
| [docs/](docs/) | 排序、索引、预注册模板、作业模板、证据日志模板、未收入清单 |

## 各项目状态

状态含义：**未开始**＝只有方案。**方案已定**＝早先写好了详细设计，没有确认的结果。**跑过部分**＝早先的版本跑过一部分，不能接着跑，要当作新研究重来。**暂停**＝卡在技术问题上。

| # | 项目 | 状态 | 一句话 |
|---|---|---|---|
| 01 | [端粒与间质端粒重复](projects/01-telomere-and-interstitial-telomeric-repeats/STATUS.md) | 跑过部分 | 早先的扫描因诱饵对照没过，按描述性收尾；要当作新研究重做 |
| 02 | [rDNA 阵列](projects/02-rdna-arrays/STATUS.md) | 跑过部分 | 只做了元数据和合并步骤的一部分；先做描述性的闭合/开放目录 |
| 03 | [florendovirus 插入](projects/03-endogenous-florendoviruses/STATUS.md) | 未开始 | 方案完整；先在两个组装上试跑 |
| 04 | [公开 RNA-seq 里的病毒](projects/04-virus-discovery-in-public-data/STATUS.md) | 未开始 | 方案完整；先定好防 index hopping 的对照 |
| 05 | [基因有无变异审计](projects/05-gene-pav-across-pangenomes/STATUS.md) | 方案已定 | 完整设计已写好，工具只装了一半，没有结果；重来时只留一份预注册 |
| 06 | [NLR 目录](projects/06-vitis-pan-nlrome/STATUS.md) | 方案已定 | 设计已写好；先数技术重复对有几对 |
| 07 | [STS、TPS、CCD、LOX 家族](projects/07-metabolic-gene-families/STATUS.md) | 跑过部分 | 早先 STS 检验的功效太低，香气稿暂停；在公开单倍型上重来 |
| 08 | [统一的样本身份表](projects/08-harmonised-sample-panel/STATUS.md) | 跑过部分 | 身份流程设计好了，正式运行没跑完；在公开面板上重建 |
| 09 | [浆果颜色位点图基因组](projects/09-berry-colour-locus-graph/STATUS.md) | 未开始 | 快速项目；先定位位点、建局部图 |
| 10 | [ARG 与驯化定年](projects/10-arg-domestication-timing/STATUS.md) | 跑过部分 | 校准不支持直接定年；先写校准方案，方法学论文作兜底 |
| 11 | [序列到表达模型](projects/11-sequence-to-function-models/STATUS.md) | 未开始 | 要等项目 19 的表达表，并需要 GPU |
| 12 | [跨作物趋同驯化](projects/12-convergent-domestication-cross-crop/STATUS.md) | 未开始 | 先选作物、先定零模型 |
| 13 | [体细胞突变谱](projects/13-somatic-mutation-spectra-across-cultivars/STATUS.md) | 未开始 | 先做克隆清单和掩蔽区；2 号染色体 LOH 的想法先放着 |
| 14 | [TE 插入多态](projects/14-te-insertion-polymorphisms-cultivated/STATUS.md) | 方案已定 | 设计和对照已写好，没有产出；注释工具环境失败；要和 vitis-te 目录分工 |
| 15 | [图基因组上的渐渗](projects/15-graph-introgression/STATUS.md) | 未开始 | 先定供体面板 |
| 16 | [图上的遗传和克隆结构变异](projects/16-graph-sv-load/STATUS.md) | 未开始 | 图基因分型加三联体；ROH 与负荷那条线并入 AM12 |
| 17 | [大倒位](projects/17-large-inversions-in-populations/STATUS.md) | 跑过部分 | 跨越读段检验设计好了，代码没通过检查；要用项目 08 的样本池 |
| 18 | [着丝粒](projects/18-vitis-muscadinia-centromeres/STATUS.md) | 暂停 | TRASH 没装成，ChIP 下载没完成 |
| 19 | [T2T 上的公开 RNA-seq](projects/19-public-rnaseq-on-t2t/STATUS.md) | 未开始 | 先做表达图谱，QTL 放后面 |
| 20 | [古代种子上图](projects/20-ancient-seeds-on-graph/STATUS.md) | 未开始 | 先逐个登录号确认有没有原始读段 |
| 21 | [GWAS 元分析](projects/21-gwas-meta-and-cross-ancestry-prediction/STATUS.md) | 未开始 | 只做清点；数据不公开就停 |
| 22 | [性别决定区](projects/22-sex-region-population-level/STATUS.md) | 未开始 | 已降级；先查性别记录 |
| 23 | [亲子与亲缘关系质控（公开记录）](projects/23-family-parentage/STATUS.md) | 方案已定 | 设计已写、未运行；只用公开记录，私有家系不进本仓库；阳性对照是 DS18 的三联体 |
| 24 | [系谱与连锁不平衡重组图谱](projects/24-recombination-maps/STATUS.md) | 方案已定 | 设计已写、未运行；系谱量和 LD 量分开；公开路线用已发表图谱和公开面板 |
| 25 | [TE 注释方法、整理与自动化](projects/25-te-annotation-methods/STATUS.md) | 方案已定 | 方法调查提纲已写；本仓库尚无文稿；与项目 14、vitis-te 的分工在 docs/DEFAULTS.md 有默认 |
| 26 | [线粒体基因组、核内线粒体插入与异质](projects/26-mitochondrial-genomes/STATUS.md) | 未开始 | 已列出拟定的起步设计和公开输入；决定项目走向的问题还没定 |

## 建议的重启顺序

这是按排序和项目之间的依赖给出的建议，不是定论，主人想换就换。

1. **打底**：对 DS01、DS02、DS03、DS16 做 AM01（带校验和下载）和 AM05（组装质控）。项目 01、02、03、05、06、07、14、17、18 都靠它。
2. **只用组装、算力小**：01、02、18 一起做（共用 AM10 和 7 号染色体融合点检查），然后 03。
3. **注释和泛基因组**：05 和 06（一篇文章两节），再做 07 和 14。
4. **样本表**：08。很多群体项目要用它去掉克隆后的样本池。先做元数据和小面板，最大的下载放后面。
5. **要用样本表的项目**：09（快），然后 17、15、16、13。
6. **大项目或高风险**：10（先校准）、19 然后 11、12、20、21（先清点）、22（已降级）。
7. **方法线（2026-11-21 补入）。** 先做 23，再做 24（先用公开记录）。25 可按已发表文献并行起草。26 要先定下决定项目走向的问题。

## 工作规则

- 先写判据，再看结果。填好 [docs/PREREGISTRATION.md](docs/PREREGISTRATION.md)，带日期提交，再运行。每次重启都写新的预注册；早先尝试的判据只作参考。
- 看到结果之后做的任何改动都算事后修改：在日志里写明，结果只能当探索性的。
- 每个项目写证据日志（[docs/EVIDENCE_LOG_TEMPLATE.md](docs/EVIDENCE_LOG_TEMPLATE.md)），只追加，不改旧条目；写错了就加一条新条目指向旧条目。
- 每条引用必须是你自己打开过的 DOI 或网址，DOI 要用 Crossref 或 DataCite 核对；没核对的标 [待确认]。不编文献、登录号和数字。
- 看主要结果之前先跑阳性和阴性对照，通过标准事先定好。
- 写代码的人或程序不检查自己的代码，由另一个来检查。
- 不覆盖、不删除输出。每次运行一个新文件夹，以 .DONE 或 .FAILED 结尾（[docs/HPC_JOBS.md](docs/HPC_JOBS.md)）。每个下载的文件都记 sha256 清单。
- 只用公开数据。不要提交私有数据、样本明细、结果、主机名、本地路径或密钥。
- 用平实的话写。不点名、不贬低其他团队，引用他们的论文时保持中性。
- 更新 STATUS.md 时，在文末加一节带日期的内容，旧文字保留，其余交给 git 历史。

## 早先尝试的教训

- 先定阈值和样本清单。看到结果后再改，会让好几条早先的线变成探索性的。
- 阴性对照没过，就改成描述性报告；这个结局要提前想好。
- 基因组很少的时候，精确置换检验得不到很小的 p 值（9 个基因组只有 36 种分配）。设计时就要算功效。
- 葡萄里克隆和重复样本很多。做任何群体分析之前先跑 AM04。
- 用一个读段数据当证据之前，先核对它的 BioSample 和名称，确认确实属于你以为的那个基因型。
- 工具安装失败比分析失败更常见：TRASH（依赖）、EDTA（数据库分区缺失、RepeatMasker 引擎设置）、还有一个计算站点连不上的数据主机。先用很小的输入测安装和网络，并写明备用工具。
- 脚本里不要写死路径。路径放在本地配置里，用清单管理文件。
- 一个设计被许多小补充拆得很碎，就很难读。每次重启只留一份预注册，把最终规则写进去。

## 需要主人定的事 [待确认]

- 先做哪些项目、什么顺序。
- 项目 14 和 vitis-te 目录是合并还是分工。
- LOX、MLO、PPO、CBF 哪些放进项目 07。
- 突变率、世代时间和 OMArk 谱系数据的来源。
- 项目 13 里 2 号染色体 LOH 的想法，公开读段是否存在。
- DS11 的读段能否从 NGDC 手动导出（项目 08、10、23、24）。
- 决定项目 26 走向的问题是什么，以及项目 25 是否保持为方法调查、与项目 14 和 vitis-te 目录并行。
- 项目 23 和 24 的公开坐标系统是否用 PN_T2T [待确认]。

所有 [待确认] 项也列在各项目自己的 STATUS.md 里。

已核对的公开下载链接清单见 [data/DOWNLOADS.md](data/DOWNLOADS.md)。

状态补记，2026-11-21（UTC+8）：新增项目 23 至 26，只写到方法层面。待定事项的默认选项见 [docs/DEFAULTS.md](docs/DEFAULTS.md)（英文）。四条方法线见 [docs/METHOD_LINES.md](docs/METHOD_LINES.md)（英文）。STATUS 页只指向 README 的那些项目，其核对过的来源见 [docs/SOURCES_CHECKED_20261121.md](docs/SOURCES_CHECKED_20261121.md)。本补记与上文旧句子不一致处（例如项目数量），以本补记为准。
