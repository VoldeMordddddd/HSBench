# HSBench

本仓库为论文《HSGraphAgent: Knowledge-Graph-Guided Large Language Models for Harmonized System Code Classification》的配套开源项目。

该论文已被 **ACL 2026 main** 接受。

如果你希望使用英文版，请参见：

- [README.md](README.md)

## 仓库说明

本仓库主要提供：

- HS 代码图谱知识资源
- HS 代码分类基准数据集
- 与 HSGraphAgent 论文中所使用的数据和图谱相配套的开源资源

## 目录结构

- `HSBench/`：核心知识图谱与 HSBench 数据集
  - `HSBench/README.md`：详细描述知识资源与数据集结构
  - `HSBench/knowledge/`：HS 知识图谱资源
  - `HSBench/datasets/`：HSBench 任务数据集
- `hscode_cn_2026/`：中文 HS 代码层次结构及相关规则数据（CSV 格式）

## 目标

本仓库面向 HS 代码分类与推理研究，特别是：

- 研究层次化 HS 编码问题
- 支持基于知识图谱的模型与推理方法
- 提供可复现的数据与知识资源

## 引用

如果你使用本仓库中的资源，请引用论文：《HSGraphAgent: Knowledge-Graph-Guided Large Language Models for Harmonized System Code Classification》。
