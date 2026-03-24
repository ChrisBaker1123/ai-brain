---
type: reference
status: active
created: 2026-03-24
updated: 2026-03-24
domain: business
tags:
  - n8n
  - salesforce
  - automation
  - integration
  - dlk
---

# n8n Salesforce Integration Guide

Last Updated: 2026-03-24

## Overview

n8n provides a native Salesforce node supporting CRUD operations, queries, and trigger-based workflows. This is relevant for [[DLK-HUB]] workflow automation (WF2/WF3) and the broader [[Service-Playbook]] for building client automation systems.

## Authentication Methods

### 1. OAuth 2.0 (Recommended)
1. In Salesforce Setup, go to **App Manager** > **New External Client App** (or New Connected App for legacy)
2. Enable OAuth Settings
3. Set Callback URL to n8n's redirect URL
4. Set OAuth scopes: `api`, `refresh_token`, `offline_access`
5. Copy Consumer Key (Client ID) and Consumer Secret
6. In n8n, create Salesforce OAuth2 credential, paste Client ID + Secret
7. Click "Connect my account" and authorize

**Note**: Salesforce is deprecating Connected Apps. Use **External Client Apps** for new integrations.

### 2. OAuth 2.0 JWT (For server-to-server)
1. Create a private key and self-signed digital certificate
2. Create External Client App in Salesforce with the certificate
3. In n8n, enter Client ID and Private Key contents
4. No interactive authorization needed — suitable for automated/headless workflows

### Environment Options
- **Production** — Standard Salesforce org
- **Sandbox** — For testing before deploying to production

## Supported Operations

The n8n Salesforce node supports operations on these objects:

| Object | Operations |
|--------|------------|
| **Account** | Create, Get, Get All, Update, Delete, Get metadata |
| **Contact** | Create, Get, Get All, Update, Delete |
| **Lead** | Create, Get, Get All, Update, Delete, Convert |
| **Opportunity** | Create, Get, Get All, Update, Delete |
| **Task** | Create, Get, Get All, Update, Delete |
| **Case** | Create, Get, Get All, Update, Delete |
| **Attachment** | Create, Get, Get All, Update, Delete, Get metadata |
| **Custom Objects** | Via HTTP Request node with Salesforce credentials |

### Extended Operations via HTTP Request Node
For operations not natively supported by the Salesforce node, use the **HTTP Request node** with predefined Salesforce credential type. This gives access to the full Salesforce REST API:
- SOQL queries
- Bulk API operations
- Custom object CRUD
- Metadata API
- Composite requests

### Salesforce Trigger Node
Triggers workflows when:
- New Account created
- Account updated
- New Lead created
- New Opportunity created
- Opportunity updated
- Other standard/custom object changes

### AI Agent Integration
The Salesforce node can be used as an **AI tool** — parameters can be set automatically or directed by AI agents within n8n workflows. This is relevant for building intelligent CRM automation for clients.

## OAuth Setup Steps (Detailed)

### For n8n Cloud Users
1. In n8n, add Salesforce node to workflow
2. Select credential type > Salesforce OAuth2
3. Select Environment Type (Production/Sandbox)
4. Enter Salesforce Username
5. Click "Connect my account" — n8n handles the OAuth flow

### For Self-Hosted n8n
1. Log into Salesforce > Setup > App Manager
2. New External Client App (or Connected App)
3. Fill in Name, Contact Email
4. Check "Enable OAuth Settings"
5. Callback URL: Copy from n8n credential setup page
6. OAuth Scopes: `api`, `refresh_token`, `offline_access`
7. Save and wait ~10 minutes for Salesforce to propagate
8. Go to Manage Consumer Details > copy Consumer Key + Secret
9. In n8n: paste Client ID + Client Secret
10. Click "Connect my account"

### Common Issues
- **redirect_uri_mismatch** — Callback URL in Salesforce must exactly match n8n's Redirect URL
- **OAuth not connecting** — Salesforce admin may need to approve n8n as a connected app
- **Credentials don't save** — Ensure the Salesforce user has API access enabled on their profile
- **My Domain required** — Salesforce recommends deploying My Domain for OAuth

## Known Limitations

1. **No native webhook support** — Must use polling triggers or Salesforce Platform Events with HTTP nodes
2. **Custom objects** — Not directly available in the native node dropdown; must use HTTP Request node
3. **Bulk operations** — Not natively supported; use HTTP Request node with Bulk API 2.0
4. **Field mapping** — Complex custom field types may require manual mapping
5. **Rate limits** — Subject to Salesforce API limits (varies by edition)
6. **Token refresh** — OAuth tokens expire; n8n handles refresh automatically, but JWT is more reliable for unattended workflows
7. **Salesforce editions** — API access requires Enterprise, Unlimited, Developer, or Performance editions

## Best Practices for RIA CRM Integration

1. **Use JWT for production automations** — No interactive login required, more reliable for scheduled workflows
2. **Test in sandbox first** — Create a Salesforce sandbox, test all workflows before touching production data
3. **Map fields carefully** — Document which n8n workflow fields map to which Salesforce custom fields
4. **Error handling** — Add error branches in n8n for Salesforce API failures (rate limits, validation errors)
5. **Audit trail** — Log all Salesforce write operations for compliance purposes
6. **Batch processing** — For bulk updates, use the HTTP Request node with Bulk API 2.0 instead of individual record operations
7. **Refresh token policies** — Configure appropriate session and refresh token policies in Salesforce

## Example Workflow Ideas for DLK

### WF2: Post-Meeting CRM Update
```
Zocks Webhook → Parse Meeting Notes → n8n Salesforce Node → Update Contact Record
                                   → Create Follow-up Tasks
                                   → Update Opportunity Stage
```

### WF3: M&A Prospect Pipeline
```
Schedule Trigger → Fetch IAPD Data → Filter Criteria → Check Salesforce for Duplicates
                                                      → Create New Lead if not exists
                                                      → Assign to Rep
```

### Client Onboarding Automation
```
New Opportunity (Won) → Create Account → Generate Welcome Email
                      → Create Onboarding Tasks
                      → Notify Team via Slack/Email
```

## Community Resources
- n8n Salesforce node docs: https://docs.n8n.io/integrations/builtin/app-nodes/n8n-nodes-base.salesforce/
- n8n Salesforce credentials: https://docs.n8n.io/integrations/builtin/credentials/salesforce/
- n8n Community forum: https://community.n8n.io/ (search "Salesforce" for community workflows)
- Namaste Salesforce guide: https://www.namastesalesforce.com/blog/n8n-salesforce-integration-and-configuration/

## Needs Further Investigation
- DLK's specific Salesforce edition and API limits
- DLK's custom object schema (need admin access)
- Whether DLK uses Salesforce Overlay (XLR8, Practifi, etc.)
- Feasibility of JWT auth given DLK's Salesforce security policies
- Whether Platform Events can be used for real-time triggers

## Related Notes
- [[DLK-HUB]]
- [[FSC-Features]]
- [[Flow-Patterns]]
- [[n8n-Deployment-Guide]]
- [[Service-Playbook]]
