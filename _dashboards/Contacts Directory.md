---
type: dashboard
---

# Contacts Directory

```dataview
TABLE WITHOUT ID
  file.link AS "Name",
  company AS "Company",
  role AS "Role",
  status AS "Status",
  last_contacted AS "Last Contact",
  email AS "Email"
FROM "contacts"
WHERE type = "contact"
SORT company ASC, name ASC
```
