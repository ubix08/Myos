# AI-OS Operator Constraints & Principles

## Summary
AI-OS is built on a set of hard constraints and design principles that guide every architectural and product decision, ensuring the system remains operable by a solo operator while delivering value to clients.

## Definition
The AI-OS Operator Constraints & Principles are non-negotiable rules and guiding philosophies that shape the system's development, ensuring it remains buildable, maintainable, and valuable for a solo operator while avoiding common pitfalls that lead to over-engineering or missed market opportunities.

## Key Ideas
### Hard Constraints (Non-Negotiable)
1. **Solo operator** — Every system must be maintainable by one person
2. **Zero managed infrastructure** — No self-hosted servers; Supabase + Vercel only
3. **One codebase** — All verticals run from the same repo; divergence via config only
4. **Termux-compatible development** — CLI tools must run on Android arm64 (Node.js)
5. **Client data isolation** — One Supabase project per client; no shared database
6. **No vendor lock-in on AI** — Provider is swappable via env var; never hardcode OpenAI

### Design Principles
1. **Config over code** — New vertical = new JSON file, not new codebase
2. **Modules are additive** — Adding a module never breaks existing data or UI
3. **AI degrades gracefully** — Every feature works without AI enabled
4. **Client owns their data** — Full JSON export available at any time, no lock-in
5. **Setup time ≤ 5 days** — If a new vertical takes longer, the config system needs improvement
6. **Revenue first** — No feature gets built that doesn't serve a paying or near-paying client

### When to Say No
- Do not build generic features — every feature must map to a specific vertical need
- Do not add a module unless at least 2 potential clients have asked for it
- Do not optimize for scale before 20 clients — premature scaling is wasted time
- Do not build multi-tenancy (shared DB) until per-project ops become a real bottleneck

## Evidence and Findings
From AI-OS-Master-Spec-v2.md Section 18 (Operator Constraints & Principles):
- Detailed listing of 6 hard constraints with explanations
- 6 design principles that guide development decisions
- 4 specific scenarios where development should be avoided ("When to Say No")
- Clear rationale for each constraint and principle based on solo operator realities

## Areas of Agreement
- All sources confirm the solo operator focus as foundational
- Consensus on the zero managed infrastructure approach (Supabase + Vercel only)
- Agreement on the one codebase principle with config-driven divergence
- Shared understanding of the revenue-first mindset for feature prioritization

## Areas of Disagreement
| Topic | Source Positions | Possible Explanation |
|-------|------------------|----------------------|
| Specific constraints | Some sections emphasize different constraints | Evolution of thinking as challenges were encountered |
| Timeline for setup | Variations on what constitutes acceptable setup time | Different vertical complexities affecting estimates |
| Module addition criteria | Different thresholds for when to add modules | Learning from actual client requests over time |

## Related Concepts
- [[ai-os-overview]]
- [[ai-os-business-model]]
- [[ai-os-tech-stack]]
- [[ai-os-deployment-workflow]]
- [[ai-os-vertical-config]]
- [[ai-os-module-system]]
- [[ai-os-roadmap]]

## References
- AI-OS-Master-Spec-v2.md (Section 18: Operator Constraints & Principles)