---
entity: company
name: "Brightpath Education"
domain: "brightpathedu.org"
industry: "Education"
size: mid-market
status: prospect
location: "Austin, TX"
arr_potential: 150000
tags: [education, lms, mid-market]
created: 2026-03-15
updated: 2026-04-05
---

# Brightpath Education

## Overview

Brightpath is a K-12 education technology nonprofit that provides learning management systems to school districts across Texas and the Southwest. They serve 200+ school districts and are looking to upgrade their LMS infrastructure. Funded through a mix of grants and district contracts.

## Notes

- Procurement is slow — requires board approval for contracts over $100K
- Strong existing relationship with their Head of Technology
- They're also evaluating Canvas and Schoology

## Key Contacts

```dataview
TABLE role AS "Role", status AS "Status", last_contacted AS "Last Contact"
FROM "contacts"
WHERE company = link("Brightpath Education")
```

## Active Deals

```dataview
TABLE stage AS "Stage", value AS "Value", probability AS "Prob"
FROM "deals"
WHERE company = link("Brightpath Education") AND stage != "closed-lost"
```
