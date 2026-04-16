# Repolex Knowledge Graph of PyCQA/autoflake

RDF knowledge graph data for [PyCQA/autoflake](https://github.com/PyCQA/autoflake), parsed by [repolex](https://repolex.ai).

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
lexq download PyCQA/autoflake
```

This will automatically download essential data files from the last parsed commit. Consult `lexq --moreinfo` for other options, including downloading multiple commits, blobs, etc.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 988e469555a54b0b16e39faf16ae84ff247fd337
│   │       └── chunk-001.nq.gz
│   ├── lsp
│   │   └── 988e469555a54b0b16e39faf16ae84ff247fd337.nq.gz
│   └── repolex
│       └── 988e469555a54b0b16e39faf16ae84ff247fd337
│           └── chunk-001.nq.gz
├── blob
│   ├── 0252f81d147ab249d01a438795c24ef05c70ac55.nq.gz
│   ├── 0b3d9400e150450b8220ccc5327080321ba1dc94.nq.gz
│   ├── 422897aed977b2a6d5b97156f3a85a10586ad4fc.nq.gz
│   ├── 5e704b4949d9f8869ff6b4877e0629112a9ef617.nq.gz
│   ├── 680f6b8f0e140987902111db0da912c038cac310.nq.gz
│   ├── 73e5153da57f82eed92bd46f00d7907c2a265355.nq.gz
│   ├── 8c7b09949f2b07beeeda1e201ef5e26bfa525ef9.nq.gz
│   ├── 915894de017de4edf50c069ee8ec34ceaefe483b.nq.gz
│   ├── 95a8153f9e10b39e0a3fb897b3370c1eddb9aaea.nq.gz
│   ├── 9abece23002eb81220fa3150ebe4a746bd5ccd82.nq.gz
│   ├── 9b80f4d014629b6fe930df912211b4ce3be476c6.nq.gz
│   ├── b5922b980a3138fe843bd0fdfd485df140d0c755.nq.gz
│   ├── eacb0d1d9e51129bdc4f4208582376ff108062a6.nq.gz
│   ├── f6f87a3ab2bff090801342868a4456654765d968.nq.gz
│   └── fcf28f1fbe5f8585aa6593a8e0b6581bb8961aaf.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── dep
│   └── 988e469555a54b0b16e39faf16ae84ff247fd337.nq.gz
├── filetree
│   └── 988e469555a54b0b16e39faf16ae84ff247fd337.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

15 directories, 25 files
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

[PyCQA/autoflake](https://github.com/PyCQA/autoflake)

---
*Parsed on 2026-04-16 by [repolex](https://repolex.ai)*
