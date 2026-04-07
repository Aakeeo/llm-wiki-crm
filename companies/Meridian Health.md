---
type: company
name: "Meridian Health"
domain: "meridianhealth.com"
industry: "Healthcare"
size: enterprise
status: prospect
location: "Boston, MA"
arr_potential: 240000
tags: [healthcare, enterprise-sales]
created: 2026-03-10
updated: 2026-04-01
---

# Meridian Health

## Overview

Meridian Health is a regional healthcare network with 12 hospitals and 200+ clinics across the Northeast. They're modernizing their patient management infrastructure and looking to migrate from a legacy on-premise system to a cloud-based platform. Annual IT budget is ~$15M. Key decision-making is centralized through their CTO office.

## Notes

- Fiscal year ends in June — budget decisions typically finalized by April
- Strong compliance requirements (HIPAA) — security review will be thorough
- Current vendor is Oracle Health (formerly Cerner) — contract expires Q3 2026

## Key Contacts

```dataview
TABLE role AS "Role", status AS "Status", last_contacted AS "Last Contact"
FROM "contacts"
WHERE company = link("Meridian Health")
```

## Active Deals

```dataview
TABLE stage AS "Stage", value AS "Value", probability AS "Prob"
FROM "deals"
WHERE company = link("Meridian Health") AND stage != "closed-lost"
```
