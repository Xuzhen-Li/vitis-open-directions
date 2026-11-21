# 把框架迁移到其他物种

写于 2026-11-21（UTC+8）。[English](SPECIES_TRANSFER_GUIDE.md)

下面的步骤把一个新物种从零带到一份排好序、每项都可以开始预注册的方向清单。[examples/vitis/](../examples/vitis/) 里的葡萄范例展示了完成后的页面是什么样子。

## 步骤

1. 读 [README.zh.md](../README.zh.md) 和 [START_HERE.zh.md](../START_HERE.zh.md)，了解工作规则：预注册先行，证据日志只追加，没有打开过的 DOI 标 [待确认]，不用私有数据，不编造数字。
2. 填写 [templates/SPECIES_INTAKE_CHECKLIST.md](../templates/SPECIES_INTAKE_CHECKLIST.md)：参考基因组、群体面板、转录组、细胞器基因组、表型、繁殖系统和访问限制。
3. 通过数据库 API 核实清单里的每个输入，标一个状态：`available`、`portal`、`blocked` 或 `not found`（见 [GAP_FRAMEWORK.zh.md](GAP_FRAMEWORK.zh.md)）。记录登录号、所用 API、日期和文件大小。
4. 按 [GAP_FRAMEWORK.zh.md](GAP_FRAMEWORK.zh.md) 的六个维度逐一检索。每个候选缺口填一份 [templates/GAP_AUDIT_TEMPLATE.md](../templates/GAP_AUDIT_TEMPLATE.md)。
5. 通过 Crossref 或 DataCite 记录和原文核查文献，写下检索式和日期。
6. 写出该物种的未收入清单（已被覆盖或公开数据撑不起来的方向，各附覆盖它的论文）和候选方向清单。
7. 按 [EVALUATION_RUBRIC.zh.md](EVALUATION_RUBRIC.zh.md) 给候选方向打分，包括独立复评，并注明日期冻结分数。
8. 为每个保留方向写项目页（缺口、已有工作、问题、假设与判据、数据、步骤、论文拆分、风险、集群计划）和状态页。
9. 在看任何主结果之前填写 [templates/PREREGISTRATION.md](../templates/PREREGISTRATION.md)。下载、校验和与小规模试跑按 [templates/DATA_PREP.md](../templates/DATA_PREP.md) 和 [templates/HPC_JOBS.md](../templates/HPC_JOBS.md) 来做，每一步都追加写入项目的证据日志（[templates/EVIDENCE_LOG_TEMPLATE.md](../templates/EVIDENCE_LOG_TEMPLATE.md)）。

新物种建议放在 `examples/<物种>/`，结构与葡萄范例相同：`data/`、`analyses/`、`projects/`、索引页、排序页、默认值页和未收入清单。

## 没有外网时

很多模型会话和集群计算节点访问不了数据库。这时：

- 所有没有实测过的登录号和 DOI 一律标 [待确认]。
- 写出可以在联网登录节点上直接运行的查询命令，例如：

```bash
# 项目下的测序 run 与 FASTQ 大小（ENA portal API）
curl -s "https://www.ebi.ac.uk/ena/portal/api/filereport?accession=PRJNAxxxxxx&result=read_run&fields=run_accession,instrument_platform,fastq_bytes,fastq_md5&format=tsv"
# 组装概要（NCBI Datasets 命令行工具）
datasets summary genome accession GCF_xxxxxxxxx.x
# Zenodo 记录的文件列表
curl -s "https://zenodo.org/api/records/RECORD_ID"
# DOI 记录
curl -s "https://api.crossref.org/works/DOI_HERE"
```

- 等查询结果回传之后，再进入打分和预注册。
