---
title: "The AI on Your Team Was Told to Do Something. Do You Know What?"
draft: true
note: AI-drafted reference material from Jeff's project Claude, not a Jeff draft. Voice is not Jeff's. Jiminy as described here may not match what Jeff actually intends to build. Jeff will rewrite in his Hoosier voice — when that arrives, run the 3-pass against the rewrite, not this content.
---

Every modern AI coding assistant runs on a written instruction file. Claude Code reads CLAUDE.md. Cursor reads .cursorrules. Copilot reads .github/copilot-instructions.md. Aider, Windsurf, Continue — all of them. The shape varies. The role does not. That file is the AI's constitution. It tells the assistant what conventions to follow, what to refuse, what kind of code is unwelcome here.

Now ask three questions about that file in your own project:

Who wrote it?
Who approved the last change?
When was it last reviewed against your security policy?

Most teams cannot answer any of the three. The file was written by whichever engineer was most excited the week the tool landed. It has been edited a handful of times. The compliance officer has never seen it. The CISO does not know it exists. If somebody quietly removes the line that says "never write code that touches customer PII without a privacy review," the AI will not notice and will start writing code that touches customer PII without a privacy review. Neither will the rest of the team, until something ships.

This is the gap Jiminy closes — and it is not a Joplin gap. It is a gap in every project that has an AI coding assistant and any rules at all about how the codebase should be written.

## What Jiminy is

A thin governance layer that wraps whatever instruction file your AI uses. Three things, in order of how much they matter:

A governed install. Jiminy writes a short, marker-delimited block into your instruction file. The markers (<!-- JIMINY:BEGIN --> … <!-- JIMINY:END -->) define the governed region. Everything outside them stays exactly as the team wrote it. Re-running install is idempotent — the block updates in place, no duplication, no clobbering. Inside the block: the rules your team actually agreed on, signed off through whatever approval workflow you already use. Not five generic AI safety lines from a vendor — your rules.

Nightly tamper detection. A scheduled job extracts the block, normalizes it, and compares against a stored snapshot. Lines silently removed: flagged. Markers deleted to disable governance entirely: flagged. Block wrapped in HTML comments as a deactivation trick: flagged. Each flag fires an alert through whatever channel your team uses (email, Slack, Teams, webhook) with copy-paste-ready restore content.

Audited updates. When a rule changes, the change goes through an approval workflow before the instruction file is touched. The instruction file is then as version-controlled and as auditable as any other governance artifact. The question "what was the AI told, and who told it?" gets a specific answer with a timestamp and an approver name.

## Why this works on any project

Jiminy doesn't care what's in your block. It cares that the block exists, is approved, stays intact, and has a paper trail. A startup with one engineer and a .cursorrules file that says "prefer functional style, never any in TypeScript" benefits from Jiminy in exactly the same way a Fortune 500 with a 200-line HIPAA compliance block benefits. The shape of the rules is yours. The shape of the governance is universal.

If you've never opened your team's instruction file and asked "who approved this, and when?" — today would be a good day.
