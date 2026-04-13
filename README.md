# HSBench

This repository is the official open-source companion to the paper:

**HSGraphAgent: Knowledge-Graph-Guided Large Language Models for Harmonized System Code Classification**

The paper has been accepted at **ACL 2026 main**.

If you prefer Chinese, see the translated version:

- [README.zh.md](README.zh.md)

## Overview

HSBench provides:

- A knowledge graph for Harmonized System (HS) codes
- Benchmark datasets for HS code classification
- Open resources that support the paper's graph-guided modeling and dataset design

## Repository structure

- `HSBench/`: core HSBench datasets and knowledge resources
  - `HSBench/README.md`: detailed description of the resources and dataset formats
  - `HSBench/knowledge/`: machine-readable HS knowledge graph data
  - `HSBench/datasets/`: benchmark datasets for HS classification
- `hscode_cn_2026/`: Chinese HS hierarchy and rule resources in CSV format

## Purpose

This repository is intended for HS code classification and reasoning research, especially:

- studying hierarchical HS coding
- enabling knowledge-graph-guided LLM methods
- providing reproducible data and knowledge resources

## Citation

If you use the resources in this repository, please cite the paper:

> HSGraphAgent: Knowledge-Graph-Guided Large Language Models for Harmonized System Code Classification
