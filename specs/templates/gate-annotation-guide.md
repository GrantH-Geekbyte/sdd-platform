# Gate Annotation Guide (SDD v4.0 — Experimental)

When approving or rejecting at a gate, briefly note **why** — not just the outcome.

## When to Annotate

- **Always:** When you override a recommendation (e.g., approve despite a concern)
- **Always:** When you make a judgment call between viable alternatives
- **Optional:** When the decision is straightforward and the spec already explains the "why"

## Format

One to three sentences added to the gate approval. No special format required.

### Spec Gate

**Ask yourself:**
- Are we solving the right problem, or just the obvious one?
- What did we deliberately leave out, and why?

**Good:** "Approved. Keeping this ungated despite marketing pressure — reach > leads at this stage."
**Good:** "Approved with scope reduction. Removed drip campaign — too much for v1, revisit after launch data."
**Minimal (fine for straightforward specs):** "Approved as written."

### Arch Gate

**Ask yourself:**
- What alternatives did we consider, and why did we pick this one?
- What's the riskiest assumption in this approach?

**Good:** "Approved. Chose ConvertKit direct POST over custom serverless because we don't need to transform the data. Saves a function and a failure mode."
**Good:** "Approved with caveat: vercel.json routes conflict risk flagged. Must verify production deploy triggers."

### QA Gate

**Ask yourself:**
- What are we *not* testing, and are we okay with that?
- If this breaks in production, how will we know?

**Good:** "Passed. 188/188 tests. Accepted 2 visual diff pixels on mobile — anti-aliasing, not a real change."
**Good:** "Passed with known gap: manual browser test deferred to staging. Automated coverage sufficient for merge."

### Deploy Gate

**Ask yourself:**
- What needs to happen after this goes live?
- Are we accepting any known gaps in this deploy?

**Good:** "Approved for production. Placeholder PDF is acceptable — Grant will replace before sharing the URL."
**Good:** "Deployed. Need to verify GA4 events are firing on production within 24 hours."

## Where Annotations Live

- Gate approvals in spec files (existing pattern)
- Architecture Checklists (existing pattern)
- QA Checklists (existing pattern)
- Deployment Checklists (existing pattern)

No new files needed. Annotations go where gate decisions are already recorded.

## Anti-Patterns

- Writing a paragraph when a sentence will do
- Annotating obvious decisions ("Approved because the spec meets all criteria")
- Creating a separate annotation document (just add it inline)
