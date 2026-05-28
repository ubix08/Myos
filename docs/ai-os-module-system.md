# AI-OS Module System

## Summary
AI-OS uses a modular architecture with a core set of always-included modules and optional domain-specific modules that can be enabled per vertical configuration.

## Definition
The AI-OS Module System is a plugin architecture where each module encapsulates specific functionality (UI components, data tables, AI capabilities, etc.) and can be selectively enabled based on the client's vertical configuration, allowing for domain-specific customization without code duplication.

## Key Ideas
### Module Interface
Every module implements the `AIModule` TypeScript interface which defines:
- Basic metadata (id, name, icon, version, tier)
- React components (main component, settings component, dashboard widget)
- Data ownership (dbTables, migrations)
- AI capabilities (systemPrompt, aiActions)
- Configuration (defaultConfig, permissions)

### Module Registry
Modules are auto-discovered via `import.meta.glob('./*/index.ts', { eager: true })` and registered in a central registry for dynamic loading.

### Core Modules (Always Included)
1. **Dashboard** - Widget grid pulling from all enabled modules, KPI summaries
2. **Tasks** - Projects, subtasks, kanban, priorities, deadlines, recurring tasks
3. **Notes** - Rich text (Tiptap), slash commands, backlinks, embeds
4. **Contacts** - CRM-lite with custom fields per vertical
5. **Search** - Global fuzzy + semantic search across all data
6. **Settings** - Global + per-module + AI provider configuration
7. **Export** - PDF, Markdown, JSON, CSV export capabilities

### Optional / Domain Modules
Vertical-specific modules that can be enabled based on the client's needs:
- **Invoices & Proposals** - Accountants, Freelancers
- **Time Tracking** - Consultants, Freelancers
- **Calendar** - All verticals
- **Document Vault** - Accountants, Clinics, Law
- **Finance Tracker** - Accountants, Solo Founders
- **Content Planner** - Creators, Agencies
- **Inventory** - Retail, E-commerce
- **Appointments** - Clinics, Service businesses
- **Knowledge Base** - All verticals (research + SOPs)
- **Team** - Any client with staff

## Evidence and Findings
From AI-OS-Master-Spec-v2.md Section 6 (Core Engine — Module System):
- Module interface definition in `src/types/module.ts` showing all required properties
- Module registry implementation using `import.meta.glob` for auto-discovery
- Tables listing core modules and their key features
- Tables listing optional modules and their primary verticals
- Clear separation between always-included core modules and vertical-specific optional modules

## Areas of Agreement
- All sources confirm the core vs optional module distinction
- Consensus on the Module Interface structure with id, name, components, data, AI, and config properties
- Agreement on auto-discovery mechanism for module registration
- Shared understanding that modules encapsulate both UI and data concerns

## Areas of Disagreement
| Topic | Source Positions | Possible Explanation |
|-------|------------------|----------------------|
| Specific module features | Some sections elaborate more on certain modules | Different levels of detail in various spec sections |
| Naming conventions | Minor variations in module names (e.g., "Invoices" vs "Invoices & Proposals") | Evolution of terminology during development |

## Related Concepts
- [[ai-os-overview]]
- [[ai-os-tech-stack]]
- [[ai-os-vertical-config]]
- [[ai-os-data-layer]]
- [[ai-os-ai-integration]]
- [[module-interface-definition]]
- [[module-registry-mechanism]]

## References
- AI-OS-Master-Spec-v2.md (Section 6: Core Engine — Module System)