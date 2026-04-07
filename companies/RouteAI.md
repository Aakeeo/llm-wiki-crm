---
type: company
name: "RouteAI"
domain: "routeai.com"
industry: "Logistics"
size: startup
status: prospect
location: "Chicago, IL"
arr_potential: 80000
tags: [logistics, analytics, coastal-portfolio]
created: 2026-04-07
updated: 2026-04-07
---

# RouteAI

## Overview

RouteAI is a logistics startup building route optimization software for last-mile delivery companies. Series A ($8M raised), 25 employees, based in Chicago. They serve ~200 delivery company customers, processing 500K deliveries/day. Introduced by [[Tom Nakamura]] at [[Coastal Ventures]] (portfolio company).

Their customers are asking for delivery performance analytics — on-time rates, driver efficiency, cost-per-delivery trends. Currently handling this with manual SQL queries. They want to embed a self-serve analytics dashboard into their platform.

## Notes

- Coastal Ventures portfolio company — third referral from Tom (after Quantum Labs and NovaPay)
- Strong product-market fit signal: customers are already asking for this feature
- Multi-tenant requirement is key — each delivery company sees only their data
- CTO Raj Mehta needs to sign off on technical architecture

## Key Contacts

```dataview
TABLE role AS "Role", status AS "Status", last_contacted AS "Last Contact"
FROM "contacts"
WHERE company = link("RouteAI")
```

## Active Deals

```dataview
TABLE stage AS "Stage", value AS "Value", probability AS "Prob"
FROM "deals"
WHERE company = link("RouteAI") AND stage != "closed-lost"
```
