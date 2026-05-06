---
title: "I stopped spending my AI time and started investing it"
draft: true
---

[Seed for piece #5, 2026-05-06. Spine: spending vs. investing your AI time. Audience priority: PMs, then builders-afraid-to-step-up, then engineers as bonus.]

## Captured anecdotes (raw material — not drafted prose)

### The YouTuber / uncompactor inversion (likely cold open)

A YouTuber was glowing about a GitHub feature that summarizes Claude conversations before compaction. Jeff had already built the opposite — an uncompactor that recovers the original conversation when context is needed back, because he was tired of repeating himself after every compact. The YouTuber was spending (downloading a tool someone else built). Jeff was investing (built the tool that compounds his future sessions). Same problem, two opposite responses, two different relationships to AI tooling.

This is the article's thesis in 30 seconds. Likely lede.

## Resolved facts (2026-05-06)

- **The tool the YouTuber promoted: Claude Mem.** YouTube Short link Jeff sent: https://youtube.com/shorts/0csuHVNgRnU. Title: "Claude Mem breakthrough in AI coding memory." Channel name didn't surface through scrape; nice-to-have, not load-bearing.
- **The Uncompactor shape:** real engineering — LaunchAgent indexer + FastAPI retriever + hybrid SQLite FTS5 / ChromaDB / RRF pipeline. See _uncompactor-tech-reference.md. Article uses only the WHAT (`forge -- <query>` recalls past conversation), not the HOW.

## Scaffold — rough beats, 2026-05-06

Beat-by-beat outline. Voice work belongs to Jeff — these are the structural moves and what each beat needs to do, not prose to keep. Estimated length: 700-1100 words. Medium-shaped.

### Beat 1 — Cold open: the inversion (Vonnegut deadpan)
- Scene: scrolling YouTube. A creator is glowing about a tool you can download from GitHub that summarizes Claude conversations before context compaction.
- Cut: Jeff already built the opposite. Calls it an uncompactor. Recovers the original conversation when context is needed back, because he was tired of repeating himself after every compact.
- Land: same problem, two opposite responses. Two different relationships to the tooling.
- Voice cue: Open flat ("I was watching a YouTube video the other day..."), undercut at the end ("...and I realized I'd built the inverse"). No drama on the realization.
- ~150-250 words.

### Beat 2 — The pattern, named
- That moment crystallized something Jeff had been doing without a name for it.
- Most Claude time was the first kind (ask it to do work).
- The time that compounded was the second kind (ask it to help build something that made future Claude sessions faster).
- The first kind was a transaction. The second was an investment.
- ~100-150 words. Drop the financial frame here without explaining it.

### Beat 3 — The compounding mechanism
- Why the second kind compounds. Each tool you build doesn't just solve today — it shapes how you use AI tomorrow. Tomorrow's use shapes the next tool.
- Real compounding, not metaphor.
- Concrete example needed: a CLAUDE.md tweak (or hook, or script) that paid off across every later session. [OPEN: Jeff to provide specific example.]
- ~150-200 words.

### Beat 4 — The bar is your orientation, not your implementation
- Most important beat for the hesitant-builder audience. Lowers the bar.
- Investing doesn't mean "build hybrid-search RRF systems."
- Three concrete shapes, laddering up:
  1. **temp_todo.md** — externalized memory with one-word navigation. A scratch file. Reader can build it in 30 seconds and feel compounding within a week. Concrete, immediately copyable, viscerally relatable.
  2. **"Ask before coding"** — one rule line in CLAUDE.md. Pure mindset, no tooling. Lowest possible bar.
  3. **Tool Suggestion table** — Claude proactively pointing at the tools you've already built. Counter-intuitive payoff line: "you have to TELL the AI your tools exist?" — most readers haven't realized this.
- The three together: file → rule → table. None require advanced engineering. Reader sees themselves in at least one.
- The bar: did you spend the session BUILDING something that compounds, or just SPENDING the session on a task?
- ~200 words.

### Beat 5 — The diverging leverage gap
- Two builders sitting next to each other for a year.
- One spent every session on tasks. The other spent some sessions on investments.
- A year later, their AI-leverage has diverged.
- One has a custom CLAUDE.md, a few scripts, some hooks, maybe their own Uncompactor. The other has the same Claude they had a year ago.
- Possibly the strongest beat for engineering-leadership readers riding along.
- ~150-200 words.

### Beat 6 — Closer (Vonnegut flat)
- Bring it back to the YouTuber.
- The YouTuber wasn't wrong — that summarizer is probably useful for somebody.
- But the gap between downloading it and building the inverse is the gap that matters.
- Most people will never notice they're on one side of it.
- ~80-150 words.

## Open questions before drafting

1. ~~YouTuber name~~ — partially resolved (tool: Claude Mem; channel handle still missing, low priority).
2. ~~Low-rung investing example~~ — resolved (see Beat 4 picks above).
3. ~~Forge in the piece~~ — RESOLVED 2026-05-06: keep generic ("the product"). Article is about the pattern, not the product.

## Reserve material — candidates not used in #5a (saved for future articles or revisits)

- **Pre-run review with a separate agent** — same model can't honestly review its own output; spawn a fresh one. Too advanced for #5a's hesitant-builder bar. **Best home: #5b (Uncompactor / engineer companion)** or its own piece. The "same-model-can't-review-itself" insight is HN-shaped on its own.
- **Fatigue protection** — already earmarked for #2 (Project Manager piece) via the stash at _stash-fatigue-and-quality-block.md. Don't double-use here.

