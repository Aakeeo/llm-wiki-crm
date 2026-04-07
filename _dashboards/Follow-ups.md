---
entity: dashboard
---

# Follow-ups

## Overdue

```dataview
TABLE WITHOUT ID
  file.link AS "Task",
  due_date AS "Due",
  priority AS "Priority",
  assigned_to AS "Owner",
  related_to AS "Related To"
FROM "tasks"
WHERE entity = "task" AND status != "done" AND due_date < date(today)
SORT due_date ASC
```

## Upcoming

```dataview
TABLE WITHOUT ID
  file.link AS "Task",
  due_date AS "Due",
  priority AS "Priority",
  assigned_to AS "Owner",
  related_to AS "Related To"
FROM "tasks"
WHERE entity = "task" AND status != "done" AND due_date >= date(today)
SORT due_date ASC
```

## Completed

```dataview
TABLE WITHOUT ID
  file.link AS "Task",
  due_date AS "Due",
  related_to AS "Related To"
FROM "tasks"
WHERE entity = "task" AND status = "done"
SORT due_date DESC
LIMIT 10
```
