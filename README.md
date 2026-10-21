# Repolex Knowledge Graph of scverse/benchmark

RDF knowledge graph data for [scverse/benchmark](https://github.com/scverse/benchmark), parsed by [repolex](https://repolex.ai).

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
rlex download scverse/benchmark
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 8a802b24891cd85c95508e127e25b36f61ed7770
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 8a802b24891cd85c95508e127e25b36f61ed7770
│           └── chunk-001.nq.gz
├── blob
│   ├── 0951c4439f95f235b05f26b27b3ff35a9abe5d40.nq.gz
│   ├── 123fe39733e7bc53de75c437e155ee2f1ac44c6b.nq.gz
│   ├── 1321fc379078e6df49f8e1ca8d74cbcc127d26ef.nq.gz
│   ├── 180ec1e7ff79ce1b9fddcb3761e385f9eb4d8f11.nq.gz
│   ├── 1ed51578200b0e80cabbf7e20b37530bb389a3d1.nq.gz
│   ├── 238d39dbac9d265311f7a1dfca6294eda0b1e35e.nq.gz
│   ├── 2bd429d161dba7125a388711435f53d2795ab88d.nq.gz
│   ├── 2c3af0d3b5a62f2d60bd54b49cf19a4a002b1ad4.nq.gz
│   ├── 332505187b4d1839065d60297f0397de77340c72.nq.gz
│   ├── 48c432922c668c42e521a52e45524c33f2736daf.nq.gz
│   ├── 4e552551610c5e1b5546e17047428fb411fa4bff.nq.gz
│   ├── 4ed0eec6e35f33d195ee0bb90b1a9baeaa3164fe.nq.gz
│   ├── 52234408c66db4a962854c81f5df3d911332340b.nq.gz
│   ├── 5287ca61e2e858c180f557f684fd9db201b89d6c.nq.gz
│   ├── 57cbd70f45cf8b6aaed9c7eef506bf447e4f0dce.nq.gz
│   ├── 580b3447f55cafb0ed35539d5b4c7d3d435f68d0.nq.gz
│   ├── 58766117f0317fc9800fb038b302e0fe2b567f0b.nq.gz
│   ├── 70bc7aee2048f32f3745049f755f2efe08fffe6a.nq.gz
│   ├── 7ac417a0cdeb391be77213987832e713a1bcb859.nq.gz
│   ├── 80bfb411d52e0d17d48d636a6c3da3fe9b3fbdb5.nq.gz
│   ├── 86d888bc6d577c98ae37b675f73ef7788a8a9fab.nq.gz
│   ├── 87e2f0cdbe615aaca3f16b117fd9d84a845a2bec.nq.gz
│   ├── 898c833be876fe8b63d0a117e74ddd39693c5025.nq.gz
│   ├── a08ef9cecba933c71c19248361fd7440f28afa86.nq.gz
│   ├── ad99a4b0425c6ea6f26078793153dca965714566.nq.gz
│   ├── b268c4fa8989d8580e5c9b98bccf5c68ba1682cd.nq.gz
│   ├── b294848a19e21f731a7720a1451ceb67c7813ac7.nq.gz
│   ├── b7953562da80b448a1be2700a133da6f00c34c6e.nq.gz
│   ├── bb9c5e23aff5778745fbe78ab5fee08da8d91d0e.nq.gz
│   ├── bdc4cdb4cf160d1c30688764d7f392edca626b6d.nq.gz
│   ├── bed449ecf7e0ea57b241d06ff43357e38efe5bde.nq.gz
│   ├── caa773d056dd00e1b3ff207f41ea6b8fecf2f19d.nq.gz
│   ├── cce7fc195a7278c883ca8b89fc047fe4678f516f.nq.gz
│   ├── d9872b7fa53ef4d7bf12ca1ea5f49659144779f6.nq.gz
│   ├── dacaef05cb18e2017c33b14a79bc348c9da657e6.nq.gz
│   ├── e46d7578e4867a9a0fb82e7e4cf1d7312d8cf98d.nq.gz
│   ├── ea26165009a434dec8f13a97be669483bbfac3fa.nq.gz
│   ├── f288702d2fa16d3cdf0035b15a9fcbc552cd88e7.nq.gz
│   ├── f3dbd772e05352f725d83bff3e8c485d1fd3f871.nq.gz
│   └── ff19fdc405d97c7137984ec4bee76c3135a5ec9d.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 8a802b24891cd85c95508e127e25b36f61ed7770.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 48 files
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

[scverse/benchmark](https://github.com/scverse/benchmark)

---
*Parsed on 2026-10-21 by [repolex](https://repolex.ai)*
