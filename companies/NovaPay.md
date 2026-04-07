---
entity: company
name: "NovaPay"
domain: "novapay.com"
industry: "Fintech"
size: startup
status: prospect
location: "New York, NY"
arr_potential: 0
tags: [fintech, payments, coastal-portfolio]
created: 2026-04-07
updated: 2026-04-07
---

# NovaPay

## Overview

NovaPay is a fintech startup building payment infrastructure for e-commerce platforms. Series A ($12M raised), 30 employees, based in New York. They serve ~500 e-commerce merchants. Introduced by [[Tom Nakamura]] at [[Coastal Ventures]] (portfolio company).

They need real-time transaction analytics for their merchant dashboard. Currently using a homegrown solution that can't scale past 1M events/day. Budget approved for Q2, need a solution by June.

## Notes

- Coastal Ventures portfolio company — warm intro from Tom
- Fast-moving evaluation — wants demo next week
- PCI DSS compliance is a hard requirement

## Key Contacts

```dataview
TABLE role AS "Role", status AS "Status", last_contacted AS "Last Contact"
FROM "contacts"
WHERE company = link("NovaPay")
```

## Active Deals

```dataview
TABLE stage AS "Stage", value AS "Value", probability AS "Prob"
FROM "deals"
WHERE company = link("NovaPay") AND stage != "closed-lost"
```
