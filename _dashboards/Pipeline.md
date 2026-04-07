---
entity: dashboard
---

# Pipeline

## All Active Deals

```dataview
TABLE WITHOUT ID
  file.link AS "Deal",
  company AS "Company",
  stage AS "Stage",
  "$" + string(value) AS "Value",
  probability + "%" AS "Prob",
  expected_close AS "Expected Close",
  primary_contact AS "Contact"
FROM "deals"
WHERE entity = "deal" AND stage != "closed-lost"
SORT probability DESC
```

## Won Deals

```dataview
TABLE WITHOUT ID
  file.link AS "Deal",
  company AS "Company",
  "$" + string(value) AS "Value",
  expected_close AS "Close Date"
FROM "deals"
WHERE entity = "deal" AND stage = "closed-won"
SORT expected_close DESC
```

## Lost Deals

```dataview
TABLE WITHOUT ID
  file.link AS "Deal",
  company AS "Company",
  "$" + string(value) AS "Value"
FROM "deals"
WHERE entity = "deal" AND stage = "closed-lost"
SORT expected_close DESC
```
