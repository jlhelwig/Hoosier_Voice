---
title: "Claude called it a prosthetic. I called it a superpower."
draft: false
---

Claude hurt my feelings last week.

It wasn't intentional, and I took it well... maybe with a grim smile.

I noticed a pattern working with a new project. My todo list kept growing at an alarming rate. I had an idea and I architected it down to the last item... because I know when I pull a thread the whole pattern emerges. If I pull a thread and stop... the idea just dissipates, like fog. I never get it back.

I ended up with working code, but a todo list 45,000 tokens long - about the length of the novel Heart of Darkness. I was building what interested me right now, missing my goals, ending up with little things built unconnected to the rest of the code. I was spending 14 hour days going down rabbit hole after rabbit hole.

I even asked Claude about it. The honest answer, the architecture was good, but I was out of scope for MVP, Beta or SaaS. My todo was growing faster than I could get things done.

I did some googling, and executive function and time blindness were the main issues.

I had never thought about myself as having ADHD, this was a shock, so I asked my spouse. Who is a first grade teacher. "Do you think it's possible I have ADHD?"

After the two minute laughter was over. She said, "You want examples?"

That is when Claude hurt my feelings. I asked for a todo for a future article.

This came back.

ADHD + AI: offloading executive function to the model [LOW] (~3h) — How building Project with Claude exposed a new pattern: designing the AI environment to compensate for ADHD rather than fighting the deficit. Specific mechanisms: fatigue protection in CLAUDE.md (AI monitors externally because self-reporting is unreliable), temp_todo.md as externalised working memory, question mark convention to prevent impulsive coding, scope tagging as a project-level circuit breaker, and automation (refresh_reference.py, session-start hook) replacing habits that never stick. The deeper insight: AI isn't just a coding tool — it can be a cognitive prosthetic if you design the session instructions deliberately.

Yes, I was making a prosthetic... wow.

I chose to reframe this, I am making my ADHD a superpower.

A few CLAUDE.md changes, making a todo list by scope: MVP, Beta, SaaS, Improvements. Having a scope creep detector in CLAUDE.md.

I could pull every thread into the todo. The fog lifts, and a clear path is waiting for me, for when I am ready.

I thought about scope like a kid who wants to watch another hour of TV, but knows he should go to bed... but Mom, this is IMPORTANT! Claude didn't insist, just reminded me this is out of scope for this build.

Here's what's in CLAUDE.md for scope creep:

Scope discipline. Leanest solution first. Scope test fires before anything else on any new capability/command/tool/feature. Tag and flag non-MVP immediately: "This is [SaaS/IMPROVEMENT] — park in TODO, stay on MVP?" Implementation only after explicit user confirmation. Claude pre-tags its own proposals.

[MVP] — Test: "Can any customer use {product} at all without this?" No → MVP.
[SaaS] — Self-customer test: "Would we use this on {product}-on-{product} today?" Yes → SaaS. No → IMPROVEMENT.
[IMPROVEMENT] — Polish / Coverage / Support. Test: "Can we ship MVP and charge for SaaS without this?" Yes → park in TODO, do not build.

What did this do? I shipped MVP on time. My Beta is one day away from being ready early!

And the todo list? It's getting shorter, not longer.

This has never happened before on a project this big. The superpower works.
