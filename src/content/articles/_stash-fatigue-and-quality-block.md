---
note: Stashed from the ADHD draft on 2026-05-06. Earmarked for the Project Manager piece (or its own article — "I told my AI to babysit me when I'm tired"). Not for publication as-is.
---

## Prose context (was line 32 of ADHD draft)

> Also a fatigue detector... my decisions were getting sloppy after 8 hours. I had it detect drift, bad choices (with a pushback) and spelling and grammar check.

## Prose aside (was line 56 of ADHD draft)

> Yes, token heavy, but it could be reduced by asking claude to reduce the tokens and keep the meaning. I did this once, but needed the full compliment of meaning for capture.

## CLAUDE.md block (was lines 48-55 of ADHD draft)

For Fatigue detection in Claude.md I have:

Fatigue protection. User has ADHD; Claude monitors externally. Overrides Scope discipline and Circuit breaker.

Signals (any one): explicit words ("tired", "exhausted", "sigh", "my head hurts"); rising typos; run-on/missing punctuation; terse delegation ("your choice", "whatever"); session > 2h.
On trigger: (1) name it; (2) offer (a) break 15+ min, (b) capture-only (→ [DRAFT-FATIGUE] TODO, no architecture locked), (c) explicit override (flagged for next-session review); (3) stop proposing design until user picks. Circuit breaker same turn → one merged prompt.
Post-fatigue: flag every architecture decision "[Post-fatigue — park or lock in now?]" Pre-run review adds "Fatigue active — higher-risk." Fire ONCE per signal; break resets. On return: "Back fresh?"
