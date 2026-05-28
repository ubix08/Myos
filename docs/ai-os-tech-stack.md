# AI-OS Tech Stack

## Summary
AI-OS uses a modern, production-ready tech stack centered around React 19 + Vite + TypeScript on the frontend and Supabase (PostgreSQL) on the backend, with pluggable AI providers and Vercel deployment.

## Definition
The AI-OS tech stack is a carefully curated set of technologies chosen for developer experience, performance, scalability, and maintainability, enabling a solo operator to build and manage multiple client deployments from a single codebase.

## Key Ideas
### Frontend Stack
- **React 19 + Vite + TypeScript** - Fast builds, excellent developer experience, solid ecosystem
- **Tailwind CSS v4 + shadcn/ui** - Rapid UI development with production-quality components
- **Zustand + TanStack Query** - Lightweight global state management + server state synchronization
- **TanStack Router** - Type-safe routing with automatic code splitting
- **Tiptap (ProseMirror)** - Best-in-class rich text editor
- **@react-pdf/renderer** - Branded PDF document output
- **Lucide React** - Consistent, lightweight icon set
- **cmDK** - Keyboard-first command palette navigation
- **Recharts** - Dashboard and analytics visualization
- **@dnd-kit** - Module-level drag-and-drop for kanban boards and sorting
- **Framer Motion** - Micro-interactions and smooth animations

### Backend / Cloud Services
- **Supabase (PostgreSQL)** - Integrated database, authentication, storage, real-time capabilities, and pgvector for semantic search
- **Supabase Auth** - Email/password, magic link, and OAuth authentication
- **Supabase Storage** - File uploads for documents and attachments
- **Pluggable AI Providers** - OpenAI, Anthropic, Groq (client-configurable via environment variables)
- **Supabase Edge Functions** - Server-side AI calls and webhooks (keeps API keys secure)
- **Vercel** - Frontend deployment with global CDN and custom domains per client
- **Supabase** - Backend deployment (database, auth, storage, edge functions)

### Developer Tooling
- **ai-os-cli** (custom Node.js script) - Scaffold new client deployments
- **GitHub** - Source control with one branch per client vertical
- **Doppler / Vercel env vars** - Secrets management per deployment
- **Supabase CLI** - Database migrations and schema management

## Evidence and Findings
From AI-OS-Master-Spec-v2.md Section 4 (Tech Stack):
- Frontend choices justified by "Fast builds, great DX, solid ecosystem" (React/Vite/TS) and "Rapid UI with production quality" (Tailwind/shadcn)
- Backend choice of Supabase due to "Auth + DB + Storage + Realtime + pgvector" in one platform
- Deployment strategy: "Vercel (frontend) + Supabase (backend) - Zero-ops, global CDN"
- Developer tooling includes custom CLI for client scaffotyping and Supabase CLI for DB management

## Areas of Agreement
- All sources confirm React 19 + Vite + TypeScript as the frontend foundation
- Consensus on Supabase as the chosen backend/platform solution
- Agreement on Vercel for frontend deployment and Supabase for backend
- Shared understanding of the pluggable AI provider approach (OpenAI/Anthropic/Groq)

## Areas of Disagreement
| Topic | Source Positions | Possible Explanation |
|-------|------------------|----------------------|
| CSS Framework version | Some mention Tailwind v3, others v4 | Spec evolution over time |
| Routing Library | Some sections mention React Router v6, others TanStack Router | Evolution during development |
| State Management | Variations in description of Zustand/TanStack Usage | Different emphasis in different sections |

## Related Concepts
- [[ai-os-overview]]
- [[ai-os-module-system]]
- [[ai-os-data-layer]]
- [[ai-os-ai-integration]]
- [[ai-os-ui-ux-system]]
- [[ai-os-deployment-workflow]]

## References
- AI-OS-Master-Spec-v2.md (Section 4: Tech Stack)