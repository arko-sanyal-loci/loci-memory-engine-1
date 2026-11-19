# [legacy] loci-memory-engine-1

**This repository (`arko-sanyal-loci/loci-memory-engine-1`) is [legacy] and no longer maintained.**

All development has been consolidated into the canonical Billo Tech repository:

## → [arko-sanyal-loci/LOCI-MEMORY-ENGINE](https://github.com/arko-sanyal-loci/LOCI-MEMORY-ENGINE)

---

### What this repo was

`loci-memory-engine-1` was an early LOCI product combining:
1. An Ollama-based RAG pipeline for local document ingestion and retrieval
2. An early/simplified LOCI memory engine (`loci-engine/loci_engine/`)

It was the first working prototype of CARD (Category-Adaptive Recall Depth) in a RAG context,
using sqlite-vec + FTS5 + Reciprocal Rank Fusion for hybrid search.

### What was ported to the canonical repo

**Fully ported (find it at `rag/` in the canonical repo):**
- `rag/card.py` — CARD query classification and ranking strategy
- `rag/chunker.py` — LangChain recursive text splitter
- `rag/embeddings.py` — Ollama embedding client
- `rag/llm.py` — Ollama generation client (compact + expand lanes)
- `rag/loader.py` — PDF / TXT / MD document loader
- `rag/pipeline.py` — End-to-end ingest + query pipeline
- `rag/cli.py` — `rag ingest` / `rag query` CLI
- `rag/config.py` — Environment-based configuration

**Ported 2026-11-19:** `loci-engine/loci_engine/vectors.py` (sqlite-vec + FTS5 hybrid chunk
store) now lives at `rag/vector_store.py` in the canonical repo. Before that, the canonical
`rag/pipeline.py` imported `loci_engine.vectors`, which only existed here, so the ported pipeline
could not run.

**Superseded by canonical:** the simplified engine in `loci-engine/loci_engine/` (`heat`, `store`,
`db`, `mcp_server`). Note the heat model here is different (exponential 0.95/day, tiers at
0.5 / 0.167) from the canonical hyperbolic model; the RAG chunk store keeps this one on purpose.

**Only in this repository (kept read-only for reference, not ported):**
- Design specs and plans: `docs/superpowers/specs/` (memory-engine design, RAG pipeline,
  Interaction Monitor) and `docs/superpowers/plans/` (memory core, heat rescale, versioning)
- Progress records `Sonnet-01.md` (signed, see `Sonnet-01.md.sig`) and `Sonnet-02.md`
- Research notes: `docs/dual-gpu-coding-intelligence-blueprint.md`,
  `docs/loci-card-adaptive-capacity-blueprint.md`, `docs/research/`, `docs/trading/`
- The Electron installer in `installer/`
- `usymprev` provenance code in `loci-engine/loci_engine/provenance.py`

### For historical reference

`loci-engine/INDEX.md` contains the original module-by-module status table and design notes.

---

*Canonical repo: https://github.com/arko-sanyal-loci/LOCI-MEMORY-ENGINE*
*Consolidated: November 2026 by Arko Sanyal (Billo Tech)*
