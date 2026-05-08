---
name: Personal site project — canonical + syndicate model
description: Plan and decisions for Jeff's personal writing site at /Users/jeffreyhelwig/Articles
type: project
originSessionId: 72555d6e-9f71-4337-9d20-76f5a00dc523
---
Building a personal website to host AI/coding articles and serve as canonical home for syndication.

**Stack decision (2026-05-06):** Astro + Tailwind. Markdown content folder (`/articles/*.md`) with frontmatter. Email capture from day one (Buttondown or ConvertKit free tier). Hosting: AWS EC2 (Jeff has an existing instance, planned go-live evening of 2026-05-06). Earlier plan was Vercel — Jeff pivoted to EC2 to consolidate with infra he already pays for. Astro builds to static `dist/`, served via nginx or similar; deploys are rsync rather than `git push`.

**Domain:** `jeffhelwig.com` — confirmed owned (Squarespace) on 2026-05-06. This is the canonical site URL.

**Other domains Jeff owns (parked, not for the writing site):**
- `wieldor.com` (expires Jan 31, 2027) — candidate brand domain for his beta product. Surface search shows no direct conflict but a crowded "Wield-" namespace (Wield, Wielder, Wield VR, Wield AI, WieldMore, Wieldy). Before committing as product brand, run USPTO trademark search at tmsearch.uspto.gov filtered to product's class.
- `libraryofalexandria.co` (expires May 12, 2026) — open question whether to renew for optionality. Loaded metaphor, weak fit for current writing topics.
- `widgies.net` (expired April 15, 2026) — recommended to let lapse; wrong tonal fit for his audience.

**Distribution flow per article:**
1. Publish on personal site (canonical URL)
2. 24-48h later, mirror full text as a native LinkedIn Article (not a teaser+link post — see feedback_full_value_over_teasers.md)
3. Cross-post to Medium with `rel=canonical` pointing back to site
4. Optionally HN-submit pieces with sharp theses (currently candidates: "Tectonic Shift" and "Ideas are Important Now")

**Constraints:**
- Product is in beta — site must NOT link to product discovery page until Jeff explicitly says beta is done.
- Visual direction locked to docs-page aesthetic (see feedback_docs_aesthetic.md).

**Why:** Jeff wants impact for his writing on AI-assisted coding. His audience (engineers + C-level on LinkedIn, plus PMs/project-PMs broadly) is best reached via LinkedIn directly, with the personal site serving as durable canonical and email-capture surface. Owning the URL matters for long-term audience compounding.

**How to apply:** When scaffolding or editing the site, default to: minimal markdown-driven Astro setup, docs aesthetic, no link to product page yet, one prominent email-signup. When recommending what to publish where, default to the distribution flow above.
