# AI-OS Data Layer — Supabase

## Summary
AI-OS uses Supabase as its backend platform, providing PostgreSQL database, authentication, storage, real-time capabilities, and pgvector for semantic search, with a per-client project deployment strategy for data isolation.

## Definition
The AI-OS Data Layer is built on Supabase, chosen for its integrated backend services (database, auth, storage, real-time, and vector capabilities), enabling a solo operator to manage isolated client data while providing enterprise-grade features like authentication, row-level security, and semantic search.

## Key Ideas
### Core Schema (All Verticals)
The database schema includes tables that are common to all AI-OS deployments:
- **workspaces** - One per deployment, stores workspace metadata and vertical config snapshot
- **profiles** - Extends Supabase Auth users with additional information (full name, role, avatar, preferences)
- **tasks** - Task management with title, description, status, priority, due date, project/contact associations
- **projects** - Parent entities for tasks, with name, description, status, due date, and contact associations
- **notes** - Rich text notes with Tiptap JSON content, plain text for search, tags, and pgvector embeddings for semantic search
- **contacts** - CRM-lite with name, contact info, company, type, tags, and vertical-specific custom fields
- **ai_interactions** - Audit log of AI interactions including prompt, response, tokens used, and cost

### Module-Specific Tables (Examples)
Additional tables are created for enabled modules:
- **invoices** - Invoice management with contact/project associations, line items, tax calculations, and status tracking
- **time_entries** - Time tracking linked to tasks/projects/contacts with duration, billable flag, and hourly rates
- **documents** - Document vault with file metadata, storage paths, and associations to contacts/projects

### Schema Migration Strategy
- SQL migrations are organized in `supabase/migrations/` with numbered files for each module
- On new client setup: run only migrations for enabled modules
- On module add-on: run the new module's migration against existing project

### Realtime Subscriptions (Where Used)
Supabase real-time capabilities are leveraged for:
- Task status changes (collaborative task board)
- New AI responses streaming into notes
- Invoice status updates
- Dashboard widget data refresh

## Evidence and Findings
From AI-OS-Master-Spec-v2.md Section 8 (Data Layer — Supabase):
- Complete SQL schema definition for core tables and module-specific examples
- Explanation of migration strategy showing numbered migration files
- List of real-time subscription use cases demonstrating practical application
- Clear statement that "Supabase (PostgreSQL)" was chosen for "Auth + DB + Storage + Realtime + pgvector"

## Areas of Agreement
- All sources confirm Supabase as the chosen backend platform
- Consensus on the core schema structure with workspaces, profiles, tasks, notes, contacts, and ai_interactions tables
- Agreement on the per-client project deployment strategy for data isolation
- Shared understanding of Supabase's real-time capabilities usage

## Areas of Disagreement
| Topic | Source Positions | Possible Explanation |
|-------|------------------|----------------------|
| Specific table details | Some sections elaborate more on certain tables | Different levels of detail in various spec sections |
| Migration naming conventions | Variations in how migrations are referenced | Evolution of the spec over time |
| Extent of real-time usage | Different sections mention different use cases | Ongoing feature development |

## Related Concepts
- [[ai-os-overview]]
- [[ai-os-tech-stack]]
- [[ai-os-module-system]]
- [[ai-os-auth-multi-tenancy]]
- [[ai-os-ai-integration]]
- [[data-layer-supabase]]
- [[auth-multi-tenancy-details]]

## References
- AI-OS-Master-Spec-v2.md (Section 8: Data Layer — Supabase)