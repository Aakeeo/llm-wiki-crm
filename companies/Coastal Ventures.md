---
type: company
name: "Coastal Ventures"
domain: "coastalvc.com"
industry: "Venture Capital"
size: smb
status: partner
location: "Miami, FL"
arr_potential: 50000
tags: [vc, partner, referral-source]
created: 2026-02-15
updated: 2026-03-28
---

# Coastal Ventures

## Overview

Coastal Ventures is a seed-stage VC firm focused on B2B SaaS. They invested in our seed round and are an active partner — referring portfolio companies our way and providing market intelligence. Managing partner Tom Nakamura is our primary relationship.

## Notes

- Good source of warm introductions to their portfolio companies
- They introduced us to Quantum Labs
- Annual LP meeting in June — they may want us to present

## Key Contacts

```dataview
TABLE role AS "Role", status AS "Status", last_contacted AS "Last Contact"
FROM "contacts"
WHERE company = link("Coastal Ventures")
```

## Active Deals

```dataview
TABLE stage AS "Stage", value AS "Value", probability AS "Prob"
FROM "deals"
WHERE company = link("Coastal Ventures") AND stage != "closed-lost"
```
