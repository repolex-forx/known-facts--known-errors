# Repolex Knowledge Graph of known-facts/known-errors

RDF knowledge graph data for [known-facts/known-errors](https://github.com/known-facts/known-errors), parsed by [repolex](https://repolex.ai).

> **Note**: This data is experimental and subject to change without notice.

## How to use this data

The easiest way to get started is to install the [lexq](https://github.com/repolex-ai/lexq) query tool using [uv](https://docs.astral.sh/uv/getting-started/installation/).

If you have uv installed, just copy/paste this into your terminal:

```bash
uv tool install git+https://github.com/repolex-ai/lexq
```

This installs lexq onto your system, in your user context. Verify the install:

```bash
lexq --help
```

**lexq is designed to be used primarily by LLMs in a terminal.** Start up your favorite LLM and ask it to use the lexq tool. It's that easy!

To load this repo's data:

```bash
lexq download known-facts/known-errors
```

This will automatically download essential data files from the last parsed commit. Consult `lexq --moreinfo` for other options, including downloading multiple commits, blobs, etc.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── f187984687f951a9e8f4a074d54db1ab94faede2
│   │       └── chunk-001.nq.gz
│   ├── lsp
│   │   └── f187984687f951a9e8f4a074d54db1ab94faede2.nq.gz
│   └── repolex
│       └── f187984687f951a9e8f4a074d54db1ab94faede2
│           └── chunk-001.nq.gz
├── blob
│   ├── 0c7e355102099d71016a3c8648c4d81966bb7274.nq.gz
│   ├── 1130c6579d89336ae07c20152bb03bec4ddaacac.nq.gz
│   ├── 13edb27f8341a15f7ef6805243c5be8572913129.nq.gz
│   ├── 17e51c385ea382d4f2ef124b7032c1604845622d.nq.gz
│   ├── 2601b3f4151f2ad62821425751ff1867283aa420.nq.gz
│   ├── 27a7ae530c86b3e00dc92c172405f9bdeb7ccbe8.nq.gz
│   ├── 280fb8d04170d32ee9c5f1537fb204382a2602ff.nq.gz
│   ├── 29447350638efccc242e3950c858384e2661c239.nq.gz
│   ├── 3e6eb476cd0eba17ed3a5e699eb7e423a9801daf.nq.gz
│   ├── 451f7bfc1e3c1a9eb3f31ed9c58ec3609128b904.nq.gz
│   ├── 48479ae1b7c6f54fc4d6dcadfbeafb10358dd9fb.nq.gz
│   ├── 75e3b65f99b29f48ab230e3eab3de8d0b7a9229f.nq.gz
│   ├── 9ae80cbbf5265b8198bc6f2aba56d10d44128271.nq.gz
│   ├── a718674ce58c2cb835775828c8a323d259c0848c.nq.gz
│   ├── abc54e787faaa90ec86a457375655c719137aaf3.nq.gz
│   ├── c7504b17b600cacd0a72d17b05bb8dae214c4791.nq.gz
│   ├── d2d774d685a805fac62723c16262a6ba9ded7549.nq.gz
│   ├── e3e57a8ce4ccbf74759a6df8fa4a3980ff1c9209.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   ├── e94d007030c7f349ab7a49bf213a046e494b7efe.nq.gz
│   └── efb98088164f5786b17e83ed384971fc3c74f93c.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── dep
│   └── f187984687f951a9e8f4a074d54db1ab94faede2.nq.gz
├── filetree
│   └── f187984687f951a9e8f4a074d54db1ab94faede2.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 29 files
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

## Source repository

[known-facts/known-errors](https://github.com/known-facts/known-errors)

---
*Parsed on 2026-04-22 by [repolex](https://repolex.ai)*
