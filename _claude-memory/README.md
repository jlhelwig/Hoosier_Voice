# Claude auto-memory snapshot

This folder is a **snapshot** of Jeff's Claude Code auto-memory for this project, captured for cross-machine sync.

## What's here

Eight files that build up Claude's understanding of Jeff's voice, audience, project state, and feedback rules:

- `MEMORY.md` — index file Claude loads at session start
- `user_profile.md` — Jeff's role, audience, collaboration preferences
- `feedback_no_ai_slop.md` — voice rule (Vonnegut/Hoosier, anti-AI-slop)
- `feedback_b2b_tone_down_vonnegut.md` — when to dial back the voice for B2B audiences
- `feedback_docs_aesthetic.md` — visual/aesthetic preferences
- `feedback_full_value_over_teasers.md` — no-teaser-posts rule for LinkedIn
- `project_articles_in_flight.md` — active article pipeline state
- `project_personal_site.md` — site stack, hosting, distribution model

## To restore on a new machine

These files belong at `~/.claude/projects/-Users-jeffreyhelwig-Articles/memory/` (Claude Code derives this path from the project's absolute path — `/Users/jeffreyhelwig/Articles` becomes `-Users-jeffreyhelwig-Articles`).

After cloning this repo on the other machine:

```bash
mkdir -p ~/.claude/projects/-Users-jeffreyhelwig-Articles/memory/
cp _claude-memory/*.md ~/.claude/projects/-Users-jeffreyhelwig-Articles/memory/
```

If the project lives at a different absolute path on the other machine, replace `-Users-jeffreyhelwig-Articles` with the path-encoded form of wherever the project actually lives.

## Caveat

This is a **snapshot, not a live sync.** Updates Claude makes to memory on either machine are local-only until snapshot is refreshed via:

```bash
cp ~/.claude/projects/-Users-jeffreyhelwig-Articles/memory/*.md _claude-memory/
git add _claude-memory/ && git commit -m "Refresh memory snapshot" && git push
```

For continuous sync, a longer-term option is to symlink `~/.claude/projects/-Users-jeffreyhelwig-Articles/memory/` to an iCloud Drive folder on both machines. Skipped here because Jeff wanted the simpler snapshot path first.
