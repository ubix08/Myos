# AI-OS Vertical Configuration System

## Summary
AI-OS uses a JSON-driven vertical configuration system that enables domain-specific customization through a single configuration file per client deployment.

## Definition
The Vertical Configuration System in AI-OS is a mechanism where each client deployment is driven by a single JSON config file that defines everything from branding and enabled modules to AI persona and terminology overrides, allowing for deep customization without changing code.

## Key Ideas
### The Config File Structure
Every deployment is driven by a `VerticalConfig` TypeScript interface that includes:
- **Identification**: verticalId, productName, tagline
- **Branding**: primaryColor, accentColor, logoUrl, faviconUrl
- **Modules**: enabledModules array listing which modules to activate
- **AI Persona**: name, role, domainContext, tone (professional/friendly/concise)
- **Terminology Overrides**: Custom names for contact, task, note, and project
- **Dashboard Layout**: Widget configuration for the dashboard grid
- **Onboarding Flow**: Step-by-step checklist for first-time users
- **Feature Flags**: teamEnabled, aiEnabled, exportEnabled, calendarEnabled booleans

### Example: Freelance Consultant Config
A sample configuration for freelance consultants shows:
- verticalId: "freelance-consultant"
- productName: "ConsultOS"
- Branding with dark blue primary and red accent colors
- Enabled modules: dashboard, tasks, notes, contacts, invoices, time-tracking, calendar, export
- AI persona named "Aria" with consulting operations assistant role
- Terminology: contact="Client", task="Action Item", note="Brief", project="Engagement"
- Dashboard widgets showing overdue tasks, outstanding balance, weekly hours, active clients
- 4-step onboarding: add first client, create engagement, log time, generate invoice
- Feature flags: team disabled, AI enabled, export enabled, calendar enabled

### Pre-Built Vertical Configs (Starter Library)
The system includes starter configurations for common verticals:
- freelance-consultant → ConsultOS (Tasks, Invoices, Time Tracking, Contacts, Calendar)
- independent-accountant → AccountOS (Document Vault, Contacts, Deadlines, Finance Tracker, Export)
- local-clinic → ClinicOS (Appointments, Contacts, Document Vault, Tasks, Notes)
- solo-founder → FounderOS (Tasks, Notes, Content Planner, Finance Tracker, Contacts)
- freelance-designer → StudioOS (Projects, Proposals, Time Tracking, Contacts, Content Planner)
- local-retailer → ShopOS (Inventory, Contacts, Tasks, Finance Tracker)

## Evidence and Findings
From AI-OS-Master-Spec-v2.md Section 7 (Vertical Configuration System):
- Detailed VerticalConfig TypeScript interface definition
- Complete example configuration for freelance consultant
- Table showing pre-built vertical configs with IDs, product names, and key modules
- Explanation that "Every deployment is driven by a single JSON config file. This is the heart of the product factory."

## Areas of Agreement
- All sources confirm JSON-driven configuration approach
- Consensus on the structure including branding, modules, AI persona, terminology, dashboard, onboarding, and features
- Agreement that this enables deep customization without code changes
- Shared understanding that each client gets their own config file

## Areas of Disagreement
| Topic | Source Positions | Possible Explanation |
|-------|------------------|----------------------|
| Specific config fields | Some sections show slightly different field names | Evolution of the spec during development |
| Default values | Variations in what's considered required vs optional | Different emphasis in various documentation sections |

## Related Concepts
- [[ai-os-overview]]
- [[ai-os-module-system]]
- [[ai-os-tech-stack]]
- [[ai-os-ui-ux-system]]
- [[module-interface-definition]]
- [[vertical-config-file-structure]]

## References
- AI-OS-Master-Spec-v2.md (Section 7: Vertical Configuration System)