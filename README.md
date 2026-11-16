# ⚠️ This Repository Has Been Archived

**This repository (`arko-sanyal-loci/loci-memory-engine-1`) is no longer maintained.**

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

**Superseded by canonical:**
- `loci-engine/loci_engine/` — The simplified LOCI engine here has been superseded by the
  full 28-module implementation in the canonical repo. The canonical repo's `heat.py`,
  `storage.py`, `store.py`, and `mcp_server.py` cover and extend everything this contained.

### For historical reference

`loci-engine/INDEX.md` contains the original module-by-module status table and design notes.
This remains readable for historical context.

---

*Canonical repo: https://github.com/arko-sanyal-loci/LOCI-MEMORY-ENGINE*
*Consolidated: November 2026 by Arko Sanyal (Billo Tech)*
