# AI-OS Deployment Workflow

## Summary
AI-OS uses the `ai-os-cli` tool to automate client deployment, handling Supabase project creation, migrations, Vercel setup, and environment configuration through a standardized, repeatable process.

## Definition
The AI-OS Deployment Workflow is a semi-automated process powered by a custom Node.js CLI (`ai-os-cli`) that orchestrates the creation of isolated client infrastructure, code deployment, and configuration, enabling a solo operator to set up new client workspaces efficiently and consistently.

## Key Ideas
### The `ai-os-cli` Tool
A lightweight Node.js CLI that performs the following steps for new client deployment:
1. Creates new Supabase project via Supabase Management API
2. Runs core + module-specific migrations
3. Seeds with vertical config
4. Creates new Vercel project linked to GitHub repo
5. Sets all required environment variables in Vercel
6. Triggers first deployment
7. Outputs: workspace URL + Supabase dashboard link + credentials file

### Environment Variables Per Deployment
Each client deployment gets unique environment variables:
**Vercel project env vars (set by cli):**
- `VITE_SUPABASE_URL` - Supabase project URL
- `VITE_SUPABASE_ANON_KEY` - Supabase anonymous key
- `VITE_VERTICAL_CONFIG` - Vertical identifier (e.g., "freelance-consultant")
- `VITE_PRODUCT_NAME` - Product name (e.g., "ConsultOS")

**Supabase Edge Function secrets (never in Vercel):**
- `OPENAI_API_KEY` - Client's own key or operator's during trial
- `AI_PROVIDER` - AI provider selection (openai/anthropic/groq)
- `AI_MODEL` - Specific model to use
- `MONTHLY_BUDGET_USD` - Hard cap for AI usage

### Step-by-Step Deployment Process (New Client)
**Day 1: Discovery**
- 30-min call with client
- Identify vertical + required modules
- Confirm domain, branding assets, AI provider preference
- Collect: logo, colors, any existing data to import

**Day 2: Setup**
- Run: `ai-os new --vertical [id] --client [name] --domain [domain]`
- Customize vertical config JSON for this client
- Configure AI persona name + domain context paragraph
- Set up DNS for custom domain in Vercel

**Day 3-4: Configuration**
- Configure module settings (invoice numbering, tax rates, etc.)
- Import existing data (contacts CSV, etc.)
- Customize PDF templates with their branding
- Test all modules end-to-end

**Day 5: Handover**
- Create client's owner account
- Record 15-min walkthrough video
- Send handover doc (what each module does, how to use AI)
- Sign off → monthly retainer begins

### Ongoing Maintenance Workflow
- **Core bug fix**: Push to main branch → Vercel auto-deploys all projects
- **Vertical-specific updates**: Use feature flags in config
- **Add new module**: `ai-os add-module --client [name] --module [module-name]`
  → Runs migration on Supabase project
  → Updates vertical config to enable module
  → Triggers Vercel redeploy

## Evidence and Findings
From AI-OS-Master-Spec-v2.md Section 13 (Deployment Workflow):
- Detailed description of the `ai-os-cli` tool and its 7-step process
- Clear separation of Vercel environment variables vs Supabase Edge Function secrets
- Day-by-day breakdown of the 5-day client onboarding process
- Ongoing maintenance workflow showing how updates propagate to all clients
- Specific CLI commands for setup (`ai-os new`) and module addition (`ai-os add-module`)

## Areas of Agreement
- All sources confirm the CLI-driven deployment approach
- Consensus on the separation of frontend (Vercel) env vars vs backend (Edge Function) secrets
- Agreement on the 5-day deployment timeline structure
- Shared understanding that code updates deploy to all clients automatically via Vercel

## Areas of Disagreement
| Topic | Source Positions | Possible Explanation |
|-------|------------------|----------------------|
| Specific CLI flags | Some sections show slightly different command syntax | Evolution of the CLI tool during development |
| Day allocation | Variations in how many days for setup vs configuration | Different project complexities affecting timeline |
| DNS setup | Some sections mention automatic DNS, others manual | Depending on domain provider and Vercel configuration |

## Related Concepts
- [[ai-os-overview]]
- [[ai-os-tech-stack]]
- [[ai-os-vertical-config]]
- [[ai-os-data-layer]]
- [[ai-os-client-onboarding]]
- [[ai-os-pricing-revenue]]
- [[developer-tooling]]
- [[vercel-deployment]]
- [[supabase-project-management]]

## References
- AI-OS-Master-Spec-v2.md (Section 13: Deployment Workflow)