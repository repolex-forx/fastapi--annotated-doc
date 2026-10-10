# Repolex Knowledge Graph of fastapi/annotated-doc

RDF knowledge graph data for [fastapi/annotated-doc](https://github.com/fastapi/annotated-doc), parsed by [repolex](https://repolex.ai).

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
rlex download fastapi/annotated-doc
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── e6e7324ff5ab80bbde7bab5e9ba2c35662e81fe5
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── e6e7324ff5ab80bbde7bab5e9ba2c35662e81fe5
│           └── chunk-001.nq.gz
├── blob
│   ├── 0052712d940b553acd6ea3d30b5604252cbec68e.nq.gz
│   ├── 0698b1e15ee45534071154e32196cb368b3c7147.nq.gz
│   ├── 0a336809bfa9ea723c8ea2448965f7733ba3bc70.nq.gz
│   ├── 0cf05a555d202c11ad627427f52c9e1e5368e914.nq.gz
│   ├── 0d60234da0d6f14d3130dfebad079eb7ca1e33cf.nq.gz
│   ├── 109425d7cc395432df4a6e942094e74176647527.nq.gz
│   ├── 11bbf09b5e073869363186a468b38af280ebce91.nq.gz
│   ├── 1591365077b207a09fca211cc2654400cbf9cdf6.nq.gz
│   ├── 1a304f681588bafefc03d970f0f8d6561574b691.nq.gz
│   ├── 2d724ecba401da7556976c7694df8fb74b4b6ae3.nq.gz
│   ├── 2e0061f5e5dfaeeda49d050646d0a8c35a129f0d.nq.gz
│   ├── 2e5e42001c7155d68abbc5e5428c20e87839b211.nq.gz
│   ├── 2ee6d72e01568893326d7fbe8d7d80a8b6770440.nq.gz
│   ├── 3e0b71187cdca13c4e5465b25ebb9c8f66397be5.nq.gz
│   ├── 510b8f9515fa39fdd779d694498cfae689b395e8.nq.gz
│   ├── 5805c206319498efff5311901b1adc9debcd2749.nq.gz
│   ├── 58bb20b090879360085ae7da8764d458648c54cb.nq.gz
│   ├── 7063c59e4500a1d02bfc9b41887f9e95f8163507.nq.gz
│   ├── 71e1126dcbdd743a9b52c84421a9bf2507eb43c7.nq.gz
│   ├── 770f853009936499acf9dd4aaa7fb31d3f256705.nq.gz
│   ├── 7a254464cc78ccea32b3ded00513c44c4e4da412.nq.gz
│   ├── 909228ecd52f3640b066f2c04d24b1d3e23b8353.nq.gz
│   ├── 94ec1a3fd6983ce9bf87c7e45c571accecaa1de2.nq.gz
│   ├── 9c8a1c8f5df288b41f89381e94d69e80b9a0278c.nq.gz
│   ├── a3d03bfab198d8e48f8565a4c29db0879bfeb9b7.nq.gz
│   ├── b5b50a8483601cca30079868ec133ce1a09dac64.nq.gz
│   ├── bc945f95d352e45801d9c2c3c10a33a75502d4eb.nq.gz
│   ├── bd28b9c5c27e0dfa60da94179ec9b23f2be8be0c.nq.gz
│   ├── c9aa5241927d47da74b344d6457b0f8f474324ac.nq.gz
│   ├── d6f729253cbdcfad8b1aa27513d4de07e443cf05.nq.gz
│   ├── dd0745329502a1145fa171e8130cbd3c76676e14.nq.gz
│   ├── e07b51ec5932dac2c6cac43c7cf8539c48471a8d.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   ├── e7f3a5f539e9330b4a85867fa7396deb4ebd043d.nq.gz
│   ├── ebf0cd44d41c167444e22da70cc1e00da99d4076.nq.gz
│   ├── ef92dd28b2307900386d46537a000659c1f437c4.nq.gz
│   ├── f79b147acc522bebcbc38cb606909d0dbc56fabd.nq.gz
│   └── f87f906dc23ca7421b67c56eae955d577bc5f399.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── e6e7324ff5ab80bbde7bab5e9ba2c35662e81fe5.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 46 files
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

[fastapi/annotated-doc](https://github.com/fastapi/annotated-doc)

---
*Parsed on 2026-10-10 by [repolex](https://repolex.ai)*
