# Repolex Knowledge Graph of certifi/cert-tools

RDF knowledge graph data for [certifi/cert-tools](https://github.com/certifi/cert-tools), parsed by [repolex](https://repolex.ai).

> **Note**: This data is experimental and subject to change without notice.

## How to use this data

The easiest way to get started is to install the [rlex](https://github.com/repolex-ai/rlex) query tool:

```bash
cargo install --git https://github.com/repolex-ai/rlex
```

Verify the install:

```bash
rlex --help
```

**rlex is designed to be used primarily by LLMs in a terminal.** Start up your favorite AI assistant and ask it to use rlex. It handles the SPARQL — you just ask questions in plain English.

To load this repo's data:

```bash
rlex download certifi/cert-tools
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 94ff3b87f5d2bce9fe66c1d01b91947bdb37f663
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 94ff3b87f5d2bce9fe66c1d01b91947bdb37f663
│           └── chunk-001.nq.gz
├── blob
│   ├── 0f0e3a9a06efa2e60558878811ff5b2f06df9425.nq.gz
│   ├── 2f48d5b640912407a4e7c1ee2f10cfcf756f19c0.nq.gz
│   ├── 8d37d887459c0cdbacf2e029a79571b9f3454b7e.nq.gz
│   ├── 9ad007a4d5c43bbdae71a2cc7ad9006a3912e65d.nq.gz
│   └── bfa6c01ea805561f6fc452926b70748d083bc5da.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 94ff3b87f5d2bce9fe66c1d01b91947bdb37f663.nq.gz
└── tag
    └── tag.nq.gz

11 directories, 11 files
```

| Directory | What it contains |
|-----------|-----------------|
| `blob/` | Per-file AST graphs, content-addressed by git blob SHA. Each file in the source repo gets its own graph. |
| `aggregate/ast/` | Combined AST graph per parsed commit. Merges all blob graphs for a snapshot of the entire codebase at that point. |
| `aggregate/lsp/` | Language Server Protocol enrichment: resolved symbols, definitions, references, and type information. |
| `aggregate/dataflow/` | Interprocedural data flow edges between functions and modules. |
| `aggregate/repolex/` | Combined graph (AST + LSP + dataflow) per commit. |
| `commit/` | Git commit metadata (author, date, message, parent links). |
| `branch/` | Branch metadata. |
| `tag/` | Tag metadata. |
| `filetree/` | File tree snapshots per commit (which files existed and their blob SHAs). |
| `audit/` | Code architecture and graph audit reports per commit. |

## Source repository

[certifi/cert-tools](https://github.com/certifi/cert-tools)

---
*Parsed on 2026-10-11 by [repolex](https://repolex.ai)*
