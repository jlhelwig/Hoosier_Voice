---
note: Scaffold for AI governance whitepaper. Audience: Chief Compliance Officer / General Counsel / Chief Risk Officer / Chief AI Officer / governance-scoped CISO at regulated orgs. NOT for direct publication. This file scaffolds only the executive summary + hook (the first ~600 words of a 4,000–6,000 word document). The full framework Jeff drafted is preserved at the bottom for reference. Voice: Hoosier-toned-down per saved memory rule (feedback_b2b_tone_down_vonnegut.md) — keep the bones, lose the deflection humor.
---

# AI Governance Whitepaper — Scaffold

Working title candidates (pick before drafting):
- "AI Governance Below the Model Layer"
- "The Three Questions Your Auditor Will Ask About AI-Generated Code"
- "The Control Surface Your GRC Stack Doesn't Reach"

## Open decisions before drafting

1. **Format:** gated PDF download (lead capture) / open web long-form / both. Default recommendation: **both**.
2. **Author byline:** Jeff Helwig personally / company-branded (Joplin/Forge). Default recommendation: **personal** — at this stage, your name is the trust signal, not your brand.
3. **Voice register:** pure GRC vocabulary / Hoosier-toned-down with GRC vocabulary where the audience needs it. Default recommendation: **yours, with their vocabulary** — reads as a person who knows GRC, not a vendor doc trying to sound like one.

---

## Page One — Above the Fold (~120 words target)

Purpose: the load-bearing surface of the entire document. Most C-level governance readers — except their lawyers in due diligence — will only read this page. The decision to "send this to my team" or "schedule a gap review" happens here. Title visible at top. Three questions visible without scrolling.

Beats:

1. **Title.** Working candidate: "AI Governance Below the Model Layer." Pick the title before this page is drafted — it shapes the first line.
2. **One-sentence setup.** "Your auditor will ask three questions about your AI-assisted code. In most organizations, no one can answer them with evidence."
3. **The three auditor questions, in italics, numbered:**
   1. *"What instructions was your AI assistant given when it wrote this code?"*
   2. *"Who approved those instructions, and when?"*
   3. *"What rules were applied to this commit, and what was the verdict?"*
4. **One paragraph naming the gap.** "The compliance obligation already exists. The control surface that produces the evidence does not."
5. **One paragraph naming the answer-by-reference.** "This paper walks through nine gaps in current AI governance posture and the controls that close each."
6. **Single-line CTA.** Whatever the call to action is — gap review, contact, schedule. One line, no fluff.

Voice cues: declarative throughout. No "honest pauses," no scene-setting. The page is a load-bearing surface, not a story. Every word earns its place. Read aloud test: under 45 seconds.

---

## Page Two — Why This Paper Exists (~400-600 words target)

Purpose: for the reader who continues past page one — typically the buyer's compliance team, governance lawyer, or champion's direct reports preparing the procurement memo. Anchor the document in current regulation. Frame the depth that follows.

Beats:

1. **The auditor will not accept "we don't know."** A single line silently removed from the AI's instruction file changes what the AI is willing to write. Until something ships and someone asks where it came from. By then, "we don't know" is not an answer the regulator accepts.
2. **This is not speculative future risk.** Current regulations already require evidence of AI controls when AI is in the loop. Specific list with article references:
   - GDPR Article 22 (automated decision-making)
   - EU AI Act Articles 9 / 13 / 15 (risk management, transparency, accuracy)
   - NIST AI RMF — Govern function
   - NY DFS 23 NYCRR 500 §500.16 (incident response, governance)
   - HIPAA §164.312 (audit controls)
   - SOC 2 CC7 (system operations, change management)
   - FDA 21 CFR Part 11 (electronic records, signatures)
3. **The control gap, named.** Existing GRC stacks don't reach the AI instruction file. Existing change-management applies to code commits, not to the file the AI actually reads. Privacy review applies to architecture, not to AI conventions. Compliance reviews the policy PDF, not the constitution that governs the AI's output.
4. **What this paper covers.** Nine gaps in AI governance posture. Each anchored in regulation that already applies. Each closed by a specific control mechanism. Each producing a concrete evidence artifact a regulator can accept.
5. **What this paper does not cover.** Architecture choices that affect compliance independently (data residency, encryption-at-rest). Human review on security-critical paths. Cultural or training interventions. These are real and important; they live outside the scope of an AI instruction-layer governance paper.

Voice cues: declarative, sourced. Each regulatory citation can be footnoted with the article reference for the buyer's lawyer. The "what this paper does not cover" note is an honest-limitations move that earns trust before the depth begins.

---

## Open content questions for these 600 words

1. Confirm the working title before the exec summary lands — title shapes the exec summary's first sentence.
2. Decide whether to introduce the product name in the exec summary or hold it for Section 4 / Section 5 (recommend: hold, let the gap be felt before the answer arrives).
3. Confirm "the three auditor questions" wording verbatim — these become the document's spine; they will be quoted across articles, social, and sales conversations.

---

## Reference — full framework (Jeff's original outline, preserved verbatim)

[The 9-section framework Jeff drafted lives below. Use as the source of truth for sections 1–9 when we move past the hook+exec-summary unit. Voice in the reference is product-Claude-shaped, not Jeff-shaped — translate to Jeff's voice when drafting actual sections.]

### Audience
Chief Compliance Officer / General Counsel / Chief Risk Officer / Chief AI Officer / governance-scoped CISO at a regulated org.

### Tone vocabulary
control, evidence, auditability, defensibility, attestation, chain of custody, named authority, segregation of duties.

NOT: AI safety, prompt engineering, fine-tuning.

### Three auditor questions (the spine)
1. "What instructions was your AI assistant given when it wrote this code?"
2. "Who approved those instructions, and when?"
3. "What rules were applied to this commit, and what was the verdict?"

### Regulatory anchors (already in force)
- GDPR Article 22 (automated decision-making)
- EU AI Act Articles 9 / 13 / 15 (risk management, transparency, accuracy)
- NIST AI RMF — Govern function
- NY DFS 23 NYCRR 500 §500.16 (incident response, governance)
- HIPAA §164.312 (audit controls)
- SOC 2 CC7 (system operations, change management)
- FDA 21 CFR Part 11 (electronic records, signatures)

### Section 1 — "What were the AI's instructions, and who approved them?"
- Control gap: every coding AI runs on a written instruction file (CLAUDE.md, .cursorrules, .github/copilot-instructions.md). Untracked, unapproved, unreviewed in most orgs.
- Joplin's answer: governed instruction injection (Jiminy) — marker-delimited stanza, version-controlled, tamper-detected, Scribe-approved updates.
- Evidence the regulator gets: exact instruction set, approver name, timestamp, governance posture at the time of generation.

### Section 2 — "What did the AI produce, and was it allowed to?"
- Control gap: AI-assisted commits ship without per-decision compliance evaluation. Post-hoc code review is too late and not evidentiary.
- Joplin's answer: synchronous prompt-level evaluation (Belt) — tiered rule check before the AI's output reaches the developer's editor. Tier 0 (provider AUP) and Tier 1 (Constitution) hard-block. Tier 2/3 advisory + ticketed.
- Evidence: every AI-assisted change carries a JOPR record — verdict, tier, rules applied, author, machine, branch, prompt hash, output hash.

### Section 3 — "Prove it. Show me a regulator-ready package."
- Control gap: most "AI governance" tools produce dashboards, not evidence packages.
- Joplin's answer: per-framework compliance reports — 50+ builders (HIPAA, EU AI Act, NIST AI RMF, SOC 2 Type II, FDA 21 CFR Part 11, GDPR, PCI DSS, NY DFS, DORA, ISO 42001, FedRAMP, CMMC, etc.).
- Evidence integrity: hash-chained audit log — every record links to the previous; tamper is cryptographically detectable, not merely discouraged.
- Defensibility: structured, dated, signed, reproducible — not screenshots, not narrative.

### Section 4 — "Who has authority to change a rule?"
- Control gap: rules live in policy PDFs and Confluence pages. They drift. No enforcement, no record of changes, no segregation of duties.
- Joplin's answer: Scribe — every amendment is a routed ticket to a named authority. Tier 0 (provider AUP) is read-only; Tier 1 (Constitution) requires CIO/CISO sign-off; Tier 2/3 routed by domain.
- Evidence: amendment chain traces from current rule back to originating ticket, approver, and the JOPR record that triggered the change.

### Section 5 — "Does this still work when my AI provider releases a new model?"
- Control gap: most AI controls couple to one model or provider. When the model changes, controls drift silently.
- Joplin's answer: provider-agnostic — local Ollama, Anthropic, Gemini swappable; Tier 0 always local. Beat Cop is the org's own classifier trained on the org's own audit log — model-version-independent.
- Strategic angle: institutional governance knowledge accumulates in your data, not the vendor's. (Push back to Jeff: this is the THESIS of the section, not a takeaway. Lead with vendor-lock-in as a governance risk.)

### Section 6 — "Can my data stay inside the building?"
- Control gap: cloud AI governance services route prompts and code through their infrastructure. Many regulated orgs cannot legally use them.
- Joplin's answer: full air-gapped mode — local Ollama path, audit log on-prem, compliance reports generated locally.
- Evidence: code never leaves the network; evidence chain runs on hardware the org controls; no third-party log custody.

### Section 7 — "Can engineering route around it?"
- Control gap: shadow AI on every laptop. Copilot/Cursor/Claude Code installed individually with no central enforcement.
- Joplin's answer: commit-layer enforcement — pre-commit hook + Belt synchronous block, deployable org-wide via MDM / .gitconfig template / CI pipeline. Independent of which assistant produced the code.
- Bypass posture: --no-verify is a Tier 1 violation; the governed stanza tells the AI itself to refuse to help bypass; pre-commit hook can be CI-mirrored so local skip still fails the build.

### Section 8 — "What's my exposure if I don't?"
Penalty scales (cite real numbers, not vague "fines"):
- GDPR — up to 4% of global annual revenue
- EU AI Act — up to €35M or 7% of global revenue
- HIPAA — up to $2.1M per violation category per year
- NY DFS 23 NYCRR 500 — individual officer liability
- FDA 21 CFR Part 11 — warning letter, consent decree, product hold
- SOX — personal CFO/CEO certification at risk

Frame: a single failed audit costs more than a year of org-wide AI governance tooling.

### Section 9 — One-sentence frame for the close
"You already have the policy. Joplin is the control that makes the policy enforceable at the moment AI writes code, with the evidence to prove it."

### Sections to add (Claude pushbacks)
- **Honest limitations.** What this DOESN'T solve. Two paragraphs, callout box. Specific items: doesn't replace human review on security-critical paths; doesn't catch architecture-level compliance (data residency, encryption-at-rest); effectiveness depends on rule quality; requires up-front rule-setting work, not turnkey day one.
- **What good looks like.** The positive pair to the penalty section. Faster audit attestation, board-reportable control posture, evidence package on-demand, defensibility in incident response. Without this, the whitepaper is fear-only and governance buyers smell that.

### What to leave out
- Architecture details (BM25, FAISS, ChromaDB, FastAPI ports)
- Code examples
- Internal naming as primary terms — introduce Belt / Scribe / Jiminy / Beat Cop once and use functional descriptions thereafter
- Pricing — that's a sales conversation, not a positioning piece
