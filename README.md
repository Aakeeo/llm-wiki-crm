# LLM Wiki CRM

**Your CRM is a folder of markdown files. An LLM maintains it for you.**

Drop meeting notes in a folder. The LLM extracts contacts, companies, deals, and action items — updates every relevant page, maintains cross-references, keeps your pipeline current. Browse it all in Obsidian with graph view, Dataview dashboards, and full-text search. Zero lock-in. Your data is just files.

<!-- Add screenshot: Obsidian graph view + pipeline dashboard side by side -->

---

## What is this?

Most CRMs fail because nobody wants to do the data entry. You finish a sales call, and the last thing you want to do is open Salesforce and update 5 different records. So the data goes stale, and the CRM becomes useless.

This project flips that. Instead of you maintaining the CRM, an **LLM does it for you**. You drop raw sources — meeting notes, email threads, call transcripts — into an inbox folder. Then you tell your LLM agent to process them. The LLM reads the source, extracts every entity (people, companies, deals, action items), and updates all the relevant pages in your wiki. A single meeting note might touch 5-10 files. Cross-references, relationship history, deal stage updates — all handled automatically.

The result is a **living, interlinked knowledge base** that stays current because the maintenance cost is near zero. You browse it in [Obsidian](https://obsidian.md) — graph view shows your relationship network, Dataview dashboards show your pipeline, and everything is connected through wiki-links.

Built on [Andrej Karpathy's LLM Wiki pattern](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f).

---

## Quick Start

### 1. Clone and open in Obsidian

```bash
git clone https://github.com/arunchauhan/llm-wiki-crm.git
```

Open the cloned folder as a vault in [Obsidian](https://obsidian.md).

### 2. Install required plugins

In Obsidian, go to **Settings > Community plugins > Browse** and install:

- **Dataview** — powers all the dashboard queries
- **Templater** — enables templates with dynamic fields

Enable both plugins after installing.

### 3. Explore the demo data

The vault comes pre-loaded with realistic dummy data:

- **5 companies** across healthcare, dev tools, education, manufacturing, and VC
- **8 contacts** with detailed backgrounds and relationship history
- **5 deals** at different pipeline stages ($845K total pipeline)
- **8 interactions** telling a coherent sales story
- **4 open tasks** with priorities and due dates

Start with the **[[Home]]** dashboard, then explore the **[[Pipeline]]** and **graph view**.

### 4. Try an ingest

There's an example meeting note in `_inbox/_example_meeting_notes.md`. Open your LLM agent and tell it:

> "Process the meeting notes in _inbox"

Watch as it creates new contact, company, deal, and interaction pages — and updates the index and log.

---

## How It Works

### Architecture

```
llm_wiki/
├── CLAUDE.md          # LLM instructions — the "brain"
├── _templates/        # Page templates for each entity type
├── _inbox/            # Drop raw sources here for processing
├── _dashboards/       # Dataview-powered views (pipeline, activity, etc.)
├── contacts/          # One page per person
├── companies/         # One page per company
├── deals/             # One page per deal
├── interactions/      # One page per meeting/call/email
├── tasks/             # One page per follow-up
├── wiki/              # Index and activity log
└── raw/               # Archived raw sources
```

### Four Workflows

**Ingest** — Drop a raw source (meeting notes, email, transcript) into `_inbox/`. Tell your LLM to process it. The LLM extracts entities, creates/updates pages, maintains cross-references, and logs everything. A single source might touch 10+ files.

**Query** — Ask questions against your CRM. *"What's our pipeline value?"* *"Who are our warmest leads?"* *"What follow-ups are overdue?"* The LLM reads the relevant wiki pages and synthesizes an answer with citations.

**Update** — Make changes via natural language. *"Move the Acme deal to negotiation."* *"Mark Jane as inactive."* The LLM finds the right page, updates it, and logs the change.

**Lint** — Ask for a health check. The LLM scans for stale deals, missing data, broken links, overdue tasks, and orphan pages. Outputs a report with suggested fixes.

---

## Entity Schema

| Entity | File Pattern | Key Fields |
|--------|-------------|------------|
| Contact | `contacts/First Last.md` | name, company, role, status, last_contacted |
| Company | `companies/Company Name.md` | industry, size, status, arr_potential |
| Deal | `deals/Company - Deal Name.md` | value, stage, probability, expected_close |
| Interaction | `interactions/YYYY-MM-DD Description.md` | date, type, participants, summary |
| Task | `tasks/Task Title.md` | due_date, priority, status, related_to |

All entities use YAML frontmatter (queryable by Dataview) and `[[wikilinks]]` for cross-referencing.

---

## Works With Any LLM

The schema is defined in both `CLAUDE.md` and `AGENTS.md` (identical content). Your LLM agent picks up the right one automatically:

- **[Claude Code](https://claude.ai/claude-code)** — reads `CLAUDE.md`. Just run `claude` in the vault directory.
- **[OpenAI Codex](https://openai.com/codex)** — reads `AGENTS.md`. Just run `codex` in the vault directory.
- **[Cursor](https://cursor.sh)** — reads `CLAUDE.md` or add as `.cursorrules`
- **Any LLM agent** that reads instruction files from the project root

The schema is LLM-agnostic. The instructions work with any model.

---

## Customizing

### Add a new entity type

1. Create a template in `_templates/` with YAML frontmatter
2. Add the schema to `CLAUDE.md`
3. Create a directory for the entity (e.g., `products/`)
4. Add a Dataview dashboard in `_dashboards/`

### Modify fields

Edit the frontmatter in `_templates/` and update the schema in `CLAUDE.md`. Existing pages can be batch-updated by asking your LLM.

### Add dashboards

Create a new `.md` file in `_dashboards/` with Dataview queries. See existing dashboards for examples.

---

## Philosophy

This project is inspired by [Andrej Karpathy's LLM Wiki pattern](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f) and, more distantly, by Vannevar Bush's [Memex](https://en.wikipedia.org/wiki/Memex) (1945) — a personal, curated knowledge store with associative trails between documents.

The key insight: **the tedious part of maintaining a CRM is not the selling or the thinking — it's the bookkeeping.** Updating records, maintaining cross-references, keeping deal stages current. Humans abandon CRMs because the maintenance burden grows faster than the value. LLMs don't get bored, don't forget to update a cross-reference, and can touch 15 files in one pass.

The human's job: source leads, build relationships, close deals, think strategically.
The LLM's job: everything else.

---

## Tech Stack

- **[Obsidian](https://obsidian.md)** — free, local-first markdown editor with graph view
- **[Dataview](https://github.com/blacksmithgu/obsidian-dataview)** — query engine for page frontmatter
- **[Templater](https://github.com/SilentVoid13/Templater)** — dynamic templates
- **Markdown + YAML** — your data, in plain text, forever
- **Git** — version history, branching, and collaboration for free

---

## License

MIT — see [LICENSE](LICENSE).
