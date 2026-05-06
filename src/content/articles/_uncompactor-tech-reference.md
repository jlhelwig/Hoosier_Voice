---
note: AI-drafted reference material from Jeff's project Claude, not a Jeff draft. Voice is not Jeff's. NOT for direct publication. Pattern essay (#5a) references only the WHAT (showable scene: `forge -- <query>` recalls past conversation); this file holds the HOW for the engineer companion (#5b). Codename: "Forge" (decided 2026-05-06, replacing internal "Joplin"). Jeff will rewrite in his Hoosier voice when ready.
---

# Uncompactor — How it Works

## What it is
Per-project session memory for Claude Code. When `/compact` discards earlier conversation, the next session can retrieve specific moments from prior conversations on demand. Per-project — memories never leak between repos. Two halves: Squeezer (indexer) and Uncompactor (retriever).

## Where the data comes from
Claude Code already writes every conversation to `~/.claude/projects/<encoded-cwd>/<session-id>.jsonl`. The Uncompactor scavenges what's already there — no new recording.

## Half 1 — Squeezer (indexer)
- Runs as a LaunchAgent (`com.forge.squeezer`). Implementation: `forge_uncompactor/squeezer_sessions.py`.
- `_start_watcher()` watches `~/.claude/projects/` for new/modified `.jsonl` files. On change → `index_file()`.
- `parse_jsonl()` keeps user, assistant (text only), and ai-title records. Drops tool calls, thinking blocks, attachments, system messages.
- `extract_turn_pairs()` pairs sequential user/assistant records into coherent turns.
- `chunk_turn_pair()` splits each turn pair into overlapping chunks (max 4000 chars, 200-char overlap so a sentence cut by a boundary still appears intact in the next chunk).
- Project resolution: `_resolve_project_id()` reads the cwd from the JSONL record and walks upward looking for a `.forge_id` file. Falls back to `proj_<md5(cwd)[:12]>` if none. This scopes memories per project.
- Storage: per-project SQLite FTS5 (`~/.forge_uncompactor/{project_id}/sessions.db`) + ChromaDB (`~/.forge_uncompactor/{project_id}/chroma/`).
- Each session also gets a one-time LLM-generated summary (`_summarize_session()`) so a query that doesn't hit any chunk can still surface the right session by topic.

## Half 2 — Uncompactor (retriever)
FastAPI on port 8001 (`forge_uncompactor/uncompactor.py`). Endpoints: `POST /recall`, `GET /health`.

Retrieval algorithm at `recall()` line 259:

1. **Query expansion** — `_decompose_query()` hands the query to a background LLM (Ollama or Anthropic) that returns 5–8 specific technical terms plus 2–3 broader related concepts. Catches the case where the user remembers a concept ("the audit thing") but indexed turns used precise jargon ("hash-chained JOPR record").
2. **Two parallel searches** over the same chunk store:
   - `_fts_search()` — BM25 over SQLite FTS5, 50 candidates.
   - `_vector_search()` — ChromaDB embedding similarity, 50 candidates.
3. **Reciprocal Rank Fusion** — `_rrf_merge()` combines both ranked lists with the standard RRF formula `1/(k + rank)`. The clever bit: with `k=60`, a chunk at rank 1 in only one list scores ~0.016, while a chunk in both lists scores higher. The threshold `MIN_RRF_SCORE = 0.020` is set deliberately above the single-list-rank-1 ceiling, which forces consensus between keyword and vector. Keyword-only or vector-only hits are dropped.
4. **Vector distance gate** — anything with L2 distance > 1.5 is dropped as semantically distant.
5. **Rerank** survivors by vector distance, then RRF score.
6. **Context expansion** — `_expand_context()` pulls ±3 turns around each hit. The user gets the matching turn plus the conversation around it, not an isolated quote.
7. **Summary fallback** — if no chunks survive the gates, `_search_summaries()` does an FTS5 lookup over session summaries and returns those instead. Better to surface "you talked about this in session X on April 28" than nothing.
8. **Honest empty results** — if nothing hits at all, returns `{"found": false, "chunks": []}`. Never fabricates.

## How it gets called

**Path A — `forge -- <query>` trigger word.** User types `forge -- where did we discuss prompt caching` at the start of any prompt. Forge's Belt hook (`forge_hooks/prompt_hook.py:1565-1584`) sees the trigger, short-circuits all governance logic, calls `_session_recall()` (talks to SQLite FTS5 directly for speed — no HTTP roundtrip), formats matches as a context block, prepends to the prompt, exits. Claude sees the recalled exchanges as if they were always there.

**Path B — HTTP.** Any tool can `POST /recall { query, project_path, top_k }` to `http://127.0.0.1:8001` for the full hybrid-search pipeline.

## The interesting design choice
The default short-circuit path uses keyword-only FTS5 — fast, no embedding cost. The full hybrid pipeline (FTS + vector + RRF) lives behind the FastAPI endpoint for callers that want precision. **Two paths, same index, different cost/quality tradeoffs.** This is the line that engineers will quote.

The whole thing runs entirely local — SQLite, ChromaDB, optionally Ollama for query expansion — so prior conversations never leave the machine.
