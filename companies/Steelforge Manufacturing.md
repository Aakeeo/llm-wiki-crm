---
entity: company
name: "Steelforge Manufacturing"
domain: "steelforgemfg.com"
industry: "Manufacturing"
size: enterprise
status: prospect
location: "Detroit, MI"
arr_potential: 320000
tags: [manufacturing, iot, enterprise-sales]
created: 2026-03-20
updated: 2026-03-25
---

# Steelforge Manufacturing

## Overview

Steelforge is a Fortune 500 steel and automotive parts manufacturer with 15 plants across the Midwest. They're in the early stages of an Industry 4.0 initiative — connecting factory floor equipment to a centralized IoT dashboard for predictive maintenance and efficiency monitoring. Early conversations, big potential.

## Notes

- Very early stage — still building internal business case
- Multiple stakeholders involved: VP Engineering, VP Operations, CIO
- Budget hasn't been allocated yet — likely Q1 2027
- Long sales cycle expected (6-12 months)

## Key Contacts

```dataview
TABLE role AS "Role", status AS "Status", last_contacted AS "Last Contact"
FROM "contacts"
WHERE company = link("Steelforge Manufacturing")
```

## Active Deals

```dataview
TABLE stage AS "Stage", value AS "Value", probability AS "Prob"
FROM "deals"
WHERE company = link("Steelforge Manufacturing") AND stage != "closed-lost"
```
