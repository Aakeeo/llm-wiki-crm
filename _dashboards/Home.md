---
type: dashboard
---

# CRM Home

Welcome to your LLM-maintained CRM. Drop raw sources (meeting notes, emails, transcripts) into `_inbox/` and ask your LLM to ingest them.

---

## Quick Stats

**Active Deals:** `$= dv.pages('"deals"').where(p => p.type == "deal" && p.stage != "closed-lost" && p.stage != "closed-won").length`

**Total Pipeline Value:** `$= "$" + dv.pages('"deals"').where(p => p.type == "deal" && p.stage != "closed-lost" && p.stage != "closed-won").values.map(p => p.value).reduce((a, b) => a + b, 0).toLocaleString()`

**Active Contacts:** `$= dv.pages('"contacts"').where(p => p.type == "contact" && p.status == "active").length`

**Open Tasks:** `$= dv.pages('"tasks"').where(p => p.type == "task" && p.status != "done").length`

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
2. **Ask a question:** *"What's our pipeline value this quarter?"* or *"When did we last talk to Quantum Labs?"*
3. **Update a record:** *"Move the Meridian Health deal to closed-won"*
4. **Health check:** *"Run a lint check on the CRM"*
