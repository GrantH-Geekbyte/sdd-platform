# CLAUDE.md — SDD Platform

## Project Overview

SDD Platform is a product by GeekByte LLC that provides metrics dashboards,
documentation, and AI-powered advisory for teams using Spec-Driven Development (SDD).

**Owner:** Grant Howe, Managing Partner, GeekByte LLC
**Methodology:** Spec-Driven Development (SDD) v3.0 — Solo Operator Model
**Repository:** https://github.com/GrantH-Geekbyte/sdd-platform

## Current State

### Tech Stack
- **Framework:** Next.js (App Router)
- **Language:** TypeScript
- **Styling:** Tailwind CSS
- **Hosting:** Vercel
- **Database:** TBD (likely Vercel Postgres or Supabase)
- **Auth:** TBD (likely NextAuth.js or Clerk)
- **Payments:** TBD (Stripe when needed)

### Project Status: Greenfield
This project is brand new. No code exists yet beyond this CLAUDE.md and SDD governance files.

## Product Roadmap

### Phase 1: SDD Metrics Dashboard (MVP)
- Dashboard UI for visualizing SDD pipeline metrics
- Import/display velocity baselines, gate effectiveness, escape rates
- Charts and tables for spec throughput, speedup ratios, quality trends
- Static data initially (JSON/file-based), migrate to database later

### Phase 2: SDD Documentation & Help
- Interactive SDD methodology documentation
- Pipeline stage guides, gate checklists, complexity tier reference
- Searchable spec templates and examples
- Best practices from real SDD deployments (GeekByte's experience)

### Phase 3: AI Advisory Agent
- Conversational agent trained on Grant's SDD knowledge and methodology
- Answers questions about SDD implementation, pipeline optimization, gate tuning
- Draws from documentation, metrics patterns, and accumulated learnings

### Phase 4: Multi-Tenant & Subscriptions
- User accounts and authentication
- Organization/team workspaces
- Subscription billing (Stripe)
- Per-team metrics isolation and dashboards
- Gated access to premium content and AI agent

### Architectural Implications
- Phase 1 can use static data or API routes with file-based storage
- Phase 2 is content-heavy — could use MDX for documentation pages
- Phase 3 requires AI integration (Anthropic API), conversation storage, rate limiting
- Phase 4 adds auth, payments, multi-tenancy — Critical tier in SDD

## Development Methodology: SDD v3.0

### Pipeline
```
PM-Spec → Spec Gate → Architect-Review → Arch Gate → Implementer-Tester → QA Gate → Deployment → Deploy Gate → Production
```

### Conventions
- Spec IDs: `SPEC-NNN` (sequential, starting at 001)
- Checklists: `ARCH-SPEC-NNN`, `QA-SPEC-NNN`, `DEPLOY-SPEC-NNN`
- Branches: `spec/SPEC-NNN-short-description`
- Commits reference spec ID: `[SPEC-NNN] description`
- Non-spec fixes: `fix/short-description`, `docs/short-description`

### Complexity Tier Defaults
| Change Type | Default Tier |
|------------|-------------|
| Copy/content updates | Trivial |
| New static page/component | Standard |
| Styling/layout changes | Trivial or Standard |
| New interactive feature | Standard or Complex |
| Database schema changes | Standard or Complex |
| AI agent integration | Complex or Critical |
| Auth/user accounts | Critical |
| Payment/subscription | Critical |

### Gate Ownership (Solo Operator)
All gates owned by Grant with AI agent structured review.
Critical tier requires external second reviewer.

### SDD v4.0 Experimental: Preserving the Why
These additions are experimental. Evaluate after 10 specs.

**Decision Rationale:** Standard+ specs include a `## Decision Rationale` section.
**Gate Annotations:** When approving gates, note *why*.
**Post-Completion Retros:** After deployment, capture what went well/surprised you.
**`// WHY:` Comments:** Use `// WHY:` prefix for non-obvious code decisions.
**Stack Quirks:** Platform gotchas at `governance/stack-quirks.md`.

## Code Conventions

### TypeScript
- Strict mode enabled
- Prefer interfaces over types for object shapes
- Use `// WHY:` prefix for comments explaining non-obvious decisions

### React / Next.js
- App Router (not Pages Router)
- Server Components by default, Client Components only when needed
- Collocate components with their routes when route-specific

### CSS
- Tailwind CSS for styling
- Custom CSS only when Tailwind is insufficient
- Mobile-first responsive design

### General
- No `any` types — use proper typing or `unknown`
- Prefer named exports over default exports
- Keep components small and focused

## Security

### Current (Phase 1)
- No user data, no auth, no sessions
- Static dashboard — minimal attack surface
- HTTPS enforced via Vercel

### Future Requirements (Phase 3-4)
- Auth via established provider (not custom-built)
- Payments via Stripe (never handle card data directly)
- AI conversation data retention policy
- Rate limiting on API endpoints and AI agent
- PII encrypted at rest and in transit
- API keys never exposed client-side

## Related Projects
- **GeekByte Website** (`geekbyte-website`): Corporate site where SDD was first deployed.
  Contains real-world velocity baselines and learning events that inform this product.
