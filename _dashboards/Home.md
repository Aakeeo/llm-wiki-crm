---
type: dashboard
---

# CRM Home

Welcome to your LLM-maintained CRM. Drop raw sources (meeting notes, emails, transcripts) into `_inbox/` and ask your LLM to ingest them.

---

## Quick Stats

```dataview
TABLE WITHOUT ID
  length(filter(rows, (r) => r.stage != "closed-lost" AND r.stage != "closed-won")) AS "Active Deals",
  length(filter(rows, (r) => r.stage = "closed-won")) AS "Won Deals"
FROM "deals"
WHERE type = "deal"
FLATTEN stage
GROUP BY true
```

```dataview
TABLE WITHOUT ID
  length(filter(rows, (r) => r.status = "active")) AS "Active Contacts",
  length(rows) AS "Total Contacts"
FROM "contacts"
WHERE type = "contact"
GROUP BY true
```

```dataview
TABLE WITHOUT ID
  length(filter(rows, (r) => r.status != "done")) AS "Open Tasks",
  length(filter(rows, (r) => r.status = "done")) AS "Completed Tasks"
FROM "tasks"
WHERE type = "task"
GROUP BY true
```

---

## Dashboards

- [[Pipeline]] — deals by stage with values and probabilities
- [[Recent Activity]] — latest interactions across all accounts
- [[Follow-ups]] — open tasks sorted by due date
- [[Contacts Directory]] — all contacts with company and status
- [[Companies Directory]] — all companies with deal counts

---

## Quick Actions

To use this CRM with your LLM agent:

1. **Ingest a source:** drop meeting notes into `_inbox/`, then tell your LLM: *"Process the new file in _inbox"*
2. **Ask a question:** *"What's our pipeline value this quarter?"* or *"Who are our warmest leads?"*
3. **Update a record:** *"Move the Acme deal to negotiation"* or *"Mark Jane as inactive"*
4. **Health check:** *"Run a lint check on the CRM"*
