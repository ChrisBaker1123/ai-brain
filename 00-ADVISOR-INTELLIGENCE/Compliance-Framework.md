---
type: reference
title: "Advisor Intelligence — Compliance Framework"
status: active
created: 2026-03-24
updated: 2026-03-24
---

# Compliance Framework

Master template for AI usage policies, SEC/FINRA requirements, and vendor due diligence. Customized per client.

## SEC/FINRA AI Guidance (2026)

### SEC Examination Priorities
- AI usage in investment advice and client communications
- Marketing Rule compliance for AI-generated content
- Cybersecurity and data privacy around AI tools
- Books and records requirements for AI-assisted work
- Vendor due diligence for AI service providers

### FINRA Considerations
- Supervisory requirements for AI-generated communications
- Record retention for AI interactions
- Suitability/best interest obligations when AI assists recommendations

## AI Usage Policy Template Components

Every client gets a customized version covering:

### 1. Approved Tools
- List of approved AI tools (e.g., Microsoft Copilot, specific Claude implementations)
- Version requirements and update policy
- Who approves new tools

### 2. Data Restrictions
- **Never enter into AI**: Client SSNs, account numbers, passwords, full DOB
- **Allowed with caution**: Client first names, general financial situations, anonymized scenarios
- **Freely usable**: Market data, regulatory references, template text, public information

### 3. Human Review Requirements
- All AI-generated client communications must be reviewed by the advisor before sending
- AI-generated compliance documents must be reviewed by CCO
- Investment recommendations may be informed by AI research but must reflect advisor judgment

### 4. Record Retention
- AI-generated drafts that become client communications: retain per existing communication policy
- AI prompts/queries: retain for 12 months minimum
- AI tool access logs: retain for audit trail

### 5. Vendor Due Diligence
- Document each AI vendor: company, data handling, security certifications, terms of service
- Annual review of all AI vendors
- Incident response plan for AI vendor breaches

### 6. Annual Review
- CCO reviews AI usage policy annually
- Update for new tools, regulations, and incidents
- All team members acknowledge updated policy

## Our Own Compliance (Advisor Intelligence)

### What We Access
- Client CRM data (Salesforce) — only with dedicated user account, logged access
- Public SEC data (IAPD, EDGAR) — freely available
- Firm tool configurations — with explicit permission

### What We Don't Access
- Client investment accounts directly
- Client PII beyond what's in CRM
- Custodian platforms with trading authority
- Any data outside the scope defined in the engagement letter

### Data Handling
- No client PII exported to our personal systems
- Salesforce work happens within their instance
- Research systems use only public data
- Secure credential storage (password manager, never plain text, never in vault)
- All access documented in client compliance file

### Insurance Considerations
- E&O (Errors & Omissions) insurance — research California requirements
- Professional liability coverage
- Cyber liability if handling any client data

---

## Related

- [[00-ADVISOR-INTELLIGENCE/INDEX|INDEX]] — Master hub
- [[AI-Usage-Policy-Template]] — Customizable template
- [[DLK-HUB]] → [[20-CLIENTS/DLK/Compliance/AI-Usage-Policy|DLK AI Usage Policy]] — First customized version
