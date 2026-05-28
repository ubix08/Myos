# AI-OS Folder Structure

## Summary
AI-OS follows a well-organized folder structure that separates concerns between core engine, modules, libraries, stores, types, vertical configurations, and deployment configurations.

## Definition
The AI-OS Folder Structure is a standardized organization of files and directories that enables maintainability, scalability, and clear separation of concerns between different aspects of the system, from core engine logic to vertical-specific configurations.

## Key Ideas
### Root Level Directories
- **src/** - Main source code directory
- **supabase/** - Database migrations and edge functions
- **cli/** - Deployment CLI (`ai-os-cli.mjs`)
- **docs/** - Documentation and handover materials
- **.opencode/** - OpenCode agent and command definitions
- **scripts/** - Additional utility scripts (if any)

### Source Code Structure (`src/`)
- **core/** - Fundamental system components
  - layout/ - AppShell, Sidebar, TopBar, CommandPalette
  - providers/ - Supabase, Auth, Theme, VerticalConfig providers
  - hooks/ - Custom React hooks (useAuth, useVertical, useAI, useModules)
  - router.tsx - TanStack Router setup
- **modules/** - Feature modules (dashboard, tasks, notes, etc.)
  - Each module has: index.ts (module definition), component files, AI actions
  - Auto-discovered via `import.meta.glob('./*/index.ts', { eager: true })`
- **lib/** - Libraries and utilities
  - supabase.ts - Supabase client initialization
  - auth.ts - Authentication helpers
  - ai/ - AI integration (client.ts, context.ts, prompts.ts)
  - export/ - PDF templates and format exporters
  - utils/ - Utility functions
- **verticals/** - JSON configuration files for each vertical
  - freelance-consultant.json
  - independent-accountant.json
  - local-clinic.json
  - solo-founder.json
  - freelance-designer.json
- **stores/** - Zustand stores
  - auth.store.ts
  - workspace.store.ts
  - ui.store.ts
- **types/** - TypeScript type definitions
  - module.ts - AIModule interface
  - vertical.ts - VerticalConfig interface
  - database.ts - Generated from Supabase schema
  - ai.ts - AI-related types
- **App.tsx** - Root application component
- **main.tsx** - Application entry point

### Supabase Structure (`supabase/`)
- **migrations/** - SQL migration files (numbered sequentially)
- **functions/** - Edge functions
  - ai-chat/ - Main AI edge function
  - ai-embed/ - Embedding generation
  - export-pdf/ - Server-side PDF generation
- **config.toml** - Supabase configuration

### CLI Structure (`cli/`)
- **ai-os-cli.mjs** - Node.js deployment CLI for scaffolding new client instances

### Documentation Structure (`docs/`)
- **verticals/** - Per-vertical setup guides
- **client-handover/** - Handover templates for clients

## Evidence and Findings
From AI-OS-Master-Spec-v2.md Section 16 (Folder Structure):
- Complete directory tree showing all folders and files
- Clear explanation of each directory's purpose
- Emphasis on the auto-discovery mechanism for modules via `import.meta.glob`
- Specification of where vertical configurations live (`src/verticals/`)

## Areas of Agreement
- All sources confirm the modular organization approach
- Consensus on the separation of core, modules, libs, verticals, stores, and types
- Agreement on the auto-discovery pattern for module registration
- Shared understanding that vertical configurations are JSON files in `src/verticals/`

## Areas of Disagreement
| Topic | Source Positions | Possible Explanation |
|-------|------------------|----------------------|
| Specific file names | Some sections show slightly different file organization | Evolution of the structure during development |
| Nesting levels | Variations in how deeply nested certain components are | Different organizational preferences |
| Additional directories | Mentions of other potential directories (utils, helpers) | Implementation details that may evolve |

## Related Concepts
- [[ai-os-overview]]
- [[ai-os-module-system]]
- [[ai-os-vertical-config]]
- [[ai-os-tech-stack]]
- [[ai-os-deployment-workflow]]
- [[folder-structure-details]]

## References
- AI-OS-Master-Spec-v2.md (Section 16: Folder Structure)