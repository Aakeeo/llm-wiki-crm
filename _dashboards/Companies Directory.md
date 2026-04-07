---
type: dashboard
---

# Companies Directory

```dataview
TABLE WITHOUT ID
  file.link AS "Company",
  industry AS "Industry",
  size AS "Size",
  status AS "Status",
  location AS "Location"
FROM "companies"
WHERE type = "company"
SORT name ASC
```
