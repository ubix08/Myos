# AI-OS AI Integration Layer

## Summary
AI-OS implements a domain-aware AI assistant that understands the client's specific profession and workflows, with all AI calls routed through secure Supabase Edge Functions to keep API keys server-side.

## Definition
The AI-OS AI Integration Layer is a system that provides contextual AI assistance tailored to each client's vertical (profession), using dynamic system prompts assembled from vertical context, module context, and workspace state, with all AI processing happening securely on the backend.

## Key Ideas
### Philosophy
- AI is a **domain-aware assistant**, not a generic chatbot
- Every AI call is routed through a **Supabase Edge Function** (API key stays server-side)
- The system prompt is assembled dynamically from: vertical context + module context + workspace state
- All AI interactions are logged locally (for cost transparency + audit)
- AI works 100% without — workspace degrades gracefully if AI is disabled

### System Prompt Architecture
The system prompt is constructed by combining:
1. Vertical AI persona (name, role)
2. Domain context paragraph specific to the profession
3. Current workspace state (active projects, pending tasks, current module)
4. Terminology overrides (what contacts/tasks/notes/projects are called in this vertical)
5. Tone setting (professional/friendly/concise)
6. Rules for AI behavior (suggest concrete actions, reference actual data, never invent data, flag uncertainty)

### AI Features by Module
Each module has specific AI capabilities:
- **Tasks**: Natural language task creation, breakdown, prioritization, weekly review generation
- **Notes**: Summarize, expand, improve writing, extract tasks, convert to proposal
- **Contacts**: Suggest follow-up actions, summarize relationship history
- **Invoices**: Auto-fill from project data, suggest line items, draft cover message
- **Dashboard**: "What needs my attention today?" — cross-module AI briefing
- **Global**: Command palette AI: any freeform question about workspace data

### AI Provider Configuration (Per Deployment)
Configuration is stored in Supabase Edge Function environment (never in browser):
- Provider choice: openai | anthropic | groq
- Model selection (with default recommendations per use case)
- API key (stored in Supabase Vault)
- Cost controls: maxTokensPerCall and monthlyBudgetUSD

### Semantic Search (pgvector)
- On note save: generate embedding using text-embedding-3-small and store in notes.embedding
- Search: embed query, use match_notes RPC with threshold 0.78, return top results
- Enables semantic search across notes content beyond simple keyword matching

## Evidence and Findings
From AI-OS-Master-Spec-v2.md Section 10 (AI Integration Layer):
- Clear philosophy statements about AI as domain-aware assistant
- Detailed TypeScript function showing system prompt assembly
- Table listing AI features by module with specific capabilities
- AI Provider Configuration type definition showing secure storage approach
- Semantic search implementation using OpenAI embeddings and Supabase pgvector
- Emphasis on API keys never touching the browser (Edge Function Vault storage)

## Areas of Agreement
- All sources confirm the Edge Function approach for AI calls
- Consensus on dynamic system prompt assembly from multiple context sources
- Agreement on module-specific AI capabilities tailored to each function
- Shared understanding of semantic search using pgvector embeddings

## Areas of Disagreement
| Topic | Source Positions | Possible Explanation |
|-------|------------------|----------------------|
| Default models | Some sections mention different default models | Evolution as new models become available |
| Cost control specifics | Variations in how budget limits are described | Different emphasis in documentation |
| Semantic search threshold | Different threshold values mentioned (0.75 vs 0.78) | Tuning based on testing results |

## Related Concepts
- [[ai-os-overview]]
- [[ai-os-tech-stack]]
- [[ai-os-data-layer]]
- [[ai-os-vertical-config]]
- [[ai-os-module-system]]
- [[ai-os-ui-ux-system]]
- [[ai-integration-layer]]
- [[semantic-search-pgvector]]

## References
- AI-OS-Master-Spec-v2.md (Section 10: AI Integration Layer)
