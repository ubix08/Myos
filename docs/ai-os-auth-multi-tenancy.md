# AI-OS Authentication & Multi-Tenancy

## Summary
AI-OS implements authentication using Supabase Auth and employs a per-client Supabase project strategy for multi-tenancy, ensuring complete data isolation while providing role-based access control within each client deployment.

## Definition
The AI-OS Authentication & Multi-Tenancy system combines Supabase Auth for user authentication with a strategic decision to use isolated Supabase projects per client rather than a shared database with row-level security, prioritizing data isolation, portability, and operational simplicity for a solo operator.

## Key Ideas
### Auth Flow
1. User visits workspace URL
2. Supabase Auth checks for valid JWT in localStorage
3. If expired/missing → Login page (email/password or magic link)
4. On login → load profile + vertical config
5. Render workspace

### Auth Implementation
- Uses `@supabase/supabase-js` client initialized with environment variables
- Session listener updates auth store on sign-in/sign-out events
- Clean separation between auth state management and application state

### Row-Level Security (Within a Client Project)
Even within isolated projects, RLS provides role-based access:
- Policies define what authenticated users can do (read tasks)
- Additional policies restrict sensitive operations (only owner can delete tasks)
- Role checking happens via `profiles` table joined with `auth.uid()`

### Multi-Tenancy Strategy: Per-Client Supabase Project
Each client deployment gets its own isolated Supabase project rather than sharing a database:

**Why per-project over shared + RLS:**
- **Data isolation**: Complete vs policy-enforced (risk of misconfiguration)
- **Client data portability**: Simple export vs complex
- **Billing transparency**: Clear per-client vs blended
- **Ops complexity**: More projects to manage vs one project with complex policies
- **Appropriate for**: Solo operator, <50 clients vs platform with hundreds of tenants

**Scaling note**: Per-project is right until ~30-40 active clients; then evaluate migrating to shared project with mature RLS layer.

### API Key Storage (Security)
Client AI provider API keys are stored in Supabase Edge Function secrets:
- Never in frontend bundle or localStorage
- Frontend calls Supabase Edge Function ("ai-chat")
- Edge Function reads API key from Vault → calls OpenAI/Anthropic/Groq
- Edge Function streams response back to client
- API key never touches the browser

## Evidence and Findings
From AI-OS-Master-Spec-v2.md Section 9 (Authentication & Multi-Tenancy):
- Detailed auth flow description showing JWT checking and login process
- TypeScript implementation of supabase client initialization and session listener
- SQL examples showing row-level security policies for tasks table
- Comparison table detailing reasons for per-project multi-tenancy choice
- Diagram showing frontend → Edge Function → AI provider flow for secure API key handling

## Areas of Agreement
- All sources confirm Supabase Auth as the authentication mechanism
- Consensus on using environment variables for Supabase connection details
- Agreement that RLS is used within client projects for role-based access
- Shared understanding that per-client projects provide better data isolation

## Areas of Disagreement
| Topic | Source Positions | Possible Explanation |
|-------|------------------|----------------------|
| Scaling threshold | Some mention 30-40 clients, others less specific | Evolution of thinking as system matures |
| RLS policy complexity | Variations in policy examples shown | Different focus in various documentation sections |
| Auth providers | Some sections detail specific providers (Google, GitHub) | Optional features not core to spec |

## Related Concepts
- [[ai-os-overview]]
- [[ai-os-data-layer]]
- [[ai-os-tech-stack]]
- [[ai-os-vertical-config]]
- [[ai-os-deployment-workflow]]
- [[auth-multi-tenancy-details]]
- [[multi-tenancy-strategy]]

## References
- AI-OS-Master-Spec-v2.md (Section 9: Authentication & Multi-Tenancy)