---
type: document
title: "DLK Vendor Due Diligence"
status: draft
created: 2026-03-24
client: DLK
---

# DLK Vendor Due Diligence — AI Tools

> Document every AI tool recommended to DLK. Required by compliance framework.

## Microsoft Copilot (M365)

| Field | Detail |
|-------|--------|
| **Vendor** | Microsoft Corporation |
| **Product** | Microsoft 365 Copilot |
| **Data handling** | Processes within Microsoft's enterprise cloud (Azure). Tenant data stays within tenant boundary. |
| **Security** | SOC 1, SOC 2, ISO 27001, ISO 27018, FedRAMP |
| **Data used for training** | No — enterprise Copilot data is not used for model training |
| **Terms reviewed** | [Date TBD] |
| **Recommended by** | Advisor Intelligence |
| **Approved by** | [Don Dempster — pending] |

## Otter.ai (Pending Recommendation)

| Field | Detail |
|-------|--------|
| **Vendor** | Otter.ai, Inc. |
| **Product** | Otter Business |
| **Data handling** | Cloud-based transcription. Audio uploaded, transcribed, stored in Otter cloud. |
| **Security** | SOC 2 Type II, encryption at rest and in transit |
| **Data used for training** | Check current policy — may opt out |
| **Retention** | Configurable — recommend deleting recordings after CRM entry |
| **Terms reviewed** | [Date TBD] |
| **Risk note** | Meeting recordings contain client conversations. Must configure data retention carefully. |
| **Alternative** | Fireflies.ai (similar capabilities, check vendor policies) |

## Advisor Intelligence Platform

| Field | Detail |
|-------|--------|
| **Vendor** | Advisor Intelligence (Christopher Baker) |
| **Product** | AI Toolkit + Custom Workflows |
| **Data handling** | Toolkit is copy-paste templates (no data ingestion). Custom workflows run within DLK's Salesforce instance. Prospecting system uses only public SEC data. |
| **Security** | Supabase (SOC 2), Vercel (SOC 2), no client data stored |
| **Data used for training** | No client data ever enters our AI systems |
| **Terms reviewed** | Per engagement letter |

## Future Tools (As Recommended)

Each new tool gets a row here before recommendation to DLK.

---

## Related

- [[DLK-HUB]]
- [[20-CLIENTS/DLK/Compliance/AI-Usage-Policy|AI Usage Policy]]
- [[Compliance-Framework]]
