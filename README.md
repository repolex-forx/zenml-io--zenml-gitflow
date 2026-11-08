# Repolex Knowledge Graph of zenml-io/zenml-gitflow

RDF knowledge graph data for [zenml-io/zenml-gitflow](https://github.com/zenml-io/zenml-gitflow), parsed by [repolex](https://repolex.ai).

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
rlex download zenml-io/zenml-gitflow
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 9d832d0286719223b58d6e45038e74c01481d5ac
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 9d832d0286719223b58d6e45038e74c01481d5ac
│           └── chunk-001.nq.gz
├── blob
│   ├── 03c6b2b6e6a75de7f226f45be6a4516b74d15f87.nq.gz
│   ├── 111f9bc117eb9d49a05ef428095dea188bbaba17.nq.gz
│   ├── 15f7b3b86e0694e8420522098eed70722d695c59.nq.gz
│   ├── 349cc3e534e24bd0f70098a25926144ff9d3e19d.nq.gz
│   ├── 3bbda4a563680e4b51506ba47300768cb1e4c2aa.nq.gz
│   ├── 3ea7fe7cf9b3a883f9a6797a26829e9a1d2c1765.nq.gz
│   ├── 456ead700a62fda4000378ef4a9ddf4bc8bf2702.nq.gz
│   ├── 48b1947bbc73497cc5f4709d1d3c3f6fb5c943b9.nq.gz
│   ├── 51b84d6419cbcc06d1090c60c8823b49751bf62d.nq.gz
│   ├── 52abefe369d35e0055984811cf6b299b22df5576.nq.gz
│   ├── 5403f163a5f0870a2b2ed52063e63bba8947a085.nq.gz
│   ├── 556c53c069531549901106a3f36d06e079dcf584.nq.gz
│   ├── 61318b1694c4e522ccc36be85429053d972d393e.nq.gz
│   ├── 622cb1dc4f5438d16d8ec4b7351642756e35cfdd.nq.gz
│   ├── 6ccf8d021c1b674cdeb625954a601f08172d0000.nq.gz
│   ├── 6fc8678c41ff34cc7c23a6c7a8c88c6b7e0b9d14.nq.gz
│   ├── 7018d6dd6e7b196f4d8faa3a4871c9ccf9c16fb3.nq.gz
│   ├── 7045d152b2c8775187bb9845b9558a9fa13af601.nq.gz
│   ├── 73c44a7214b73af6973463d72fe7f93de950edd0.nq.gz
│   ├── 774f065ccf23a02e1941905d25e8cabfea29ade1.nq.gz
│   ├── 84c94a6250ee309a5e453f0599f74d7e05429557.nq.gz
│   ├── 8b7a4c3bf198113a906fb3f82bf1732b591f0e9e.nq.gz
│   ├── 9b63679c8112d73baf4fc34588de5af3708c6f82.nq.gz
│   ├── 9bd401a74a176d4f2e33706e8f67da935b7e1656.nq.gz
│   ├── a042dd9ad026118d1df57d3513b8aaf5545c61c9.nq.gz
│   ├── a2e94356e93556c28362d88f3f7d383602f7cbba.nq.gz
│   ├── c65290df92f059f8485453e8e2b8d4074aaba99a.nq.gz
│   ├── ccc340256f06a0ced7cfb7dd8d3515c3e9537f2c.nq.gz
│   ├── ccdc87a8f540fa99dced9026d931a917eeb60a87.nq.gz
│   ├── cdadcb95f9202cb98fdcac6aaefd7d8ef9fac2bf.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   ├── f54fb5bf2f1c8927f1f88cb4d3d6e3eb025c2b55.nq.gz
│   ├── f5fdd464adea2b4921bca8bd5f310b41b4fdc582.nq.gz
│   ├── f6e603692c6e0ebc3100c76338939bd68afa2c5d.nq.gz
│   ├── f7975bb3e9f12d44ca3472d880e173f4099b801e.nq.gz
│   └── f7c474fa1fd659c93492843e61382c5d0a842f47.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 9d832d0286719223b58d6e45038e74c01481d5ac.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 44 files
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

[zenml-io/zenml-gitflow](https://github.com/zenml-io/zenml-gitflow)

---
*Parsed on 2026-11-08 by [repolex](https://repolex.ai)*
