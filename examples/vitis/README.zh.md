# 葡萄（*Vitis*）完整范例

写于 2026-11-21（UTC+8）。[English](README.md)

本文件夹把[六维缺口框架](../../framework/GAP_FRAMEWORK.zh.md)完整地用在葡萄上，存放仓库里全部葡萄内容：公开数据、可复用分析步骤、26 个项目，以及给它们排序、建索引和做核查的页面。所有项目都要遵守的工作规则见 [START_HERE.zh.md](../../START_HERE.zh.md)。

## 这里有什么

| 路径 | 内容 | 原路径 |
|---|---|---|
| [data/](data/) | DS01 到 DS23：每个公开数据集一个文件夹；[data/DOWNLOADS.md](data/DOWNLOADS.md) 列出已核查的下载链接 | `data/` |
| [analyses/](analyses/) | AM01 到 AM26：可复用步骤，含工具、命令、输出和大致资源 | `analyses/` |
| [projects/](projects/) | 26 个项目；01 到 22 有 README（方案）和 STATUS，23 到 26 只有 STATUS | `projects/` |
| [INDEX.md](INDEX.md) | 每个项目用哪些模块，以及项目怎样拆成论文 | `docs/INDEX.md` |
| [RANKING.md](RANKING.md) | 冻结的分数、独立复评和调整登记表 | `docs/RANKING.md` |
| [DEFAULTS.md](DEFAULTS.md) | 待定项的默认做法 | `docs/DEFAULTS.md` |
| [NOT_KEPT.md](NOT_KEPT.md) | 核查后未收入的方向及覆盖它们的论文 | `docs/NOT_KEPT.md` |
| [METHOD_LINES.md](METHOD_LINES.md) | 四条方法线（项目 23 到 26） | `docs/METHOD_LINES.md` |
| [SOURCES_CHECKED_20261121.md](SOURCES_CHECKED_20261121.md) | 2026-11-21 的 Crossref 核查记录 | `docs/SOURCES_CHECKED_20261121.md` |
| [EARLIER_LINES.md](EARLIER_LINES.md) | 早先尝试与项目文件夹的对应关系，主要用于追溯项目来历 | `docs/EARLIER_LINES.md` |
| [CHECK.md](CHECK.md) | 2026-11-14 的链接、DOI、登录号和一致性核查，2026-11-21 在文末加了说明 | `CHECK.md` |

这些页面正文里以纯文本写出的路径（例如 `docs/DEFAULTS.md`、`data/DOWNLOADS.md`）指的是原来的目录结构，当时 `data/`、`analyses/`、`projects/` 和 `docs/` 都在仓库顶层。`docs/X.md` 现在是 `examples/vitis/X.md`；PREREGISTRATION、EVIDENCE_LOG_TEMPLATE、DATA_PREP 和 HPC_JOBS 例外，现在在 [templates/](../../templates/)。链接都已更新。

## 方向映射

下表把 26 个项目放进六个维度。这是 2026-11-21 写的提议：没有合并、改名或删除任何文件夹，[RANKING.md](RANKING.md) 里冻结的分数不变。建议的合并、项目 21 和 26 的降级、以及对项目 09 的提议，都等维护者决定 [待确认]。项目 22 在 RANKING.md 里本来就已降级。

| 维度 | 保留 | 建议合并或联动 | 降级（满足条件才启动） | 建议移出主线 |
|---|---|---|---|---|
| 1. 数据与资源 | [08](projects/08-harmonised-sample-panel/) 统一样本身份表，所有群体项目的底座；[23](projects/23-family-parentage/STATUS.md) 亲子与亲缘质控，紧接 08 | 08 与 23 共用去重样本池和 SNP 集，可以作为上下游联动 | 无 | 无 |
| 2. 基因组结构与细胞器 | [01](projects/01-telomere-and-interstitial-telomeric-repeats/) 端粒与 ITS；[02](projects/02-rdna-arrays/) rDNA 阵列；[07](projects/07-metabolic-gene-families/) STS、TPS、CCD、LOX 家族；[18](projects/18-vitis-muscadinia-centromeres/) 着丝粒与 chr7 融合点，解除暂停后与 01、02 并行 | [05](projects/05-gene-pav-across-pangenomes/) + [06](projects/06-vitis-pan-nlrome/) 合为一篇两节的论文（共用去重与距离矩阵）[待确认]；01 + 02 可选合为一篇重复阵列论文（[INDEX.md](INDEX.md) 中的 A2）[待确认] | [26](projects/26-mitochondrial-genomes/STATUS.md) 线粒体基因组、NUMT 与异质性，核心科学问题定下来之前 [待确认] | 无 |
| 3. 多尺度变异与可移动元件 | [03](projects/03-endogenous-florendoviruses/) 内源 florendovirus；[13](projects/13-somatic-mutation-spectra-across-cultivars/) 跨品种体细胞突变谱（chr2 LOH 想法继续搁置）；[14](projects/14-te-insertion-polymorphisms-cultivated/) 图上 TE 插入多态；[16](projects/16-graph-sv-load/) 遗传与克隆半合子 SV；[17](projects/17-large-inversions-in-populations/) 大倒位 | [25](projects/25-te-annotation-methods/STATUS.md) 与 14 明确分工：25 是方法综述，14 是实证分析；不重复建插入库 | 无 | 线性参考有害负荷方向在 [NOT_KEPT.md](NOT_KEPT.md)，方法保留在 AM12 |
| 4. 群体演化、驯化与繁殖系统 | [10](projects/10-arg-domestication-timing/) ARG 与驯化定年，校准优先，方法学论文 K1 兜底；[15](projects/15-graph-introgression/) 图上 SV 渐渗；[20](projects/20-ancient-seeds-on-graph/) 古葡萄种子图比对 | [24](projects/24-recombination-maps/STATUS.md) 作为方法线与 23、10 衔接；基于 LD 的重组率与系谱重组率严格分开 | [22](projects/22-sex-region-population-level/) 性别决定区，除非找到足够的野生性别记录，否则维持降级 | 无 |
| 5. 表达、调控与表观遗传 | [19](projects/19-public-rnaseq-on-t2t/) PN_T2T 上的公开 RNA-seq，先图谱（S1），后 QTL 与 ASE（S2、S3）；[11](projects/11-sequence-to-function-models/) 序列到表达模型，依赖 19 | 无 | 无 | 群体 WGBS、单细胞调控、Hi-C/TAD 和移动 mRNA 维持在 [NOT_KEPT.md](NOT_KEPT.md) |
| 6. 表型、功能与跨物种比较 | [04](projects/04-virus-discovery-in-public-data/) 公开数据病毒发现；[12](projects/12-convergent-domestication-cross-crop/) 跨作物趋同驯化 | 无 | [21](projects/21-gwas-meta-and-cross-ancestry-prediction/) GWAS 荟萃与预测，公开表型清点通过后才启动 [待确认] | [09](projects/09-berry-colour-locus-graph/) 浆果颜色位点：建议改作图分型（AM07）的教学与测试范例，而不是主线项目 [待确认]；维护者决定之前仍是 Quick 项目 |

这 26 个之外可能的方向（叶绿体泛基因组与核质互作；跨单倍型蛋白结构演化）在框架里标为 [待确认]，没有建文件夹。

## 说明

- **项目 23 到 26** 只有 STATUS：没有 README，RANKING.md 里没有 F/N/E 分数，INDEX.md 的矩阵里也没有这几行。这几个项目请读 [METHOD_LINES.md](METHOD_LINES.md) 和各自的 STATUS，而不是 README。是补 README 和分数，还是在 INDEX.md 里给方法线单列一节，[待确认]。
- **ITS** 在本范例中指间质端粒重复（项目 01 和 18），不是 rDNA 单元里的内转录间隔区（ITS1、ITS2），后者属于项目 02 的 rDNA 话题。两种意思都可能被读到的地方，请写全称。
- **CHECK.md** 生成于 2026-11-14，覆盖项目 01 到 22、DS01 到 DS22 和 103 个 DOI；不覆盖项目 23 到 26、DS23，也不覆盖 2026-11-21 仓库里约 150 个不重复的 DOI 字符串。在新目录结构上完整重跑一次 [待确认]；见 [CHECK.md](CHECK.md) 文末说明。

## 怎样开始一个葡萄项目

1. 读 [INDEX.md](INDEX.md)、[RANKING.md](RANKING.md) 和 [DEFAULTS.md](DEFAULTS.md)，确认该项目是否被建议合并、是否降级、待定项有没有默认做法（例如首轮不用 DS11、DS02 用精确列表）。
2. 读项目的 README 和 STATUS；STATUS 有带日期的补记时，以最新一条为准。项目 23 到 26 读 METHOD_LINES.md 和 STATUS。再读 [NOT_KEPT.md](NOT_KEPT.md)，避免重复已发表的工作。
3. 读 [data/DOWNLOADS.md](data/DOWNLOADS.md) 以及项目用到的 DS、AM 模块，确认每个输入都是 `available`。
4. 填写 [templates/PREREGISTRATION.md](../../templates/PREREGISTRATION.md)：样本清单、对照通过线、统计检验和止损规则。预注册提交、对照通过之前，不看主结果。
5. 按 [templates/HPC_JOBS.md](../../templates/HPC_JOBS.md) 和 [templates/DATA_PREP.md](../../templates/DATA_PREP.md) 做小规模试跑和校验和清单，每一步都追加写入项目证据日志（[templates/EVIDENCE_LOG_TEMPLATE.md](../../templates/EVIDENCE_LOG_TEMPLATE.md)）。
