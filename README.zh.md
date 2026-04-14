# HSBench

本仓库为论文《HSGraphAgent: Knowledge-Graph-Guided Large Language Models for Harmonized System Code Classification》的配套开源项目。

该论文已被 **ACL 2026 main** 接受。

[English](README.md) / 中文

## 仓库说明

本仓库主要提供：

- HS 代码图谱知识资源
- HS 代码分类基准数据集
- 与 HSGraphAgent 论文中所使用的数据和图谱相配套的开源资源

本仓库提供一个开放、可扩展的层次化 HS 编码分类与推理资源库。

当前发布内容包括经过整理的 HS 领域知识库，以及中英文基准数据集，可用于评估结构感知、图谱引导和推理型分类方法。

## 目录结构

- `knowledge/`：机器可读的 HS 知识图谱资源
- `datasets/`：多语言 HS 分类基准数据集
  - `datasets/cn/`：中文数据集
  - `datasets/en/`：英文数据集
- `hscode_cn_2025/`：中文 HS 层次结构数据（CSV 格式）

## 动机与范围

HS 编码分类本身具有明显的层次性，也受到规则和领域知识约束。很多现有基准仍把它当作普通文本分类任务，没有明确体现层级结构、排除规则，也没有把知识资源和任务数据拆开。

本仓库希望补上这部分空缺，公开以下内容：

- 结构化 HS 知识层，覆盖层级关系、定义和排除关系
- 面向任务的基准数据集，用于评估层级一致性和推理能力

这些知识资源本身也可以单独复用，不依赖某一个具体模型或评测方案。

## HS 知识资源

`knowledge/` 目录保存与具体任务解耦的 HS 领域知识。

### `knowledge/hs_nodes.json`

定义不同层级的 HS 节点。每个节点至少包含编码、层级和名称，也可能包含语义摘要、说明文本或排除说明。

### `knowledge/hs_taxonomy.json`

定义 HS 体系的显式层级关系，覆盖以下层级：

- `section`
- `chapter`
- `heading`
- `subheading`
- `extension`

### `knowledge/hs_exclusions.json`

定义从 HS 说明规则中整理出的排除关系，可用于规则约束推理、无效路径识别和层级回退。

## 基准数据集

`datasets/` 目录保存面向分类任务的数据集，按语言和标注粒度组织。

- 语言：`cn`、`en`
- 粒度：4 位、6 位

每条样本包含：

- `id`：样本唯一编号
- `input.text`：商品描述文本
- `label`：按层级组织的 HS 标签

输入中不直接包含 HS 名称，以减少标签泄露。

### `datasets/*/hsbench_4digit.json`

用于 4 位编码分类，标签包含 `hs2` 和 `hs4`。

### `datasets/*/hsbench_6digit.json`

用于 6 位编码分类，标签包含 `hs2`、`hs4` 和 `hs6`。

## 中文 HS 层次结构数据

`hscode_cn_2025/` 目录中的 CSV 已统一整理为三列：

- `code`
- `name`
- `description`

这些文件适合直接用于检索、映射和说明展示。

## 目标

本仓库面向 HS 代码分类与推理研究，特别是：

- 研究层次化 HS 编码问题
- 支持基于知识图谱的模型与推理方法
- 提供可复现的数据与知识资源

## 引用

如果你使用本仓库中的资源，请引用论文：《HSGraphAgent: Knowledge-Graph-Guided Large Language Models for Harmonized System Code Classification》。
