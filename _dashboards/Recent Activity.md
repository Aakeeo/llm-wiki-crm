---
entity: dashboard
---

# Recent Activity

```dataview
TABLE WITHOUT ID
  file.link AS "Interaction",
  date AS "Date",
  interaction_type AS "Type",
  participants AS "With",
  company AS "Company",
  summary AS "Summary"
FROM "interactions"
WHERE entity = "interaction"
SORT date DESC
LIMIT 20
```
