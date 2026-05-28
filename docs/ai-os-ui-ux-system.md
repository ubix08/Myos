# AI-OS UI/UX System

## Summary
AI-OS implements a terminology-aware, domain-specific UI/UX system that adapts its interface language, colors, and layout based on each client's vertical configuration, creating a personalized experience that matches the user's professional context.

## Definition
The AI-OS UI/UX System is a set of design principles and implementation patterns that ensure the interface speaks the user's professional language, uses their branding colors, provides keyboard-first navigation, and adapts to different device contexts while maintaining consistency across modules.

## Key Ideas
### Layout Structure
- **TopBar**: Logo, Search, AI Button, User info
- **Sidebar**: Module navigation (240px width on desktop)
- **Main Workspace Area**: Where module views render
- **Mobile-responsive**: Sidebar collapses to bottom navigation on mobile devices

### Key UI Principles
1. **Terminology-aware**: All labels use the vertical's configured terminology (never generic "tasks" if vertical says "action items")
2. **Domain color**: Primary + accent colors from vertical config applied via CSS custom properties
3. **Keyboard-first**: Full command palette (Cmd+K) with AI-enhanced search
4. **Progressive disclosure**: Simple default views, advanced options hidden until needed
5. **Mobile-responsive**: Clients often check on phone — sidebar collapses to bottom nav on mobile

### Command Palette (cmdk)
Central navigation + AI entry point:
- Cmd+K → opens palette
  - Navigate to [module] (navigation)
  - Create new [task/note/etc] (quick create)
  - Search [query] (global search)
  - Ask AI: [anything] (AI chat)
  - Recent items (history)

### Theme Engine
- Applies vertical theme via CSS custom properties:
  ```ts
  export function applyVerticalTheme(config: VerticalConfig) {
    const root = document.documentElement;
    root.style.setProperty('--color-primary', config.branding.primaryColor);
    root.style.setProperty('--color-accent', config.branding.accentColor);
    // Tailwind uses these via CSS var utilities
  }
  ```

## Evidence and Findings
From AI-OS-Master-Spec-v2.md Section 11 (UI/UX System):
- Detailed layout diagram showing TopBar, Sidebar, and Main Workspace Area
- Explicit listing of the 5 key UI principles with explanations
- Command palette structure showing its 5 functions
- TypeScript implementation of the theme engine function
- Emphasis on terminology-awareness: "All labels use the vertical's configured terminology"

## Areas of Agreement
- All sources confirm the terminology-aware approach as a core principle
- Consensus on the layout structure with TopBar, Sidebar, and Main areas
- Agreement on the command palette as central navigation+AI entry point
- Shared understanding of the theme engine using CSS custom properties

## Areas of Disagreement
| Topic | Source Positions | Possible Explanation |
|-------|------------------|----------------------|
| Specific UI components | Some sections mention additional components | Different levels of detail in documentation |
| Breakpoints | Variations in mobile vs desktop thresholds | Implementation details that may evolve |
| Animation libraries | Some mention Framer Motion, others less specific | Optional enhancements vs core requirements |

## Related Concepts
- [[ai-os-overview]]
- [[ai-os-tech-stack]]
- [[ai-os-vertical-config]]
- [[ai-os-module-system]]
- [[ai-os-ai-integration]]
- [[ui-ux-system-details]]
- [[terminology-aware-design]]
- [[command-palette-pattern]]

## References
- AI-OS-Master-Spec-v2.md (Section 11: UI/UX System)