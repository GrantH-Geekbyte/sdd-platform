# Production Escapes (INC-*)

**Definition:** Defects that reached production and impacted users.

**Naming Convention:** `INC-{SPEC_ID}-{sequence}-{short-description}.md`

**Examples:**
- `INC-019-002-formdata-json-bug.md` - Contact form broken in production for 12+ hours

## When to Create an Escape Event

Create an escape event when:
- A defect was deployed to production
- Users experienced the issue or could have experienced it
- The issue was not caught by staging, CI, or pre-production testing

## Why We Track These Separately

Production escapes represent **true process failures** where gates did not prevent user impact. These are high-priority learnings and the primary metric for evaluating SDD effectiveness.

**Key Questions:**
- Which gate should have caught this?
- Why didn't it?
- What process change prevents recurrence?

## Severity Classification

Every escape gets a severity tag. Report escape rate by severity — a flat count is misleading.

| Severity | Definition | Counts toward escape rate threshold? |
|----------|-----------|--------------------------------------|
| **Critical** | Data loss, security breach, site unusable | Yes |
| **High** | Core feature broken, key action blocked | Yes |
| **Medium** | Feature degraded, workaround exists | Yes |
| **Low** | Minor functional issue, edge case | No (track, don't alarm) |
| **Cosmetic** | Visual-only, no functional impact | No (track, don't alarm) |

**Actionable metric:** Escape rate (High+) — only Critical/High/Medium count toward the 5% alert threshold in `governance/pipeline-monitoring.md`.

## Related Categories

- [../catches/](../catches/) - Issues caught by staging/CI before user impact
- [../process-gaps/](../process-gaps/) - Process improvements not related to defects
