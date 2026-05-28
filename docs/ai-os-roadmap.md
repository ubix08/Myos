# AI-OS Roadmap

## Summary
AI-OS follows a four-phase roadmap designed to build sustainable revenue, validate the business model, expand to multiple verticals, and eventually productize the solution for broader distribution.

## Definition
The AI-OS Roadmap is a structured, phased approach to business growth that balances product development with revenue generation, starting with a single paying client and evolving toward a self-hosted license business model.

## Key Ideas
### Phase 1 — Foundation (Weeks 1-6)
**Goal**: One working vertical deployed to one real client.
- Core engine: layout, routing, auth, Supabase client
- Vertical config system (load from JSON → apply theme + modules)
- Dashboard module with widgets
- Tasks module (list + kanban + detail)
- Notes module (Tiptap editor)
- Contacts module
- Supabase schema (core tables)
- Basic AI chat (Edge Function → OpenAI)
- `ai-os-cli` — basic `new` command
- Deploy `freelance-consultant` vertical for 1 pilot client

**Milestone**: First paying client live. First retainer payment received.

### Phase 2 — Revenue Modules (Weeks 7-12)
**Goal**: 3 active clients, $2,000+ MRR.
- Invoices module with PDF generation
- Time Tracking module
- Export engine (PDF + CSV + JSON)
- AI-powered invoice generation from project data
- Command palette with AI integration
- Semantic search (pgvector embeddings)
- `independent-accountant` vertical config
- Mobile-responsive layout polish

**Milestone**: 3 clients × ($99 retainer + $1,200 setup amortized).

### Phase 3 — Vertical Expansion (Months 4-6)
**Goal**: 8-10 active clients, $4,000+ MRR, 3 vertical configs.
- Document Vault module
- Calendar module
- Finance Tracker module
- `local-clinic` and `solo-founder` vertical configs
- `ai-os-cli` add-module command
- Client self-service settings (limited — branding, AI persona name)
- Onboarding flow per vertical
- Admin panel (your view of all active deployments)

**Milestone**: Monthly income from retainers covers personal operating costs.

### Phase 4 — Productization (Month 7+)
**Goal**: 20 retainer clients, begin self-hosted license sales.
- Documentation site for self-hosted buyers
- Self-hosted license checkout (Gumroad or Lemon Squeezy)
- Team module (multi-user workspace)
- Content Planner module
- Inventory module (for retail vertical)
- Multi-agent AI workflows (Pro tier)
- Agency white-label toolkit

**Milestone**: 20 retainer clients, begin self-hosted license sales.

## Evidence and Findings
From AI-OS-Master-Spec-v2.md Section 17 (Roadmap):
- Detailed four-phase breakdown with specific goals, features, and milestones for each phase
- Clear progression from foundation work to revenue generation to expansion and productization
- Specific module development timelines aligned with revenue goals
- Explicit milestones tied to business outcomes (first paying client, MRR targets, operating cost coverage)

## Areas of Agreement
- All sources confirm the four-phase structure
- Consensus on the logical progression from core engine to revenue modules to expansion
- Agreement that milestones are tied to business outcomes rather than just feature completion
- Shared understanding that productization comes after validating the service model

## Areas of Disagreement
| Topic | Source Positions | Possible Explanation |
|-------|------------------|----------------------|
| Timeline specifics | Some sections suggest different week/month allocations | Evolution of planning as more was learned |
| Module priorities | Variations in which modules are considered most critical | Different vertical needs influencing priorities |
| Self-hosted license timing | Some suggest earlier availability | Evolution of thinking as product stabilizes |

## Related Concepts
- [[ai-os-overview]]
- [[ai-os-business-model]]
- [[ai-os-deployment-workflow]]
- [[ai-os-module-system]]
- [[ai-os-vertical-config]]
- [[ai-os-pricing-revenue]]
- [[ai-os-operator-principles]]

## References
- AI-OS-Master-Spec-v2.md (Section 17: Roadmap)