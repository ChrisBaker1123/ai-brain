---
type: document
title: "DLK Data Handling Protocol"
status: draft
created: 2026-03-24
client: DLK
---

# DLK Data Handling Protocol

> How Advisor Intelligence handles DLK's data. Attachment to the engagement letter.

## Principle

**No client PII leaves DLK's systems.** All work happens within their Salesforce instance, their tools, and with publicly available data. Cri does not maintain a separate database of DLK client information.

## Access Model

### What Cri Accesses

| System | Access Type | Purpose | Data Touched |
|--------|-----------|---------|-------------|
| **Salesforce** | Dedicated user account, admin permissions | Build Flows, configure automations, create dashboards | Contact records, Tasks, custom objects. No export of client data. |
| **SEC IAPD/EDGAR** | Public data, no authentication | Advisor prospecting system (WF1) | Publicly filed Form ADV data for RIA firms. Zero client data. |
| **DLK website** | Public | Reference and research | Public information only |

### What Cri Does NOT Access

| System | Reason |
|--------|--------|
| Schwab Advisor Center | No trading authority. No need for direct access. |
| intelliflo redblack | Trading/rebalancing system. Brian and Mark manage directly. |
| Client investment accounts | Never. Under any circumstances. |
| Client personal financial data | Only what's visible in Salesforce CRM records as needed for workflows. |
| DLK email accounts | No access to any team member's email. |
| DLK file storage | No access unless specifically shared for a workflow. |

## Credential Security

| Practice | Implementation |
|----------|---------------|
| Salesforce credentials | Stored in encrypted password manager (1Password/Bitwarden). Never in plain text. Never in Obsidian vault. Never in code repositories. |
| Shared credentials | DLK provides via secure method (password manager share, not email/text). |
| Session management | Log out of Salesforce after each work session. |
| 2FA | Enable 2FA on dedicated Salesforce account if available. |

## Data Retention

### What Cri Retains

| Data | Where | How Long | Purpose |
|------|-------|----------|---------|
| Workflow specs and documentation | Obsidian vault (local, encrypted) | Duration of engagement + 90 days | Reference and continuity |
| Prospecting intelligence reports | Obsidian vault + delivered to Don | Duration of engagement | Client deliverable and historical tracking |
| SEC public data (parsed) | VPS (local processing) | Refreshed monthly | Prospecting system input |
| Meeting notes and transcripts | Obsidian vault (local) | Duration of engagement + 90 days | Reference |

### What Cri Does NOT Retain

| Data | Policy |
|------|--------|
| Client PII | Never stored on personal systems |
| Client account data | Never exported from Salesforce |
| DLK proprietary strategies | Not documented outside engagement scope |
| Client communications | Stay in DLK's systems |

### Post-Termination

Upon termination of the engagement:
1. All DLK-specific documentation is offered to DLK for retention
2. Cri deletes or archives DLK files within 30 days
3. Salesforce dedicated user account is deactivated by DLK
4. VPS prospecting scripts are offered to DLK or decommissioned
5. No client data remains on Cri's systems (there was none to begin with)

## Advisor Prospecting System (WF1) — Special Note

The prospecting system uses **only publicly available SEC data**:
- Form ADV filings (public record, available to anyone)
- EDGAR 13F filings (public record)
- LinkedIn profiles (public or semi-public)
- Firm websites (public)

**Zero DLK client data** is used in the prospecting system. The system identifies potential acquisition targets for DLK — it does not process or reference any DLK client information.

## Salesforce Work — Special Note

All Salesforce automation (Flows, custom fields, dashboards) is built **within DLK's Salesforce instance**:
- Work product belongs to DLK
- Configurations remain in DLK's org if engagement ends
- No Salesforce data is exported or synced to external systems
- All changes are documented in workflow Build-Log files

## California Requirements

As a technology consultant serving SEC-registered investment advisers in California:
- [ ] Research E&O (Errors & Omissions) insurance requirements
- [ ] Research professional liability coverage
- [ ] Confirm no licensing requirements for AI consulting to RIAs
- [ ] Document California Consumer Privacy Act (CCPA) compliance (if applicable)

## Breach Response

If Cri suspects a data breach involving DLK data:
1. **Immediately** notify Don Dempster
2. **Document** the incident: what happened, what data, scope of exposure
3. **Remediate**: Revoke compromised access, contain the breach
4. **Cooperate** with DLK's incident response process
5. **Report** to regulators as directed by DLK

---

## Related

- [[DLK-HUB]]
- [[20-CLIENTS/DLK/Compliance/AI-Usage-Policy|AI Usage Policy]]
- [[20-CLIENTS/DLK/Engagement/Engagement-Letter|Engagement Letter]]
- [[Compliance-Framework]]
