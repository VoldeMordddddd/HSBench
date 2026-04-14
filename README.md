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

This repository provides an open and extensible benchmark and knowledge resource for hierarchical HS code classification and reasoning.

The release includes a curated HS-domain knowledge base together with multilingual benchmark datasets for evaluating structure-aware, graph-guided, and reasoning-based classification methods.

## Repository structure

- `knowledge/`: machine-readable HS knowledge graph data
- `datasets/`: multilingual benchmark datasets for HS classification
  - `datasets/cn/`: Chinese benchmark sets
  - `datasets/en/`: English benchmark sets
- `hscode_cn_2025/`: Chinese HS hierarchy and rule resources in CSV format

## Motivation and Scope

Accurate classification under the Harmonized System is hierarchical, rule-constrained, and knowledge-intensive. Many benchmarks still treat HS coding as flat text classification and do not expose hierarchy, exclusion rules, or a clean split between domain knowledge and task data.

This repository addresses that gap by releasing:

- a structured HS knowledge layer covering taxonomy, definitions, and exclusions
- task-oriented benchmark datasets for hierarchical consistency and reasoning evaluation

The knowledge resources are reusable on their own and are not tied to one model or evaluation setup.

## HS Knowledge Resources

The `knowledge/` directory stores task-independent HS domain knowledge.

### `knowledge/hs_nodes.json`

Defines HS nodes across hierarchical levels. Each node includes a code, level, and official name, and may also include a semantic summary, explanatory description, or exclusion note.

### `knowledge/hs_taxonomy.json`

Defines the explicit hierarchy of the HS system through parent-child relations across these levels:

- `section`
- `chapter`
- `heading`
- `subheading`
- `extension`

### `knowledge/hs_exclusions.json`

Encodes exclusion relations derived from HS explanatory rules. This supports regulation-aware reasoning, invalid-path detection, and hierarchical backtracking.

## Benchmark Datasets

The `datasets/` directory contains task-oriented HS classification benchmarks, organized by language and label granularity.

- Languages: `cn`, `en`
- Granularity: 4-digit, 6-digit

Each sample contains:

- `id`: unique sample identifier
- `input.text`: product description text
- `label`: hierarchical HS labels by level

HS names are excluded from inputs to reduce label leakage.

### `datasets/*/hsbench_4digit.json`

Targets 4-digit heading classification. Labels include `hs2` and `hs4`.

### `datasets/*/hsbench_6digit.json`

Targets 6-digit subheading classification. Labels include `hs2`, `hs4`, and `hs6`.

## Purpose

This repository is intended for HS code classification and reasoning research, especially:

- studying hierarchical HS coding
- enabling knowledge-graph-guided LLM methods
- providing reproducible data and knowledge resources

## Citation

If you use the resources in this repository, please cite the paper:

> HSGraphAgent: Knowledge-Graph-Guided Large Language Models for Harmonized System Code Classification
