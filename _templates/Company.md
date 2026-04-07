---
entity: company
name: "{{name}}"
domain: ""
industry: ""
size: ""
status: prospect
location: ""
arr_potential: 0
tags: []
created: {{date}}
updated: {{date}}
---

# {{name}}

## Overview


## Notes


## Key Contacts

```dataview
TABLE role AS "Role", status AS "Status", last_contacted AS "Last Contact"
FROM "contacts"
WHERE company = link(this.file.name)
```

## Active Deals

```dataview
TABLE stage AS "Stage", value AS "Value", probability AS "Prob"
FROM "deals"
WHERE company = link(this.file.name) AND stage != "closed-lost"
```
