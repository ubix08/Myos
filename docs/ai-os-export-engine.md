# AI-OS Export Engine

## Summary
AI-OS includes a comprehensive export engine that supports multiple formats (PDF, Markdown, JSON, CSV, ZIP) for professional document generation and data portability, with domain-specific PDF templates per vertical.

## Definition
The AI-OS Export Engine is a system that enables users to export their workspace data in various formats for reporting, backup, sharing, and professional document generation, featuring domain-appropriate PDF templates tailored to each vertical's needs.

## Key Ideas
### Supported Formats
| Format | Use Case |
|--------|---------|
| PDF | Invoices, proposals, reports, case summaries |
| Markdown | Notes, knowledge base export |
| JSON | Full workspace backup |
| CSV | Tasks list, time entries, contacts |
| ZIP | Full workspace backup (JSON + attachments) |

### PDF Templates (Per Vertical)
Each vertical ships with domain-appropriate PDF templates:
- **freelance-consultant**: Invoice, Proposal, Statement of Work, Project Summary
- **independent-accountant**: Tax Summary, Client Report, Fee Statement
- **local-clinic**: Appointment Summary, Patient Report (no sensitive medical data)
- **solo-founder**: Investor Update, Sprint Report

### PDF Template Implementation
Templates use `@react-pdf/renderer` with TypeScript components:
```ts
export function InvoiceTemplate({ invoice, contact, branding }: InvoiceTemplateProps) {
  return (
    <Document>
      <Page style={styles.page}>
        <View style={styles.header}>
          <Image src={branding.logoUrl} style={styles.logo} />
          <Text style={styles.invoiceNumber}>Invoice #{invoice.number}</Text>
        </View>
        {/* ... line items, totals, payment terms */}
      </Page>
    </Document>
  );
}
```

### Export Capabilities
- **PDF Generation**: Professional document output with branding
- **Markdown Export**: Portable notes and knowledge base
- **JSON Backup**: Complete workspace data for migration or backup
- **CSV Export**: Tabular data for spreadsheet analysis
- **ZIP Packaging**: Complete backup including attachments

## Evidence and Findings
From AI-OS-Master-Spec-v2.md Section 12 (Export Engine):
- Detailed table showing supported formats and their use cases
- Explanation of PDF templates per vertical with examples
- TypeScript code sample showing PDF template implementation
- Clear statement that "Each vertical ships with domain-appropriate PDF templates"

## Areas of Agreement
- All sources confirm multiple export format support
- Consensus on PDF, Markdown, JSON, CSV, and ZIP formats
- Agreement on domain-specific PDF templates per vertical
- Shared understanding of the technical implementation using @react-pdf/renderer

## Areas of Disagreement
| Topic | Source Positions | Possible Explanation |
|-------|------------------|----------------------|
| Specific template details | Some sections show more elaborate templates | Different levels of implementation detail |
| Additional formats | Mentions of other potential formats (XML, Excel) | Evolution of feature set over time |
| Export triggers | Variations in how exports are initiated (UI vs command) | Implementation-specific details |

## Related Concepts
- [[ai-os-overview]]
- [[ai-os-tech-stack]]
- [[ai-os-module-system]]
- [[ai-os-vertical-config]]
- [[export-engine-capabilities]]
- [[pdf-templates-per-vertical]]

## References
- AI-OS-Master-Spec-v2.md (Section 12: Export Engine)