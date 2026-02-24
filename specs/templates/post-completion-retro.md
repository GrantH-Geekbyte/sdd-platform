# Post-Completion Retro Template (SDD v4.0 — Experimental)

After a spec reaches production, spend 2-3 minutes capturing what you learned.
This is separate from learning events (GAP/CATCH/INC) which capture *problems*.
This captures *insights* — things that went well, surprising findings, process observations.

## When to Use

- After every Standard+ spec reaches production
- Optional for Trivial specs (use if something interesting happened)
- Skip if nothing stands out — an empty retro is worse than no retro

## Template

Copy this into the spec file as a `## Post-Completion Retro` section at the bottom,
or add it to the spec's deployment checklist.

```markdown
## Post-Completion Retro

**Date:** YYYY-MM-DD
**Spec:** SPEC-NNN

### What went well?
- (1-3 bullets)

### What surprised you?
- (Anything unexpected — easier than expected, harder than expected, discovered something)

### What would you do differently?
- (Skip if nothing — not every spec has regrets)

### Process observation
- (Optional: Did the SDD pipeline help or hinder? Any friction worth noting?)
```

## Examples

### SPEC-021 (if retro had existed)
```
### What went well?
- Marketing-copywriter agent produced strong copy on first pass
- CEO Brief page template saved significant design time

### What surprised you?
- Human effort estimate was 10-14x — highest speedup for a Standard spec
- Test automation added 2-3 hours to human estimate that we initially missed

### What would you do differently?
- Create feature branch before implementation (documented as GAP-021-002)

### Process observation
- Effort estimation step needs test automation line item (now added to process)
```

## Where This Goes

Add to the spec file itself, after the Effort Comparison section. Keeps everything
about a spec in one place. The learning engine can scan these during monthly reviews.

## Ground Rules

- Honest > polished. Write what you actually think.
- Brief > thorough. 5 minutes max.
- Skip > force. If nothing comes to mind, skip it.
