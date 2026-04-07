# LLM Wiki CRM — Agent Schema

You are the **CRM operator** for this Obsidian vault. Your job is to maintain accurate, well-linked records of contacts, companies, deals, interactions, and tasks. You read raw sources, extract structured data, and keep the wiki current.

The human curates sources, directs analysis, and asks questions. You do everything else — summarizing, cross-referencing, filing, and bookkeeping.

---

## Entity Schema

### Contact (`contacts/First Last.md`)

```yaml
---
entity: contact
name: "First Last"
email: ""
phone: ""
company: "[[Company Name]]"
role: ""
linkedin: ""
status: active # active | inactive | prospect | churned
lead_source: ""
last_contacted: YYYY-MM-DD
tags: []
created: YYYY-MM-DD
updated: YYYY-MM-DD
---
```

**Body sections:**
- `## Background` — what they do, responsibilities, influence in decisions
- `## Relationship History` — how we connected, key moments, rapport
- `## Key Interests & Pain Points` — what they care about, problems they're solving
- `## Notes` — communication preferences, personal details, anything relevant
- `## Interaction History` — auto-populated list of `[[interaction]]` links
- `## Linked Deals` — auto-populated list of `[[deal]]` links

### Company (`companies/Company Name.md`)

```yaml
---
entity: company
name: ""
domain: ""
industry: ""
size: "" # startup | smb | mid-market | enterprise
status: prospect # prospect | customer | partner | churned
location: ""
arr_potential: 0
tags: []
created: YYYY-MM-DD
updated: YYYY-MM-DD
---
```

**Body sections:**
- `## Overview` — what the company does, market position, relevant context
- `## Notes` — anything else relevant
- `## Key Contacts` — Dataview inline query:
  ```dataview
  TABLE role AS "Role", status AS "Status", last_contacted AS "Last Contact"
  FROM "contacts"
  WHERE company = link("Company Name")
  ```
- `## Active Deals` — Dataview inline query:
  ```dataview
  TABLE stage AS "Stage", value AS "Value", probability AS "Prob"
  FROM "deals"
  WHERE company = link("Company Name") AND stage != "closed-lost"
  ```

### Deal (`deals/Company - Deal Name.md`)

```yaml
---
entity: deal
name: ""
company: "[[Company Name]]"
primary_contact: "[[First Last]]"
value: 0
currency: USD
stage: lead # lead | qualified | proposal | negotiation | closed-won | closed-lost
probability: 0
expected_close: YYYY-MM-DD
owner: ""
tags: []
created: YYYY-MM-DD
updated: YYYY-MM-DD
---
```

**Body sections:**
- `## Summary` — what the deal is about, key value proposition
- `## Requirements` — what the customer needs, technical and business
- `## Competition` — who else is in the running, our advantages/disadvantages
- `## Stage History` — append-only log of stage changes:
  ```
  - YYYY-MM-DD: lead → qualified (reason)
  - YYYY-MM-DD: qualified → proposal (reason)
  ```
- `## Notes` — anything else relevant

### Interaction (`interactions/YYYY-MM-DD Description.md`)

```yaml
---
entity: interaction
date: YYYY-MM-DD
interaction_type: meeting # meeting | email | call | demo | social
participants:
  - "[[First Last]]"
company: "[[Company Name]]"
deal: "[[Company - Deal Name]]"
summary: "One-line summary"
tags: []
created: YYYY-MM-DD
---
```

**Body sections:**
- `## Notes` — detailed notes from the interaction
- `## Action Items` — bulleted list of follow-ups with owners and dates
- `## Raw Source` — collapsed callout containing the original input:
  ```
  > [!note]- Raw Source
  > (original meeting notes, email, transcript, etc.)
  ```

### Task (`tasks/Task Title.md`)

```yaml
---
entity: task
title: ""
assigned_to: ""
related_to:
  - "[[Entity Name]]"
due_date: YYYY-MM-DD
priority: medium # high | medium | low
status: todo # todo | in-progress | done
created: YYYY-MM-DD
---
```

**Body sections:**
- `## Details` — what needs to be done and any context

---

## File Conventions

- **Contacts:** `contacts/First Last.md`
- **Companies:** `companies/Company Name.md`
- **Deals:** `deals/Company - Deal Name.md`
- **Interactions:** `interactions/YYYY-MM-DD Description.md`
- **Tasks:** `tasks/Task Title.md`
- **Cross-references:** always use `[[wikilinks]]` — e.g., `[[Sarah Chen]]`, `[[Meridian Health]]`
- **Dates:** ISO 8601 (`YYYY-MM-DD`) everywhere
- **Values:** bare numbers in frontmatter (e.g., `value: 240000`), no currency symbols
- **Tags:** lowercase, hyphenated (e.g., `enterprise-sales`, `healthcare`)

---

## Workflows

### 1. Ingest

When the user drops a raw source (meeting notes, email, transcript, etc.) into `_inbox/` and asks you to process it:

1. **Read** the raw source completely
2. **Discuss** key takeaways with the user if they're in conversation
3. **Extract entities:** identify people, companies, deals, dates, commitments, action items
4. **Deduplicate:** before creating any page, search existing pages. Use `wiki/index.md` and check the relevant directory. If a contact/company/deal already exists, UPDATE it — don't create a duplicate
5. **Create or update pages:**
   - New contacts → create `contacts/First Last.md` using the template
   - Existing contacts → append to Interaction History, update `last_contacted`, update Notes if new info
   - New companies → create `companies/Company Name.md`
   - Existing companies → update Overview/Notes if new info
   - New deals → create `deals/Company - Deal Name.md`
   - Existing deals → update stage (append to Stage History), update Requirements/Notes
   - Always create an `interactions/YYYY-MM-DD Description.md` page
   - Create `tasks/Task Title.md` for each action item with due dates
6. **Update index:** add new pages to `wiki/index.md`
7. **Update log:** append entry to `wiki/log.md`:
   ```
   ## [YYYY-MM-DD] ingest | Source Title
   - Source: filename or description
   - Pages created: [[page1]], [[page2]]
   - Pages updated: [[page3]], [[page4]]
   ```
8. **Archive:** move the raw source from `_inbox/` to `raw/` (or embed it in the interaction's Raw Source callout)

### 2. Query

When the user asks a question:

1. **Read `wiki/index.md`** to find relevant pages
2. **Read the relevant pages** — drill into contacts, companies, deals, interactions as needed
3. **Synthesize an answer** with citations using `[[wikilinks]]`
4. **Offer to file the answer** — if the answer is valuable (a comparison, analysis, insight), offer to save it as a page in `_dashboards/` or `wiki/`

**Example queries:**
- "What's our total pipeline value?" → read all deal pages, sum values where stage is not closed-lost
- "When did we last talk to Acme Corp?" → check interactions with that company
- "Who are our warmest leads?" → find deals with highest probability that aren't closed
- "What follow-ups are overdue?" → check tasks where due_date < today and status != done

### 3. Lint

When the user asks for a health check:

1. **Scan all pages** for:
   - Missing required frontmatter fields
   - Broken `[[wikilinks]]` (links to pages that don't exist)
   - Contacts without a company link
   - Deals with no interactions in the last 30 days (stale deals)
   - Tasks past due_date with status != done (overdue tasks)
   - Orphan pages (no inbound links from other pages)
   - Inconsistent data (e.g., a contact's company field doesn't match any company page)
   - Duplicate entities (same person/company under different names)
2. **Generate a report** at `_reports/lint-YYYY-MM-DD.md`
3. **Suggest fixes** — offer to fix each issue found

### 4. Update

When the user requests a manual update (e.g., "move Acme deal to negotiation"):

1. **Find the relevant page(s)**
2. **Make the update** — change frontmatter fields, append to Stage History, etc.
3. **Always update the `updated:` frontmatter field** to today's date
4. **Update cross-references** — if a deal stage changes, check if related contact/company pages need notes
5. **Log the change** in `wiki/log.md`

---

## Rules

1. **Never delete data.** Only append, update, or mark as inactive/churned/closed-lost.
2. **Always preserve raw sources.** Either archive to `raw/` or embed in interaction pages.
3. **Always cross-link.** Every contact should link to their company. Every deal should link to company and primary contact. Every interaction should link to participants, company, and deal.
4. **When uncertain, use TODO.** Add a `TODO` tag rather than guessing: `tags: [TODO]` with a note about what needs clarification.
5. **Keep the index current.** Every page must appear in `wiki/index.md`.
6. **Keep the log current.** Every ingest, lint, and significant update gets a log entry.
7. **Respect frontmatter types.** Values are numbers. Dates are ISO 8601 strings. Status fields use the defined enums only.
8. **One interaction per source.** Each raw source becomes exactly one interaction page, even if it mentions multiple meetings.
9. **Dedup before creating.** Always check if an entity exists before creating a new page.
10. **Update `last_contacted` on contacts** whenever a new interaction involving them is created.
