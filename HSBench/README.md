# Hierarchical HS Code Benchmark and Knowledge Resources

This repository provides an open and extensible benchmark and knowledge resource for hierarchical HS code classification and reasoning.

The repository releases, as a research contribution, a curated HS-domain knowledge base together with multilingual benchmark datasets designed for evaluating structure-aware, graph-guided, and reasoning-based classification methods.

## 1. Motivation and Scope

Accurate classification under the Harmonized System (HS) is inherently hierarchical, rule-constrained, and knowledge-intensive.
However, most existing benchmarks formulate HS coding as a flat text classification problem, lacking:

- Explicit hierarchical structure

- Formalized exclusion rules

- A clear separation between domain knowledge and task-oriented data

This repository addresses these limitations by jointly releasing:

- A structured HS knowledge layer, explicitly modeling taxonomy, definitions, and exclusions

- Task-oriented benchmark datasets, designed to evaluate hierarchical consistency and reasoning behavior

Crucially, the HS knowledge resources themselves constitute an independent and reusable research contribution, enabling investigation beyond any single model, method, or paper.

## 2. Repository Structure
```
├── knowledge/
│   ├── hs_nodes.json
│   ├── hs_taxonomy.json
│   └── hs_exclusions.json
├── datasets/
│   ├── cn/
│   │   ├── hsbench_4digit.json
│   │   └── hsbench_6digit.json
│   └── en/
│       ├── hsbench_4digit.json
│       └── hsbench_6digit.json
└── README.md
```

- knowledge/ contains task-independent HS domain knowledge

- datasets/ contains multilingual benchmark datasets (Chinese / English)

- Knowledge resources and datasets are strictly decoupled by design

## 3. HS Knowledge Resources (Core Contribution)

The knowledge/ directory encodes explicit, machine-readable HS domain knowledge, independent of any downstream task, model, or evaluation protocol.

### 3.1 hs_nodes.json

Defines HS nodes across hierarchical levels.

Each node includes:

- code (string)
    Valid formats:

    Pure digits (e.g., 01, 0106, 010619)

    Section-level identifiers: digits followed by 类 (e.g., 1类)

- level (string)
    One of:
    section | chapter | heading | subheading | extension


- name (string)
    Official HS designation

- abstract (string, optional)
    Expert-curated semantic summary for reasoning and candidate discrimination

- description (string, optional)
    Detailed explanatory text

- exclude (string, optional)
    Exclusion notes associated with the node

All nodes are validated to ensure code format correctness and level consistency.

### 3.2 hs_taxonomy.json

Defines the explicit hierarchical structure of the HS system.

- Fields:

    levels
    Ordered hierarchy:

    ["section", "chapter", "heading", "subheading", "extension"]


- edges

    Parent–child containment relations:

    parent: parent HS code

    child: child HS code

Only structural containment relations are included.
All references are guaranteed to exist in hs_nodes.json.

### 3.3 hs_exclusions.json

Encodes explicit exclusion relations derived from HS explanatory rules.

For each source node, the file specifies:

- Excluded target nodes

- Optional exclusion conditions or rationale

This resource supports:

- Regulation-aware reasoning

- Invalid-path detection

- Hierarchical backtracking and redirection

Unlike flat classification labels, exclusion knowledge enables non-monotonic and constraint-aware inference.

## 4. Benchmark Datasets

The datasets/ directory contains task-oriented classification benchmarks, separated by:

Language: cn / en

Granularity: 4-digit / 6-digit

Each dataset is aligned with the released HS knowledge but does not embed or leak that knowledge.

### 4.1 Common Sample Format

Each sample includes:

- id: unique sample identifier

- input.text: product description text (HS names excluded)

- label: explicit hierarchical HS labels by level

HS names are intentionally excluded from inputs to prevent label leakage.

### 4.2 hsbench_4digit.json

Targets medium-grained classification at the 4-digit (heading) level.

Each label includes:

- label.hs2

- label.hs4

This setting reflects practical scenarios where product descriptions are coarse and lack fine-grained technical detail.

### 4.3 hsbench_6digit.json

Targets fine-grained classification at the 6-digit (subheading) level.

Each label includes:

- label.hs2

- label.hs4

- label.hs6

Descriptions typically include discriminative attributes such as usage, material, or processing method, enabling evaluation of hierarchical stability and reasoning precision.